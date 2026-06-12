---
title: "does upgrading kernel always upgrade linux-modules-extra"
date: 2022-01-12
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2022-01-12
It said I had to reboot so I did.
I had no kernel module for my mediatek wifi after I rebooted.
I did:
[HTML]dpkg -l | grep linux-modules-extra
ii  linux-modules-extra-5.13.0-1011-raspi
ii  linux-modules-extra-5.13.0-1012-raspi
rc  linux-modules-extra-5.13.0-23-generic

$ uname -r
5.13.0-1013-raspi
[/HTML]
So I installed linux-modules-extra-5.13.0-1013-raspi and now I have wifi.

My question is should linux-modules-extra get upgraded with any kernel update?

---

### Post by rsteinmetz70112 on 2022-01-13
Assuming modules-extra was installed originally "apt upgrade" should upgrade it whenever the kernel is upgraded. I've never seen it not upgrade. I suppose there could be a problem with the repository you used not being completely updated, or something else.

---

### Post by ajgreeny on 2022-01-13
The linux-modules package is a dependency of a linux-image package but the linux-modules-extra is not even a recommended or suggested package, so if you don't already have it installed the linux-modules-extra will not be upgraded.

Interestingly I have just realised that I have the linux-modules-extra packages installed in my laptop with Xubuntu 20.04 but on my desktop machine the linux-modules-extra are not installed as far as I can remember.
If I have remembered this wrongly I will update here, but the apparent difference makes me wonder if the linux-modules-extra packages are normally installed only for machines using wireless network.

---

### Post by chili555 on 2022-01-13
> on my desktop machine the linux-modules-extra are not installed as far as I can remember.That would surprise me. Check:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```I have seen several cases where -extra was not updated. Here, for example: [https://ubuntuforums.org/showthread.php?t=2470761](https://ubuntuforums.org/showthread.php?t=2470761)

It is a dependency of linux-image-generic. I'd check to see if it is installed:

```
sudo dpkg -s linux-image-generic | grep Status
```

And perhaps reinstall it:

```
sudo apt install --reinstall linux-image-generic
```

---

### Post by bjlockie on 2022-01-14
```
$ sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
Status: install ok installed

$ sudo dpkg -s linux-image-generic | grep Status
dpkg-query: package 'linux-image-generic' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files.

$ uname -r
5.13.0-1013-raspi

```

---

### Post by chili555 on 2022-01-15
Please do:

```
sudo apt install linux-image-generic
```I'm confident that then -extra will update as expected.

---

### Post by ajgreeny on 2022-01-15
> **chili555 said:**
> 

> On my desktop machine the linux-modules-extra are not installed as far as I can remember.
That would surprise me. Check:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```I have seen several cases where -extra was not updated. Here, for example: [https://ubuntuforums.org/showthread.php?t=2470761](https://ubuntuforums.org/showthread.php?t=2470761)

It is a dependency of linux-image-generic. I'd check to see if it is installed:

```
sudo dpkg -s linux-image-generic | grep Status
```

And perhaps reinstall it:

```
sudo apt install --reinstall linux-image-generic
```
You were absolutely correct chili555.

I do indeed have the ***linux-modules-extra*** packages for my two installed kernel versions on my desktop machine, as you said I should.
Having checked all packages installed I think it may be the ***linux-tools*** that are present on my laptop and not on my desktop.

---

### Post by deadflowr on 2022-01-15
The "extras" package dependency does not apply to the linux-raspi meta-packages like it does for the linux-generic packages.
For linux-raspi it is only a suggested package.
I have no idea why, but you could probably ask the kernel team about it here: [https://answers.launchpad.net/ubuntu/+source/linux-raspi]("https://answers.launchpad.net/ubuntu/+source/linux-raspi")

---

### Post by bjlockie on 2022-01-16
```
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.13.0-25-generic
Killed
E: mkinitramfs failure zstd -q -19 -T0 137
update-initramfs: failed for /boot/initrd.img-5.13.0-25-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.13.0-25-generic (--configure):
 installed linux-image-5.13.0-25-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.13.0-25-generic
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I suspect out of memory.

```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           906Mi       220Mi       480Mi       5.0Mi       205Mi       597Mi
Swap:             0B          0B          0B
```

I used gzip as per:
[https://ubuntuforums.org/showthread.php?t=2469034&p=14067672](https://ubuntuforums.org/showthread.php?t=2469034&p=14067672)

---

