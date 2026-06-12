---
title: "network woes"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by zygoat_D on 2007-06-28
here is the deal. it seems as though every other time i run Ubuntu it does NOT connect to my network. i live in an apartment with high speed internet. every other time it works fine and then the next no go at all. i have to restart completely and then it works like a charm. what gives? does anybody know what might be causing this? or any ideas that might help.


some of my system info to help out

Ubuntu 7.04 x_86  64
Realtek Rtl 8111/8168b pci express gigabit Ethernet controller (its on board dual gigabit ie 2 connections i am only using one the other i use in windows to network my laptop)
amd athlon 64 x2
msi k9a platinum
ati north and south bridge


any help would be much appreciated!!!

---

### Post by kevdog on 2007-06-29
Try editing /etc/modprobe.d/blacklist:

sudo gksu /etc/modprobe.d/blacklist  <---This opens the editor

blacklist ipv6


Reboot! 

Kind of a shot in the dark if it works!

---

### Post by zygoat_D on 2007-06-29
well that was a no go but thanks for trying maybe someone else will have an idea


ps this is what it said
bash: blacklist: command not found

---

### Post by WinterWeaver on 2007-06-29
nope... done it wrong

you have to add that line into the file

```
sudo gedit /etc/modprobe.d/blacklist
```

If you open that file, you will see many things that is 'blacklisted'...

ie... mine looks like this

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

# network woes
blacklist ipv6
```

try it again ^_^

---

