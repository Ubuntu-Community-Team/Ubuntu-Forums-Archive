---
title: "Lock-up when I try and connect to router. Help?"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by castrophany on 2008-03-05
I have a year-old Gateway MX6426 notebook with a Realtek RTL8185.

When I boot up the Ubuntu 7.10 disk, it detects the router just fine, but when I try and connect, my computer locks-up completely.

Any help would be awesome.

---

### Post by alan34 on 2008-03-06
I might be able to help with a rtl8185 chipset.

My card is a Peak pci wireless card with rtl8185 chipset I also had the kernel panic when I tried to connect to my wireless router, really annoyed as the card worked with Edgy and Fiesty.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card.

In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)
(Go to Applications - Acessories - Terminal)

then copy and paste

sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l
------------You should see something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

Now to load the driver when you boot

sudo gedit /etc/modules
----------You should see something like this add ndiswrapper at the end of the file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


Now we blacklist the linux driver

sudo gedit /etc/modprobe.d/blacklist
---------------At the end of the file add

# wireless network card driver
blacklist r8180

Reboot and you should be okay well at least I was. Only re-installed three times to get it to work

Good luck

---

