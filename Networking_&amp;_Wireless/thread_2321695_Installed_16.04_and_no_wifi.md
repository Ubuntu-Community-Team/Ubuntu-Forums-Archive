---
title: "Installed 16.04 and no wifi"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by ericnotar on 2016-04-23
I installed 16.04 and I don't have Wi-Fi, impossible to see any ssid
I want to mention that I don't have network connection on my Lenovo Ideapad yoga 11S and cannot go online from the distribution to download anything. What works is to boot from USB stick and test 16.04, on this case I have Wi-Fi.
I hope somebody find a solution rapidly as it looks to be an epidemic as I see in many forum and no solution so far.
Realtek RTL8723AU
BTW: wifi-info doesn't run
: No such file or directory/bin/bash
./wireless-info: line 27: $'\r': command not found
./wireless-info: line 32: $'\r': command not found
./wireless-info: line 38: $'\r': command not found
./wireless-info: line 43: $'\r': command not found
./wireless-info: line 48: $'\r': command not found
./wireless-info: line 52: $'\r': command not found
./wireless-info: line 57: syntax error near unexpected token `elif'
'/wireless-info: line 57: `elif [ -x /usr/bin/zenity ]; then


Thank you for the help

---

### Post by jeremy31 on 2016-05-05
Please run the wireless script after booting to the USB stick if wifi works good there.  Some solutions you find may not work with Secure Boot enabled in BIOS using kernel 4.4.0-21 and newer

The wireless-info you have might be corrupted or just wrong, as the copy I looked at had nothing at all on the lines 27, 32, 38, 43

---

### Post by damianfanaro on 2016-07-17
Hi,


In my case, the work around was to unload and load again the 'rtl8xxxu' module after every reboot.


Here is the command:

**sudo rmmod rtl8xxxu && sudo modprobe rtl8xxxu**




I'm running Linux Mint 18 (Sarah) - Kernel 4.4.0-21-generic.
Laptop: Lenovo Yoga 13




On previous Kernel versions I had to install the driver (rtl8723au) manually.


I hope this issue to be fixed on future Kernel releases.

---

### Post by wildmanne39 on 2016-07-17
I believe you can make that run at start up by doing:
```
sudo su 
echo rtl8xxxu >> /etc/modules 
exit
```
if that does not worj then do:
```
gksudo gedit /etc/rc.local
```
Then add:
```
modprobe -r rtl8xxxu
modprobe rtl8xxxu
```
Proofread carefully, save and close gedit. 
Make the file executible then reboot.
Thanks

---

