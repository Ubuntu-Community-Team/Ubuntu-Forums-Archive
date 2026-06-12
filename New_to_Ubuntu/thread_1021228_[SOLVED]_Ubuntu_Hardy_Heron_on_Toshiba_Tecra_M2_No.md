---
title: "[SOLVED] Ubuntu Hardy Heron on Toshiba Tecra M2 Notebook"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by khubliakhan on 2008-12-25
Hi Everyone,

Ok so I have installed Hardy Heron on my Desktop PC (impressed with the OS) and want to install it on my Notebook which has the following spec:

Toshiba Tecra M2 
Pentium M 735 1.6GHz 
1GB Memory 
60GB HDD 4200 RPM 
DVD/CD-RW Combo Drive 
14" XGA TFT Screen 
nVIDIA GeForce FX 64MB VRAM 

56k Modem 
LAN 
WLAN (Intel PRO/Wireless 802.11 BG) 
Bluetooth 
SD Card reader 
Windows XP Professional 
UK Keyboard 

Other info can be found on this link:

[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=101760&DISC_MODEL=1&service=UK#0]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=101760&DISC_MODEL=1&service=UK#0")

I am worried about the graphics card driver support with Ubuntu - although it is an old laptop it works with Vista no problems.

Can any kindly person offer some advice on the installation?

---

### Post by theozzlives on 2008-12-25
From the specs, it don't seem all that old. I'm unclear what you need help with, installing Ubuntu??

---

### Post by nhasian on 2008-12-25
i think theres many different models of nvidia geforce fx.  you didnt specify which one you have.  if you have ubuntu running you can type in a terminal:

```
lshw -C display
```

you can boot off a LiveCD and test out Ubuntu without making any changes to your system.

---

### Post by khubliakhan on 2008-12-25
Wow thanks for the replies,

I am running off the live CD and the display is pretty poor - when I type in the command lshw -C display I get the following:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV34M [GeForce FX Go5200 32M/64M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5

Question 1: Before I install Ubuntu I just want to ensure I get a decent display on the system. Will Ubuntu support the Graphics card?

Question 2: I also want to dual boot with Backtrack3 and need guidance as to how I would do this - I want to give Backtrack about 7GB of space?? Which should be installed first?
The partioning scheme is always somewhat confusing in Linux and as a noob I am stuck with the planning?

Thanks in advance

---

### Post by stalkingwolf on 2008-12-25
I think I would install Backtrack first.  As it is not something
I would use everyday and Grub defaults to Ubuntu.

I have 8.04 installed on an old Tecra 8200.  I had to manually configure
the cyberblade video for the resolution I wanted but that was all.

---

### Post by khubliakhan on 2008-12-25
Whoohoo,

Got Ubuntu and Vista Dual Boot - had to enable the restricted driver thing but all is well so far.

I now want to install Backtrack 3 on 5GB ext3 partition - I was following the advice as given on the offensive-security wiki - I think I am too late in realising this was meant for Backtrack 2.

My partition setup is as below (according to Ubuntu installer)
device type mount point

/dev/sda1 ntfs /media/sda1 ----> Vista 40GB
/dev/sda2 ext3 /media/sda2 ----> Backtrack 3 meant to be here
/dev/sda3 swap /media/sda3 ----> Swap (Can it be used by both Ubuntu and BT3?
/dev/sda4 ext3 /media/sda4 ----> Ubuntu Hardy Heron - Working!!!

Any further advice as to how I can install BT3 now??

Thanks in advance

---

