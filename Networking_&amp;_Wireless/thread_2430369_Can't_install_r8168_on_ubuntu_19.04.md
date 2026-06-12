---
title: "Can't install r8168 on ubuntu 19.04"
date: 2019-10-31
forum: Networking &amp; Wireless
---

### Post by lisa-alhadeff84 on 2019-10-31
Hi,

I'm using Ubuntu 19.04, and I've not had any luck following instructions on other threads with unstable wireless connection. I tried to install the realtek autorun, and got the following errors:

```
####@Aspire-V5-573P:~/Downloads/r8168-8.046.00$ sudo ./autorun.sh
[sudo] password for ####: 

Check old driver and unload it.
Build the module and install
Makefile:223: ================= WARNING ================
Makefile:224: 'SUBDIRS' will be removed after Linux 5.3
Makefile:225: Please use 'M=' or 'KBUILD_EXTMOD' instead
Makefile:226: ==========================================
Makefile:223: ================= WARNING ================
Makefile:224: 'SUBDIRS' will be removed after Linux 5.3
Makefile:225: Please use 'M=' or 'KBUILD_EXTMOD' instead
Makefile:226: ==========================================
Makefile:223: ================= WARNING ================
Makefile:224: 'SUBDIRS' will be removed after Linux 5.3
Makefile:225: Please use 'M=' or 'KBUILD_EXTMOD' instead
Makefile:226: ==========================================
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:72
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:79
sign-file: certs/signing_key.pem: No such file or directory
Warning: modules_install: missing 'System.map' file. Skipping depmod.
DEPMOD 5.0.0-32-generic
load module r8168
modprobe: ERROR: could not insert 'r8168': Operation not permitted
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-5.0.0-32-generic
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=091f0de6-4915-4331-b8e0-5ef94648187a)
I: Set the RESUME variable to override this.
Completed.
####@Aspire-V5-573P:~/Downloads/r8168-8.046.00$ lsmod | grep r8169
####@Aspire-V5-573P:~/Downloads/r8168-8.046.00$ 
```

When I put in ```
lsmod | grep r8168 
``` I see nothing and  indeed with r8169. What have I done! Something bad? Any help much  appreciated.

---

### Post by chili555 on 2019-10-31
> following instructions on other threads with unstable **wireless **connection.r8168 is an ethernet driver, not wireless.

Please start over and post the wireless info from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

