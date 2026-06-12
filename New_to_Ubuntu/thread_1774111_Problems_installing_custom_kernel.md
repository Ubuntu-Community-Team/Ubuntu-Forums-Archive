---
title: "Problems installing custom kernel"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by P=NP on 2011-06-02
I'm trying to learn about Kernels and I get this error after compilation on install.
```
root@c:/usr/src# dpkg -i linux-image-2.6.39-bri_2.6.39-bri-10.00.Custom_amd64.deb 
(Reading database ... 149657 files and directories currently installed.)
Preparing to replace linux-image-2.6.39-bri 2.6.39-bri-10.00.Custom (using linux-image-2.6.39-bri_2.6.39-bri-10.00.Custom_amd64.deb) ...
Examining /etc/kernel/preinst.d/
Done.
Unpacking replacement linux-image-2.6.39-bri ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.39-bri /boot/vmlinuz-2.6.39-bri
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.39-bri /boot/vmlinuz-2.6.39-bri
Setting up linux-image-2.6.39-bri (2.6.39-bri-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-bri /boot/vmlinuz-2.6.39-bri
 * dkms: running auto installation service for kernel 2.6.39-bri                
 *       fglrx (8.840)...                                                [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-bri /boot/vmlinuz-2.6.39-bri
update-initramfs: Generating /boot/initrd.img-2.6.39-bri
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-bri /boot/vmlinuz-2.6.39-bri
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-bri /boot/vmlinuz-2.6.39-bri
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-bri /boot/vmlinuz-2.6.39-bri
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-bri /boot/vmlinuz-2.6.39-bri
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-bri
Found initrd image: /boot/initrd.img-2.6.39-bri
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@c:/usr/src# 

```Any pointers?

---

### Post by jtarin on 2011-06-02
Why do you think you have a problem? Is your internet connection OK? Graphics OK? There's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/774668") against "fglrx". [It's been posted before. ]("http://www.google.com/search?hl=en&source=hp&q=fglrx+(8.840)..&btnG=Google+Search&aq=f&aqi=&aql=&oq=") I would't worry if everything is working OK, just be alert and consider. BTW the title of your post was correct..."Problems installing custom kernel" but your post remark of "I get this error after compilation on install" is slightly incorrect as this is an install of a .deb.package and is not the same as _compiling_ a kernel.

---

### Post by P=NP on 2011-06-02
After I compile the kernel, I'm left with two deb packages.

Image and Headers.

When I try to install them I get that error. I've seen the bug reports, but I didn't know if it was something I was doing. I still learning.

I'm going to try and compile .38 and see if I get that error.

Thank you for the help, you've answered a few of my threads. :)

---

### Post by jtarin on 2011-06-03
[Did you have occasion to read this?]("https://help.ubuntu.com/community/Kernel/Compile")

---

### Post by sbraz on 2011-06-03
> ```
 *       fglrx (8.840)...                                                [fail]
```
i've been searching more or less a month to address this: you need to patch fglrx for kernel 38 and 39 (i have 64bit but it shouldn't matter):

[http://ubuntuforums.org/showthread.php?t=1672882&page=11](http://ubuntuforums.org/showthread.php?t=1672882&page=11) post #102 gives you some advice.

as for those "missing firmware" i don't know, i saw something similar but didn't bother solving it because i could bot anyway and then it solved by itself (?).

i build my kernel with **fakeroot make deb-pkg** and it throws out FOUR files:

```
-rw-r--r--  1 root src     52262 2011-06-02 23:08 linux-firmware-image_2.6.39-custom-1_amd64.deb
-rw-r--r--  1 root src   6732116 2011-06-02 23:08 linux-headers-2.6.39-custom_2.6.39-custom-1_amd64.deb
-rw-r--r--  1 root src  12835414 2011-06-02 23:09 linux-image-2.6.39-custom_2.6.39-custom-1_amd64.deb
-rw-r--r--  1 root src    820166 2011-06-02 23:08 linux-libc-dev_2.6.39-custom-1_amd64.deb
```
to install this "firmware .deb" i had to **apt-get purge linux-firmware** otherwise it wouldn't install.
headers isn't required as you already have the whole source.

if you haven't patched apparmor yet, here's where you can look for patches:
[http://www.kernel.org/pub/linux/security/apparmor/AppArmor-2.6/](http://www.kernel.org/pub/linux/security/apparmor/AppArmor-2.6/)

apparmor-v2.6+v2.4-compat-for-2.6.39.tgz is what you need for kernel 2.6.39

---

