---
title: "Ubuntu 10.10 wireless firmware missing"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Yaely7 on 2010-11-26
I just recently downloaded ubuntu and under wireless it says firmware missing. What do I do?

---

### Post by slixz85 on 2010-11-26
let me guess you got a dell too? just need to know what kind of card you got. i use a dell mini inspiron 10 with broadcom 43XX
my install was this
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
that is a definited driver needed for most dells if that is what you have.
you will need to install this or the driver you need by wired connection for best install

---

### Post by dFlyer on 2010-11-26
I guess the first thing we need to know is what type of wireless? Also have you tried to connect while hard wired to the network and then use Additional Drivers under system/administrative to see if there is a firmware driver available.

---

### Post by Hippytaff on 2010-11-26
> **dFlyer said:**
> I guess the first thing we need to know is what type of wireless? 
 
Can you open a terminal (CTRL+ALT+T) and post the output of
```

lspci | grep i net

```
 
or
```

lsusb | grep -i net

```
if its a usb wireless dongle (which I suspect it is)
 
to get the chipset of your wirless card. Then we can find out what driver you need and see if this actually the problem or not :-)

---

### Post by Yaely7 on 2010-11-26
> **Hippytaff said:**
> Can you open a terminal (CTRL+ALT+T) and post the output of
```

lspci | grep i net

```
 
or
```

lsusb | grep -i net

```
if its a usb wireless dongle (which I suspect it is)
 
to get the chipset of your wirless card. Then we can find out what driver you need and see if this actually the problem or not :-)

Neither of these commands work, it says command not found

---

### Post by Hippytaff on 2010-11-26
> **Yaely7 said:**
> Neither of these commands work, it says command not found
 
ok just do
```

lspci

```
or subsittue lspci for lsusb if it is a usb wireless dongle

---

### Post by Yaely7 on 2010-11-26
yael@yael-HP-Mini-210-1000:~$ lcpci | grep i net
grep: net: No such file or directory
No command 'lcpci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lcpci: command not found
yael@yael-HP-Mini-210-1000:~$ lsusb | grep -i net
yael@yael-HP-Mini-210-1000:~$ lsusb | grep -i net
yael@yael-HP-Mini-210-1000:~$ lspci | grep i net
grep: net: No such file or directory
yael@yael-HP-Mini-210-1000:~$ sudo apt-get --reinstall install bcmwl-kernel-source
[sudo] password for yael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/896kB of archives.
After this operation, 2,597kB of additional disk space will be used.
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 141221 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.35-23-generic
Building for architecture i686
Building initial module for 2.6.35-23-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-23-generic/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
yael@yael-HP-Mini-210-1000:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
yael@yael-HP-Mini-210-1000:~$ ^C
yael@yael-HP-Mini-210-1000:~$ 


The above script first shows Hippytaffs first two suggestions and then shows slixz85's suggestion. The last command is the one that Hippytaff suggested last. What should I do?
I do not have a dell, I have a HP Mini 210 netbook.

---

### Post by Yaely7 on 2010-11-26
B
u
m
p

---

### Post by slixz85 on 2010-11-26
you just need to search for your computer model drivers i did a quick little search i cant find your mini 2010-1000 but i found drivers for the 2010-1010

[http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-drivers-Linux-for-Broadcomm-4322-AG-Network-Adapter/m-p/262305](http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-drivers-Linux-for-Broadcomm-4322-AG-Network-Adapter/m-p/262305)

