---
title: "[SOLVED] &amp;quot;sudo modprobe ndiswrapper&amp;quot; crashes my laptop"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by 11zac11 on 2008-10-10
After installing ubuntu 8.04 I thought finely a OS I can life with, I get everything working apart form one thing, my WLAN card.
i have a Atheros 802.11 wireless card (so ubuntu says) and cant get it to work. I found the 
"How To: Install Ndiswrapper (source, svn) - with Included Problem Solving Suggestions"
when i get to the "Ok, to insert the ndiswrapper module into the linux kernel:
Code:
sudo depmod -a
Ensure you dont get any errors when running this command. Then:
Code:
sudo modprobe ndiswrapper"

at the "sudo depmod -a" nothing happens at all then when i do the next code the system crash's
does anyone know why this is cause i cant work it out why it keeps doing this?

---

### Post by cariboo on 2008-10-10
I'm not sure I understand exactly what you are saying, but I think you're saying that compiled ndiwrapper from source and now it crashes when you try to install the module, it that correct?

What I would suggest is to use the version of ndiswrapper that is on the LiveCD, as something is not right with the version you built from source. Look for /pool/main/n on the CD, ndiswrapper-utils, ndiswrapper-common and ndisgtk are the files you want.

Jim

---

### Post by caljohnsmith on 2008-10-10
Did you download the latest ndiswrapper (a tar.gz file) and compile it yourself, or did you install ndiswrapper through the repositories? Also, have you tried using the "sudo modprobe ndiswrapper" while using a different kernel? In other words, on system start up where you select Ubuntu in Grub's menu, have you tried booting into a different kernel (e.g. 2.6.24-19-generic or whatever you have available) and running that command?

EDIT: I see Jim beat me to the draw about the compiled ndiswrapper issue. :)

---

### Post by 11zac11 on 2008-10-11
"Did you download the latest ndiswrapper (a tar.gz file) and compile it yourself"

Yes i did download the file and complie it my self, and i havnt tryed using a different kernel i will give that i shot.

"I'm not sure I understand exactly what you are saying, but I think you're saying that compiled ndiwrapper from source and now it crashes when you try to install the module, it that correct?
" yes thats whats wroung and how do i get the live CD?

---

### Post by 11zac11 on 2008-10-11
"select Ubuntu in Grub's menu"
i cant seem to find that how do i get to it?

---

### Post by 11zac11 on 2008-10-11
ok i found it and i tryed it on all the different versions i have and they all crash so i guess its proberly something wroung with ndiswrapper maybe?

---

### Post by caljohnsmith on 2008-10-11
You'll need to first uninstall the ndiswrapper that you compiled; that means you'll need to go to the directory where you originally did a "sudo make install" to compile ndiswrapper, and instead do:
```
sudo make uninstall
```
I assume you have no internet connection in Ubuntu right now, not even an ethernet connection? If that is true, you can download following packages from packages.ubuntu.com from some other computer and copy them to your Ubuntu desktop:
```
ndiswrapper-utils-1.9
ndiswrapper-common
```
Once they are on your desktop, do:
```
sudo dpkg -i ~/Desktop/ndis*.deb
```
And that will install them. See if you can get that far, and we can work from there.

---

### Post by kevdog on 2008-10-11
The most common reason this is happening is b/c you have chosen the wrong windows driver.  I wouldn't go chasing my tail about ndiswrapper version or the ndiswrapper installation.  Verify you have the correct Windows driver version for your card!!

---

### Post by 11zac11 on 2008-10-11
"The most common reason this is happening is b/c you have chosen the wrong windows driver." I know its the right driver as i have used it before when i had to do a system reset. 
i do have ethernet connection i can us on my laptop is there a easyer way of downloading those files?

---

### Post by 11zac11 on 2008-10-11
im sorry i know im a complete noob but i cant work out how to uninstall it

---

### Post by kevdog on 2008-10-11
What do you want to uninstall??

ndiswrapper - the compiled version

or 

ndiswrapper - the installed version

or 

the windows driver?

If you list
sudo ndiswrapper --version

