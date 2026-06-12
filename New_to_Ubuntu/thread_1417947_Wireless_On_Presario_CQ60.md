---
title: "Wireless On Presario CQ60"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Jonathan 56 on 2010-02-28
In Ubuntu 9.10 I cant turn on my wirless. Ive got a Presario CQ60. Wat do I do to get it going.

---

### Post by 2hot6ft2 on 2010-02-28
> **Jonathan 56 said:**
> In Ubuntu 9.10 I cant turn on my wirless. Ive got a Presario CQ60. Wat do I do to get it going.
There are a lot of versions of the CQ60. What wifi card does it have?
In a terminal run
Applications > Accessories > Terminal
```
lspci
```
and post the results.

---

### Post by n0dix on 2010-02-28
The way i do it in my Dell inspiron 6400 was install the property driver that suggest Ubuntu and use networkmanager (nm-applet).

---

### Post by Jonathan 56 on 2010-02-28
it tells me that commad not found

---

### Post by 3rdalbum on 2010-02-28
> **Jonathan 56 said:**
> it tells me that commad not found

Copy and paste it into the terminal.

L for Larry
S for Sam
P for Peter
C for Chris
I for Igloo

The lspci command will tell you the name of the chipset for the wireless device, so you can then use Google to tell you if there's anything you need to do to get the wireless device going on Ubuntu.

If the device is hooked up with USB, you would use the 'lsusb' command instead.

However the first thing I'd do is connect the computer to an Ethernet port on your router so you have a connection, then go to Synaptic Package Manager and hit the Reload button so you have the Ubuntu package list, then quit out of Synaptic and go to the Hardware Drivers program to see if there are any drivers that can automatically be downloaded and installed for you.

---

### Post by lkraemer on 2010-02-28
Jonathan,
First we need to know what hardware your Laptop has installed.

Just use "copy & paste" for the commands.
And, there is a difference in LSPCI and lspci.
```

lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.

lk

---

### Post by Jonathan 56 on 2010-03-01
Its got broadcom.

---

### Post by 3rdalbum on 2010-03-01
> **Jonathan 56 said:**
> Its got broadcom.

That's not exactly all the information we asked for... but try what I suggested in the last paragraph of my post.

---

### Post by lkraemer on 2010-03-01
Jonathan,
Obviously you can't follow instructions, so I'd recommend you
do some GOOGLE searching and lots of reading on "broadcom".

You'll find that you need to install some stuff, maybe
some firmware, maybe Blacklist some stuff, and then you'll be all set.

Good Luck!

lk

---

### Post by Jonathan 56 on 2010-03-01
Think Ive found them.
 
Atheros Ar 5007 802.11b/g wifi adapter
Micosoft Virtual Wifi Miniport
NVIDIA nForce Networking Controller.
 
Thanks For help out. Hope this is the info you need to help. 
 
Thanks

---

