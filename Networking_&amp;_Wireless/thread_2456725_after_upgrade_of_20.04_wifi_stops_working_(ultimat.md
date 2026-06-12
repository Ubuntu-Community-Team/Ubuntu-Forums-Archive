---
title: "after upgrade of 20.04 wifi stops working (ultimate-N 6300)"
date: 2021-01-18
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2021-01-18
Hi,
   upon upgrading my ubuntu-20.04 to the latest stage the wifi stopped working (network manager does not even show the icon but ethernet works). Wifi of the older ubuntu-16.04 installed on the same PC works normally. I have scanned the net for hours and tried various of the described solutions but none worked for me. The hardware tool described here [https://linux-hardware.org](https://linux-hardware.org) shows that the Intel driver 'Centrion Ultimate-N 6300' is missing. No idea why it disappeared! Can anybody please give me a point per point instruction of how to install this driver correctly! 
Thanks, a lot, D.

---

### Post by jeremy31 on 2021-01-18
Try ```
sudo modprobe iwlwifi
```

---

### Post by chili555 on 2021-01-18
Jeremy and I would also like to see:

```
dmesg | grep iwl
```

---

### Post by dieter-erich on 2021-01-18
Thank you!
[B]
sudo modprobe iwlwifi:[/B]
modprobe: ERROR: ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)

[B]dmesg | grep iwl:
[/B]no output

---

### Post by jeremy31 on 2021-01-18
What results for ```
dpkg -l | grep linux-modules-extra-$(uname -r); dkms status; modinfo iwlwifi
```

---

### Post by dieter-erich on 2021-01-18
I get:
"modinfo: ERROR: Module iwlwifi not found."

---

### Post by jeremy31 on 2021-01-18
Do ```
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Reboot

---

### Post by dieter-erich on 2021-01-18
Hi, some more info:
not being able to find this driver I did: [COLOR=blue]sudo apt-get install backport-iwlwifi-dkms
but "ls /usr/lib/firmware|grep wifi" shows me a lot of .ucode files but none containing "6300" 
Could it be that I have to fetch this file from somewhere else?
[/COLOR]

---

### Post by dieter-erich on 2021-01-18
sudo apt install --reinstall linux-modules-extra-$(uname -r) gives me:
.............................
Unpacking linux-modules-extra-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
Setting up linux-modules-extra-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
Processing triggers for linux-image-5.8.0-38-generic (5.8.0-38.43~20.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.8.0-38-generic
**Error! Your kernel headers for kernel 5.8.0-38-generic cannot be found.**
Please install the linux-headers-5.8.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
**Error! Your kernel headers for kernel 5.8.0-38-generic cannot be found.**
Please install the linux-headers-5.8.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
.............................................................................................
So I must have screwed up also the linux-headers. How do I reinstall them?

---

### Post by jeremy31 on 2021-01-18
Do ```
sudo apt purge backport-iwlwifi-dkms
sudo apt install --reinstall linux-headers-5.8.0-38-generic linux-modules-extra-5.8.0-38-generic
```
Reboot if no errors

---

### Post by dieter-erich on 2021-01-18
SOLVED! It works! Thank you sooo much, I learned a lot and would never ever have found out by myself! I have to be very careful when upgrading next time!

---

### Post by jeremy31 on 2021-01-18
I messed up the first command because of a copy/paste but kernel update issues are rare, I have only had one in 6 years but they do happen

---

### Post by dieter-erich on 2021-01-19
It works!!!! Thank you so much for your expert help and patience! I learned a lot and I am sure that I would not have been able of solving this problem on my own! I must be more careful when upgrading as I must have done something wrong.....

---

### Post by dieter-erich on 2021-01-19
SOLVED!!! Thank you so much Jeremy31! Without your expertise and patience I would never ever been able to solve this problem! I thanked you already in two posts but I do not know why it did not show up. I hope this one does.....

---

### Post by dieter-erich on 2021-02-10
jeremy31 solved my problem! However, when running 'sudo apt update and sudo apt upgrade' the headers are apparently lost and I
always have to re-run the below (adjusted for the new kernel having become installed)!
sudo apt purge backport-iwlwifi-dkms
sudo apt install --reinstall linux-headers-5.8.0-38-generic linux-modules-extra-5.8.0-38-generic
Is there a way to make the change permanent so that I can upgrade normally?
Thanks, D.

---

### Post by dieter-erich on 2021-02-10
Hi,
  I am sorry, I somewhat messed up this tread answering to something else. Here is the correct one. 
Jeremy31 solved my problem. Thanks again! However, when upgrading the headers are lost and I must re-install them as before. 
 How can I arrange that the headers are automatically upgraded as well and not deleted?
Thanks, D

---

### Post by chili555 on 2021-02-10
> How can I arrange that the headers are automatically upgraded as well and not deleted?Uncle Jeremy may be out for a coffee. He suggests that you do:

```
sudo apt install linux-headers-generic
```You should be all set.

---

