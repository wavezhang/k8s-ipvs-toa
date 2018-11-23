# k8s-ipvs-toa
Let you get real client IP in k8s pod using [toa](https://github.com/Huawei/TCP_option_address). Only works if your kubeproxy  is using ipvs mode.

Test on kernel 4.14 only, should work on 3.10+.

## How to use

1. Download your target kernel source. For example:
```
wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.14.49.tar.xz
tar -xf linux-4.14.49.tar.xz
cd linux-4.14.49
```

2. Apply the patch 
```
patch -p1 < ../k8s-ipvs-toa/k8s-ipvs.patch
```

3. Compile kernel modules

Refer to https://wiki.archlinux.org/index.php/Kernel/Traditional_compilation#Compilation_and_installation if you donot known how to compile the kernel.

4. Install kernel modules

Install newly compiled ipvs kernel modules and [toa](https://github.com/Huawei/TCP_option_address) kernel modules on all k8s nodes.

5. Test
You will see real client IP in Pod.

