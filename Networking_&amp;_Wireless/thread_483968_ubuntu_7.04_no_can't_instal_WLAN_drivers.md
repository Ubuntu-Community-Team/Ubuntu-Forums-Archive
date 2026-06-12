---
title: "ubuntu 7.04 no can't instal WLAN drivers"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by hardwarecompugeek on 2007-06-25
About a week ago I installed ubuntu 7.04 on my second hard drive, now that I have it installed, I would like to connect to the Internet, so I can quit using Windows! However, the card that I installed in my computer uses the RTL8185 (or something close to that) chipset. I downloaded the linux drivers and followed the instructions.

I got Error 2 after trying to Extract the files. (This was I think the 3rd command in the instructions)


The commands were (replace file with the actual file name)
tar file
cd file
make

Thanks in Advance for your Help!

---

### Post by kevdog on 2007-06-25
Can you be more specific about the error??? Make tries to compile the files from source.  If you do not have the build-essential package installed you can not compile from source.

Using the install cd - put into drive then type
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Then try the command make.

---

### Post by hardwarecompugeek on 2007-06-25
uhhh...more details:

kevin@LAN250:~$ sudo tar xzf /home/kevin/Desktop/rtl8180-0.21.tar.gz
kevin@LAN250:~$ sudo cd rtl8180-0.21
sudo: cd: command not found
kevin@LAN250:~$ cd rtl8180-0.21
kevin@LAN250:~/rtl8180-0.21$ sudo make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/kevin/rtl8180-0.21 MODVERDIR=/home/kevin/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
rm: cannot remove `/home/kevin/rtl8180-0.21/rtl8180-0.21': Is a directory
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [2.6] Error 2

The WLAN card CD does not include linux drivers, just windows.

---

### Post by kevdog on 2007-06-25
You dont have to do everything with the sudo command.

For example, for make
make

However for installation
sudo make install

Thats all I can tell you.  You need to provide more details about your card:
lspci

---

### Post by hardwarecompugeek on 2007-06-25
RTL8185 (RealTek)  is the chipset for the PCI card, but I do not know the name of the card, because it is generic. That is all I can tell you.

---

### Post by kevdog on 2007-06-25
Can you do me a favor and post the following file:

/etc/modprobe.d/blacklist

I think your card might be supported without having to use ndiswrapper.

---

### Post by hardwarecompugeek on 2007-06-26
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
```

Anything Else???

---

### Post by kevdog on 2007-06-26
Just a thought -- Im not sure if this will work but edit your blacklist file:
gksu gedit /etc/modprobe.d/blacklist

Make following modification:
# blacklist r818x

Reboot!

Basically your driver for your card r8185 was getting blacklisted at boot.  I removed the blacklist statement so hopefully the driver for your device will load.  Hopefully however you dont get the error or BUG talked about.

If you are able to boot successfully hopefully your device drivers will be loaded at boot and you can then just plug in your wireless device and use it!

---

### Post by hardwarecompugeek on 2007-06-26
I got it!

I deleted the old drivers I had installed from before (I had to log in as root) installed new ones with ndiswrapper, all after I modified /etc/modprobe.d/blacklist. I rebooted and changed the network settings. Infact I posted this in ubuntu!

---

