---
title: "rtl8185 fresh install help please"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Anacranom on 2008-03-16
Could someone please help me with problem with rt8185 card, I have never made it work, I had dual-boot XP and Ubuntu 7.10 and just yesterday I put in a new hard drive (removed others) and fresh installed WinXPP and all drivers, partitioned the hdd and installed 7.10 amd64. Installed envy, cedega, and COH, but still cant get the wireless rt8185 card working. This is a problem because we've moved into my in'law's home and not practical to string cat5 all over the place. The card works fine in winXP, since i've started fresh i was hoping someone could help me Start Fresh with this, before I muck it all up, Thank you for any help.
i think i did something stupid, now it doesn't show up in ifconfig (i think i removed the drivers) oh well, please help.

---

### Post by alan34 on 2008-03-16
You might like to try this ....................

My card is a Peak pci wireless card with rtl8185 chipset I also had the kernel panic when I tried to connect to my wireless router, really annoyed as the card worked with Edgy and Fiesty.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window XP files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card.

In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)
(Go to Applications - Accessories - Terminal)

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

Reboot and you should be okay well at least I was.

Good luck

---

### Post by jjgauthi on 2008-03-29
Okay i've tried your fix, for me it does not work, it says invalid driver?

any other suggestions?

Okay second attempt - You my friend area  genius...

It has to be the windows 98 drivers, I tried with XP and nothing, I put i the 98 drivers and VOILA.  It works, Thank you very much..

---

### Post by FleetAdmiral74 on 2008-04-20
I followed instructions on a fresh install of Ub7.04. Seemed to work, when I right clicked the network icon i saw the various networks. I then restarted (because I had just done the full upgrade with the new kernel) and it stopped working. Wireless option still shows up, but no settings/configuration/networks or anything. 

Did this big upgrade mess something up? I tried following the instructions again, thinking maybe it would correct itself....fail

---

