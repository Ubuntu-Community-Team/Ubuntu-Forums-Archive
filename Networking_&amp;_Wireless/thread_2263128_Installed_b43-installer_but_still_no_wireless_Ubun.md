---
title: "Installed b43-installer but still no wireless Ubuntu 14.04 Broadcom 14e4:4311"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by Cassia on 2015-01-29
Hi I am new to Ubuntu, have an older Aspire 3680, I followed the instructions on the sticky page of the forum, run the script 
lspci -nn -d 14e4: and the result:
 Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


So downloaded the suggested firmware-b43-installer

nothing works, and this laptop has a broken wireless switch (no way for me to phisically turn it on).

rfkill list gives this result:

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no



No idea what I am doing at this point, thanks for any kind help!
e

---

### Post by chili555 on 2015-01-29
Please reboot and show us:```
dmesg | grep b43
iwconfig
```Thanks.

---

### Post by Cassia on 2015-01-29
Hi, this is what I get:

cassia@cassia-Aspire-3680:~$ dmesg | grep b43
cassia@cassia-Aspire-3680:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Thanks!

---

### Post by chili555 on 2015-01-29
I have a bit of a hunch here. Please try:```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe b43
iwconfig
```Any good news?

---

### Post by ajgreeny on 2015-01-29
Also have a good read through the sticky thread at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Cassia on 2015-01-29
Hi, I'm back, here's what I get with the first command:
~$ sudo apt-get purge bcml-kernel-source
[sudo] password for cassia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcml-kernel-source


And... I didn't know I should have entered the next command, and I did anyways, and it does't return anything, just the blinking cursor...

Thanks!

---

### Post by Cassia on 2015-01-29
Hi, I did, that was the first thing I tried (installed the firmware from the link). Thanks, still trying to get it going!

---

### Post by Cassia on 2015-01-29
just a sec... caught my syntax mistake when I did the first command on the first try... trying again..

---

### Post by Cassia on 2015-01-29
Ok, and here's what I got when I did it again:

cassia@cassia-Aspire-3680:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for cassia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 4,944 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 195503 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic
cassia@cassia-Aspire-3680:~$ sudo modprobe b43
^Ccassia@cassia-Aspire-3680:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2015-01-29
Please reboot and if it's not working, show me:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by Cassia on 2015-01-29
Ok, here it is...
$ sudo modprobe b43
[sudo] password for cassia: 
cassia@cassia-Aspire-3680:~$ dmesg | grep b43
[    2.239854] b43-pci-bridge 0000:03:00.0: enabling device (0000 -> 0002)
[   12.417397] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   12.468678] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   27.840074] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   37.972113] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
cassia@cassia-Aspire-3680:~$ 


thank you.

---

### Post by Cassia on 2015-01-29
ok, I've had to re-start this computer (as in sometimes it just turns itself off randomnly), and I just noticed wireless is on!!! Whatever you told me to do last worked! Thank you soo much, I'll be paying it forward!

---

### Post by chili555 on 2015-01-29
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

Have fun!

---

