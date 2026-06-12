---
title: "netgear 3100 v2 don't work"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by brian40 on 2014-02-01
hi i have a netgear 3100v2 wi fi adapter
i have installed ndiswrapper correctly

i have installed dirver bcmwlhigh5 
and after bcm43xx64

lsusb see the device

ndiswrapper -l show i have installed both driver (but bcmlwhigh5 it say invalid driver!)

if i type ndiswrapper -r bcmwlhigh5.inf 
it say the driver can be removed

help please

---

### Post by chili555 on 2014-02-01
You need the bcmwlhigh5.inf and the accompanying .sys files for Windows XP and for your architecture, either 32- or 64-bit. Which do you have?```
arch
```Where did you get the files?> if i type ndiswrapper -r bcmwlhigh5.inf
it say the driver can be removedPlease try:```
sudo ndiswrapper -e bcmwlhigh5
```That is -e for 'erase.' Also, modifying system files requires administrative privileges, that is, 'sudo.'

---

### Post by brian40 on 2014-02-01
i have 64 bit

---

### Post by brian40 on 2014-02-01
i forget to tell ...i use back box not ubuntu but i think it's same thing

---

### Post by chili555 on 2014-02-01
> **brian40 said:**
> i have 64 bitSo where did you get the .inf and .sys files? Are they for Windows XP?

---

### Post by brian40 on 2014-02-01
from link in other thread and from official site of netgear

---

### Post by chili555 on 2014-02-01
> **brian40 said:**
> from link in other thread and from official site of netgearIn the other thread, was it a file that I provided? I don't trust anyone but me!

---

### Post by brian40 on 2014-02-02
i don't know
show me the rigth link

---

### Post by brian40 on 2014-02-02
ndiswrapper -e bcmwlhigh5  no such file or directory

what the command dmesg | grep ndis should do?

---

### Post by chili555 on 2014-02-02
```
ndiswrapper -e bcmwlhigh5 no such file or directory
```Let's have a look at:```
ls /etc/ndiswrapper
ndiswrapper -l
```> what the command dmesg | grep ndis should do? It shows all the messages in the log 'dmeg' that have ndis in them. It's very useful to see if ndiswrapper is loading or has an error. What does it report?> i don't know
show me the rigth link It depends on your exact version of the device. Please show us:```
lsusb
```Thanks.

---

### Post by brian40 on 2014-02-02
lsusb 

Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 004 Device 002: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | grep ndis 

nothing happen



brian@Brian-pc:~/Scrivania$ ls/etc/ndiswrapper 
bcmn43xx64  bcmwlhigh5
 



brian@Brian-pc:~/Scrivania$ ndiswrapper-l 
bcmn43xx64 : driver installed 
	device (0846:9011) present 
bcmwlhigh5 : invalid driver!

---

### Post by brian40 on 2014-02-02
maybe it work only with 32 bit driver?

---

### Post by chili555 on 2014-02-02
> bcmn43xx64 : driver installed
device (0846:9011) present
bcmwlhigh5 : invalid driver! This actually doesn't look too bad! Please try:```
sudo ndiswrapper -e bcmwlhigh5
```If it still doesn't work, then:```
sudo modprobe -r ndiswrapper
sudo rm -rf  /etc/ndiswrapper/bcmwlhigh5
```STOP!!! Proofread very carefully before you press Enter. The command 'rm' is very powerful and there is no recovery. Now check:```
ls /etc/ndiswrapper
```You should only see:```
ls /etc/ndiswrapper
bcmn43xx64 
```In other words, only the probably good driver remains. Reload ndiswrapper:```
sudo modprobe ndiswrapper
```Check for errors or warnings:```
dmesg | grep ndis
iwconfig
```

---

### Post by brian40 on 2014-02-03
it seems working now!!

for the next time i have the same problem ( or if i install ubuntu / backbox etc on another computer) can you repeat all the steps?

1) install ndiswrapper 
sudo su
make
make install
modprobe ndiswrapper
exit

2)install driver
ndiswrapper  bcm43xx64.inf

(lsusb should show the device, right?)


and so ?

---

### Post by chili555 on 2014-02-03
> **brian40 said:**
> it seems working now!!

for the next time i have the same problem ( or if i install ubuntu / backbox etc on another computer) can you repeat all the steps?

1) install ndiswrapper 
sudo su
make
make install
modprobe ndiswrapper
exit

2)install driver
ndiswrapper  bcm43xx64.inf

(lsusb should show the device, right?)


and so ?I think you have it exactly correct! As you have seen reading about this device on the forum, there are a lot of driver files floating around. Once you find a set that works for you, save them in a secure place and make a backup!

Just to add a few more details for the searchers, brian40 suggests compiling ndiswrapper from source code. The version in the Ubuntu repositories often doesn't work. To compile it, install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Download the file here: [http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-1.59.tar.gz/download](http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-1.59.tar.gz/download) By default, downloads go to (in English)  the folder Downloads. Right-click it and select 'Extract Here.' Now, in a terminal:```
cd ~/Downloads/ndiswrapper-whatever_version_you_downloaded
make
sudo make install
```The .inf files you need are XP (as ndiswrapper requires XP files), they need to match your architecture; either 32- or 64-bit and they must mention your device ID. As you read above, brian40 has a 64-bit system and used bcmn43x[COLOR="#FF0000"]x64[/COLOR]. The file he used says, in part: > [Broadcom]
%BCM4xx01_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_825C
%BCM4xx02_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_6050
%BCM4xx04_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_615A
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_[COLOR="#FF0000"]0846[/COLOR]&PID_[COLOR="#FF0000"]9011[/COLOR]
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_0846&PID_9020
So the .inf file specifically covers his device:> ID [COLOR="#FF0000"]0846:9011[/COLOR] NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]Then do:```
sudo ndiswrapper -i bcmn43xx64.inf
sudo modprobe ndiswrapper
```Great job, brian40! Glad it's working.

---

### Post by brian40 on 2014-02-03
thank you chili555!!

for installin prerequisites i already have a internet connection right

i'm a noob of linux sistem..but i begin to understand the logic 

i don't know all the command and when or how i have tu use it 

there is a guide for beginners?

---

### Post by chili555 on 2014-02-03
> for installin prerequisites i already have a internet connection rightThat is correct.> there is a guide for beginners? [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

The exact meaning of a command differs from program to program. For example, 'ndiswrapper -i' the -i means 'install.' In the command 'grep -i' the -i means 'case insensitive.' Case insensitive means, for example, I want to see acpi just as well as ACPI.

There is a manual page for almost every command so you can see what the commands do and how to adjust them:```
man grep
```Or:```
man ndiswrapper-1.9
```

---

### Post by brian40 on 2014-02-04
can you explain me why averytime i start backbox i have to repeat the command " sudo modprobe ndiswrapper" or the wifi not work?

---

### Post by chili555 on 2014-02-04
> **brian40 said:**
> can you explain me why averytime i start backbox i have to repeat the command " sudo modprobe ndiswrapper" or the wifi not work?Let's fix that:```
sudo -i
echo ndiswrapper  >>  /etc/modules
exit
```Now does it work?

---

