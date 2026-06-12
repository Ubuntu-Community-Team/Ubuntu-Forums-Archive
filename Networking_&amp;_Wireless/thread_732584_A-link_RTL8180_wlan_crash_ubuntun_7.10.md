---
title: "A-link RTL8180 wlan crash ubuntun 7.10"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Kuhitsu on 2008-03-23
so, yep.. this far.

I have HP Omnibook XE3, ubuntu 7.10 in it. all did work, even my wlan card - rtl8081,, BUT when i did install ubuntu-restricted ... thingies, it all crash. everty time when i try to connect to wireles... whole ubuntu crash. don't know is this just bad luck or did those restricted package do something?

I've been so long out of Ubuntu that I'm still in learning mode... but i truly would like to hear some ideas what to do.

ps. just to make sure.. how can i remove all those restricted thingies that .. ubuntu-restricted-extras ?

anyhow, any ideas whit "guide to the dumb" would be nice

---

### Post by alan34 on 2008-03-23
Hi first are you sure that chipset that you are using is rtl8081 and not rtl8180?

Go Applications - Accessories - Terminal then type

lspci

lsusb

and see what you get. The rtl8180 / rtl8185 (mine) chipset causes a kernel panic in Gutsy.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window XP files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card. Open Places right click to make new folder and drag the files from your cd into the folder.


In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)
(Go to Applications - Accessories - Terminal)

then copy and paste

sudo ndiswrapper -i YOUR.inf
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

Reboot and you should be okay well at least I was.

Then look in Network Manager to set your ESSID and WEP password

Good luck


To remove ubuntu restricted extras go System - Administration - Synaptic Package Manager and search
 for ubuntu-restricted-extras right click and remove although I don't think this is your problem

---

