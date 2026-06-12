---
title: "Bluetooth cannot be enabled , ubuntu 12.04 , dell latitude e4200"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by dankonino on 2013-12-18
matush@matush-Latitude-E4200:~$ uname -r
3.8.0-34-generic
matush@matush-Latitude-E4200:~$ ps -el | grep blue
5 S     0   570     1  0  80   0 -  1186 poll_s ?        00:00:00 bluetoothd
0 S  1000  2179  2076  0  80   0 - 33971 poll_s ?        00:00:00 bluetooth-apple


 lsusb
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

I have only Ubuntu on my PC.

---

### Post by agerpark on 2013-12-19
Hi [**[COLOR=#000000]dankonino[/COLOR]**]("http://ubuntuforums.org/member.php?u=1888551")
did you check hardware drivers ?

system - administrator - hardware drivers - brodcom check - active and then automatically setup and enable WIFI.

---

### Post by dankonino on 2013-12-19
I don't have hardware drivers there , only additional drivers somewhere else ,(without any additional driver).

---

### Post by agerpark on 2013-12-20
if so,, 
you can sudo apt-get install bcmwl-kernel-source and reboot and additional drivers check and enable.

if not, you can sudo apt-get install bluman.

---

### Post by dankonino on 2013-12-20
Okay thanks, this is what I get after first command 
:"After this operation, 4'016 kB of additional disk space will be used.Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)'
in the drive '/media/cdrom/' and press enter
"   
and I have on UsB ubuntu , but don't know what can do next , because it's not working if I insert Usb, i thought so that I can change the wanted directory ..

---