[http://www.netbookfiles.com](http://www.netbookfiles.com) try this too

---

### Post by Yaely7 on 2010-11-26
> **slixz85 said:**
> you just need to search for your computer model drivers i did a quick little search i cant find your mini 2010-1000 but i found drivers for the 2010-1010

I am new to Ubuntu, so I really do not no how to do anything.

---

### Post by slixz85 on 2010-11-26
the above link i just gave show these steps for a 1010 user to use since your drivers are hp give it a try (need to be connected wired to install these drivers cant download and use them (maybe but few work that way):
HP Mini 1010nr
Everything except wifi works "out of the box"; webcam, hotkeys, 3D Graphics, sound, USB, touchpad, mic, etc.

A wifi fix has been made available by performing the following:

1. Connect to Ethernet.

2. Update WL using System->Administration->Update Manager.

3. Restart.

4. Go to System->Administration->Hardware Drivers

5. Deactivate b43 and STA drivers.

6. Reactivate b43 drivers.

8. Close Hardware Drivers and open Synaptic Package Manager.

9. Flag bcmwl-modaliases for removal.

10. Flag bcmwl-kernel-source for (re)installation.

11. Apply changes and restart.

12. Wireless will be functional, and remains functional after subsequent restarts.

---

### Post by Hippytaff on 2010-11-26
Sorry, didn't mean to abandon you...had to drive home and get the kids food cooked, but looks as though you are in capable hands :-)

---

### Post by slixz85 on 2010-11-26
lets hope:mrgreen:

---

### Post by Hippytaff on 2010-11-26
I think you need to uninstall and reinstall the BCM4312 driver.

---

### Post by slixz85 on 2010-11-26
for sure

---

### Post by Hippytaff on 2010-11-26
or use ndiswrapper to install the windows driver
[http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Using_BCM43xx_cards_using_bcm43xx_or_ndiswrapper_with_Sabayon](http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Using_BCM43xx_cards_using_bcm43xx_or_ndiswrapper_with_Sabayon)

---

### Post by Yaely7 on 2010-11-26
Thanks guys, WiFi finally works! But I have one more question, why doesn't ubuntu recognize the left and right mouse buttons on the netbooks touchpad.

---

### Post by Hippytaff on 2010-11-26
not sure, works ok with me...maybe start a new thread :-)

...but how did you fix it? Ndiswrapper?
Not just becuause I'm intrigued...others can benefit from what you did...and also...remember to mark the thread as solved in the forum tools at the top of the page so others with the same issue can do what you worked out to do :-)

---

### Post by Yaely7 on 2010-11-26
I tried slixz85s, it worked well.

---

### Post by Hippytaff on 2010-11-26
> **Yaely7 said:**
> I tried slixz85s, it worked well.

Can you expand on that for the people who may need to do the same (and me because I might have this autistic need to know :-) )

---

### Post by Pennachi on 2010-11-26
My parents laptop have a Broadcom BCM4322 and about once every several months the internet won't work and I have to uninstall and reinstall the drivers and it is a pain. They are on 10.10 amd64. I was wondering if it was a 64 bit compatibility issue. If nobody knows it isn't a huge issue but I figured I would post this in hopes of some help. Also, they are using the proprietary drivers. Do they even have the open-source versions available?

---

### Post by Hippytaff on 2010-11-26
Don't know why it would work intermittently...unless it's something to do with new kernels maybe :-)

---

### Post by Pennachi on 2010-11-26
Yeah I have no idea. Again, it isn't a huge issue so I am not even worried about it. And it is tough to fix permanently because there isn't anything wrong right now.

---

### Post by t4thfavor on 2010-11-26
It's really easy to fix permanently, you go on ebay, and buy a 9USD atheros card of the apropriate type for your PC, and then you remove the Broadcom chip, and hit it with a hammer, or mail it to the devs of b43. Then you put the Atheros card into the void where the Broadcom used to be. Reboot, and connect to your favorite wifi hotspot.

If atheros is not your thing, and you have a compatible Intel CPU, you can buy a 5USD IWL3945 or 2200 (Intel).

---

### Post by slixz85 on 2010-11-26
i think its just broadcom support. no good skills with bugs or somethin. i've read on the net too many issues with the broadcoms i got one myself. it connects everytime but have had to remove then install the drivers again couple of times because for some reason the net would get real laggy and download speeds constantly dropping to idle.

no problem yaely i was damn frustrated at first tryin to get my wifi too work had to say somethin lol

---

### Post by Derekisamazing on 2011-06-18
> **slixz85 said:**
> let me guess you got a dell too? just need to know what kind of card you got. i use a dell mini inspiron 10 with broadcom 43XX
my install was this
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
that is a definited driver needed for most dells if that is what you have.
you will need to install this or the driver you need by wired connection for best install

This was an instant fix for my Dell Inspiron. Thanks :)

---

### Post by t4thfavor on 2011-06-18
I still like my fix way better as you still end up with a much more stable and speedy wireless interface, and you get to break something in the process.

---