That should give you the version number.  In most cases, its not the ndiswrapper version per se that is the problem.  Also, FYI, just b/c you have used the windows driver from within windows, in some cases, this still doesn't mean that it will work from within linux.  Jamie Jackson has written an excellent tutorial where he has documented a working driver for several various chipsets.  I believe your broadcom ID is listed in his tutorial.  I would use the driver he provides a link to.

---

### Post by 11zac11 on 2008-10-11
i would like to uninstall ndiswrapper - the compiled version
and its Atheros card not a broadcom

---

### Post by kevdog on 2008-10-11
Ok, sorry about the confusion between Atheros and Broadcom.

Just to make sure --- Are you sure your Atheros chipset is not supported by madwifi?  That would save some headache.

The uninstallation procedures are posted near the bottom of the first post in this thread:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

You could cut and paste the code lines directly to the terminal.

---

### Post by 11zac11 on 2008-10-11
its ok and i dont think it is supported no but if this dosnt work i will try again to get madwifi to work

---

### Post by 11zac11 on 2008-10-12
"And that will install them. See if you can get that far, and we can work from there."

ok i uninstalled ndiswrapper and did as you said with the 2 files and they seems to have installed what do we do next then?
thank you very much

---

### Post by 11zac11 on 2008-10-12
This is what i got when i did what you said
"zac@zac-laptop:~$ sudo dpkg -i /home/zac/Desktop/ndis*.deb
dpkg - warning: downgrading ndiswrapper-common from 1.52-1ubuntu1 to 1.50-1ubuntu1.
(Reading database ... 109073 files and directories currently installed.)
Preparing to replace ndiswrapper-common 1.52-1ubuntu1 (using .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
dpkg - warning: downgrading ndiswrapper-utils-1.9 from 1.52-1ubuntu1 to 1.50-1ubuntu1.
Preparing to replace ndiswrapper-utils-1.9 1.52-1ubuntu1 (using .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...
"

---

### Post by caljohnsmith on 2008-10-12
So which Windows drivers are you using for your wireless card? I would recommend using the Win XP ones rather than Vista since the XP ones usually work better with ndiswrapper. To use the drivers with ndiswrapper, you need both the .inf and .sys files. So first make sure no drivers are installed with ndiswrapper:
```
ndiswrapper -l
```
If that lists a driver, then uninstall it with:
```
sudo ndiswrapper -e <driver name>

```
If you put your two wireless files (.inf and .sys files) on your Ubuntu desktop, then you can install them with:
```
cd ~/Desktop
sudo ndiswrapper -i *.inf
```
Then activate ndiswrapper:
```
sudo modprobe ndiswrapper
```
If that completes successfully, check for available wireless networks with:
```
sudo iwlist wlan0 scan
```
Let me know how that goes.

---

### Post by kevdog on 2008-10-12
Can you list your chipset again and are you working with a usb or pci card device? (or internal)?

---

### Post by 11zac11 on 2008-10-12
"So which Windows drivers are you using for your wireless card?" they are the Wireless Lan Driver 802abg Atheros Ver.5.3.0.45 for xp.
"Can you list your chipset again and are you working with a usb or pci card device? (or internal)?" its the Atheros 802.11 wireless LAN card

---

### Post by 11zac11 on 2008-10-12
ok i have just tryed what you said and as soon as i tryed "sudo modprobe ndiswrapper" it crashes again

---

### Post by caljohnsmith on 2008-10-12
One thing I forgot to mention is that since you've got an Atheros card, it is likely that Ubuntu is trying to use the madwifi drivers for your card; so if you want to use ndiswrapper instead of madwifi, you'll have to "blacklist" the Atheros drivers to prevent them from loading. 

But first, how about posting:
```
sudo lshw -C network
```
So we can see what your wireless chipset is.

---

### Post by 11zac11 on 2008-10-12
*-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:26:4e:84
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

---

### Post by kevdog on 2008-10-12
That chipset that you have is problematic from a Linux perspective.  Possibly give this thread a try:

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by 11zac11 on 2008-10-12
"That chipset that you have is problematic from a Linux perspective. Possibly give this thread a try:

http://ubuntuforums.org/showthread.php?t=766169"

Dude i dont know what else to say but i love you lol that work perfectly my wireless is now working thank you SOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO MUCH

---

