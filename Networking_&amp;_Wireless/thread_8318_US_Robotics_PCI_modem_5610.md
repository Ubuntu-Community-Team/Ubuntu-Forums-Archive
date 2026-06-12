---
title: "US Robotics PCI modem 5610"
date: 2004-12-16
forum: Networking &amp; Wireless
---

### Post by Denis the P. on 2004-12-16
Hi everyone,

First of all, let me tell you that I am really impress by the Ubuntu distribution. I really would like to keep it as my primary OS. My USB drive and my Sony digital camera was recognized right away....but... I have big problems with the modem. It was well recognized by FC3 but I had other problems with this distribution and I consiber Ubuntu to be exactly what I need. I have to tell you that I am just a little bit more than a beginner in Linux (I know how to do some things in terminal mode). If I could get the modem to work in Ubuntu that would be, I think, my greatest Christmas gift!

Ok, when I check the devices, the modem shows up as:

US Robotics PCI modem 5610 OEM

In Windows, it is on COM3, so I tried setting it with the information in the UbuntuDialupHowTo ( sudo pppconfig, ttyS2, etc...) but it did not work at all (even when trying other ttyS?). 

I made lspci -vv and the modem is there with IRQ 11 and port d000. So I told myself, what if I tried the install with the setserial command, but I get the message that no such command exit....

Please, keep me beleiving in Santa  :|

---

### Post by Denis the P. on 2004-12-16
I made it! It works!

I found the deb package for setserial installed it.

dev/ttyS4 irq 11 port 0xd000

the only thing that is weird is that pppconfig see the modem at ttyS14 ???  :mrgreen:

---

### Post by Paki on 2004-12-31
Denis,

I have the same modem and the same problem... and apparently I know a lot less about Linux than you.

No chance you could give a newbie-friendly set of directions on how you got things working?

Thanks!

best regards,

- Paki

---

### Post by az on 2004-12-31
I have a hardware modem (Topic Semiconductor) that needs to be tweaked into working with setserial too.

Install setserial:
[http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/](http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/)

then do
lspci 
and find the entry that is your modem.  Note the port address and the irq.

In my case, I then do:

sudo setserial /dev/ttyS2 port oxdba0 irq 5 uart 16550A

You can use whatever ttyS you want, just do not use the one that is already present (you serial port, if you have one)

---

### Post by Paki on 2005-01-05
Sorry - I'm so clueless. I can't figure out what to download and how to install setserial!

Any help appreciated!

Thanks!

- Paki

---

### Post by az on 2005-01-05
Download this 
[http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/setserial_2.17-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/setserial_2.17-36_i386.deb)

Boot Ubuntu and cd to the directory where the file is saved - either on a windows partition or a floppy...

cd /media/floppy
sudo dpkg -i setserial*

---

### Post by Ominus on 2005-02-28
[QUOTE=azz]Download this 
[http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/setserial_2.17-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/setserial_2.17-36_i386.deb)

Boot Ubuntu and cd to the directory where the file is saved - either on a windows partition or a floppy...

cd /media/floppy
sudo dpkg -i setserial*[/QUOTE]
 I got this problem too.. but when I try a lspci -vv It doen't show the port... I know it is COM3 and IRQ 16 because I looked in WinXP Device Manager, but i don't know the hexadecimal to use in setserial command.
Also.. i don't have the /proc/pci file... I got a problem?

---

### Post by Ominus on 2005-03-06
Still no solution... =/

---

### Post by Denis the P. on 2005-03-17
Install setserial with: sudo dpkg -i 
and config with sudo pppconfig

---

### Post by az on 2005-03-17
[QUOTE=Ominus]I got this problem too.. but when I try a lspci -vv It doen't show the port... I know it is COM3 and IRQ 16 because I looked in WinXP Device Manager, but i don't know the hexadecimal to use in setserial command.
Also.. i don't have the /proc/pci file... I got a problem?[/QUOTE]


Is there any entry in lspci?  It may be a software modem.

---

