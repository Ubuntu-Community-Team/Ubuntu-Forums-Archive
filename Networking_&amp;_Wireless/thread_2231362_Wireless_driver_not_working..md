---
title: "Wireless driver not working."
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by arturodeliagmail. on 2014-06-19
Hi. I have a wireless problem and have had no success after following the steps. However, I did get that wireless info output. Here it is (thank you for your help!):


[COLOR=#000000]```
[/COLOR]
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


##### kernel #####


Linux diego-Presario-V3500-Notebook-PC 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:24 UTC 2014 i686 athlon i686 GNU/Linux


##### lspci #####


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:30d6]
    Kernel modules: forcedeth


04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1375]
    Kernel modules: wl, ssb


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


No way to aquire root rights found.


##### iwlist channel #####


##### lsmod #####


##### modinfo #####


##### modules #####


lp


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### udev rules #####


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:0d.0/0000:04:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


########## wireless info END ############
[COLOR=#000000]
```[/COLOR]

---

### Post by westie457 on 2014-06-19
Welcome [COLOR=#DD4814][COLOR=#000000][arturodeliagmail.]("http://ubuntuforums.org/member.php?u=1930199"), as you might have guessed the OP has not got back to confirm whether varunendra's solution worked or failed.
So assuming you followed the instructions posted and installed 'linux-firmware-nonfree' did you reboot your system and disconnect the internet cable?

If you did the above and it is still not working I suggest you ```
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
sudo modprobe b43
``` if still no wifi try a reboot remembering to disconnect the cable.

Let us know what happens.
Thank you.[/COLOR][/COLOR]

---

### Post by varunendra on 2014-06-20
..and please also edit your above post, arturodeliagmail., to wrap the output part in 'Code' tags, as I requested in my first post. :)

By the way, I also concur that a reboot is probably all you need.

---

### Post by arturodeliagmail. on 2014-06-20
Fixed my post with code tags. Sorry!
Thanks again for your time in helping me out with this.
I rebooted first again, just in case... no luck. Btw, I don't have the network cable plugged in, because I don't have one handy right now (Currently living in a small mountain village in the Patagonia), but I do have access to the internet with my other machine. So if I can proceed in this manner installing without the internet, that would be great. I have been downloading the packages from my good machine from ubuntu's site: **packages.[B]ubuntu.com/ **[/B], transfering to a USB, and then running them through the Ubuntu package intaller.

So I followed the instructions from westie457. First command no problem, second installed it through the gui no problem, and the third line gave me an error:

```

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 185419 files and directories currently installed.)
Preparing to replace firmware-b43-installer 1:018-2 (using .../firmware-b43-installer_018-2_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-06-20 14:58:06--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... failed: Name or service not known.
wget: unable to resolve host address www.lwfinger.com
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4

```

... and then of course the last command through the terminal errors:

```

FATAL: Module b43 not found-

```

I rebooted, but alas, with such errors, I did not expect it to work. I'm happy to receive further input as to what to do. I'm really lost since I have just begun installing Ubuntu on the machines here in town for the folks (since XP is giving them now a hayday with no support, tired of viruses, etc), so any information will help me to keep this movement going! Thank you!

---

### Post by varunendra on 2014-06-21
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by arturodeliagmail. on 2014-06-21
Thanks again! Here are the results:

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


diego-Presario-V3500-Notebook-PC 3.11.0-23-generic i686,  Ubuntu 13.10, saucy


CPU    : Mobile AMD Sempron(tm) 3600+
Memory : 1952 MB
Uptime : 14:19:33 up 5 min,  1 user,  load average: 1.57, 1.31, 0.65




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP67 Ethernet [10de:054c] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:30d6]
	Kernel modules: forcedeth
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1375]
	Kernel modules: wl, ssb




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05dc:a761 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








module parameters ~~~~~~~~~~~~~~~~~~




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o======o========o==============o=========o===========o==============o===========
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
================o======o========o==============o=========o===========o==============o===========
                |      |        |              |         |           |              |           
----------------+------+--------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


auto lo
iface lo inet loopback




resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


No way to aquire root rights found.




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:0a.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:0d.0/0000:04:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.11.0-23-generic root=UUID=34fbd430-3d25-473b-940d-6ff77b33e064 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.454568] audit: initializing netlink socket (disabled)


	======== Done ========


```

---

### Post by varunendra on 2014-06-25
Sorry for not being able to reply sooner, office matters, shortage of time etc-etc.

The status of your system looks a bit abnormal, but please try the usuals first. Please open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo apt-get purge bcmwl-kernel-source
```
Closely watch the outputs on the screen and post back if you see any errors.

Once the above command finishes its job, follow the instructions in this post to install the "linux-firmware-nonfree" package : [http://ubuntuforums.org/showpost.php?p=13039309](http://ubuntuforums.org/showpost.php?p=13039309)

Then reboot and see if the wireless works. If not, please post back the outputs of the following commands -
```
dpkg -l | grep bcmwl
dmesg | egrep -i 'b43|firmware'
modinfo b43
modinfo wl
```

---

### Post by Bucky Ball on 2014-06-25
*Post(s) moved to own thread in **Networking & Wireless**.*

---

### Post by varunendra on 2014-06-25
Thanks BB, I hope this one is easily solvable. :)

---

### Post by Bucky Ball on 2014-06-25
> **varunendra said:**
> Thanks BB, I hope this one is easily solvable. :)

All good. 

To the OP: If there is any possiblity of dragging your machine to the ethernet cable and getting online this would probably be fixed in a jiffy. A catch 22, but the instructions in westie457's post would probably work immediately, but you need to be online with a cable to perform them successfully. That card (BCM4311) is very common and very compatible with Ubuntu. 

Here are the instructions for getting it working without an internet connection:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

From that page:

> b43 - Open source driver

    For Chip ID BCM4306 (rev 03), BCM4309, BCM4311, BCM4312, BCM4318, BCM4322, BCM4331, BCM43224 and BCM43225.

B43 is what you want, i.e. b43-fwcutter and firmware-b43-installer. As westie457 has stated. 

Good luck. ;)

---

### Post by arturodeliagmail. on 2014-06-25
Thank you again. I do appreciate the time anyone is helping me get this solved, so no worries on the timeframe to respond.
So no luck again, but I did copy the outputs below. I didn't do what Bucky Ball suggested yet because I did not want to confuse any extra steps, plus I reviewed them and they seem quite similar to what I already have done. I did try the network cable (roamed the town for it), added a new network connection through the gui for ethernet and although lights are on, nobody's home. As I feared, the whole networking on this laptop is down. I am open to hearing if there are specific steps I should have taken with the cable.

```

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 185419 files and directories currently installed.)
Preparing to replace firmware-b43-installer 1:018-2 (using .../firmware-b43-installer_018-2_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-06-20 14:58:06--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... failed: Name or service not known.
wget: unable to resolve host address www.lwfinger.com
dpkg: error processing firmware-b43-installer (--install):
 subprocess installed post-installation script returned error exit status 4


FATAL: Module b43 not found-


```

... after the reboot and ran the command as asked...

```

diego@diego-Presario-V3500-Notebook-PC:~$ dpkg -l | grep bcmwl
diego@diego-Presario-V3500-Notebook-PC:~$ dmesg | egrep -i 'b43|firmware'
[    0.091368] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.138056] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-09] only partially covers this bridge
diego@diego-Presario-V3500-Notebook-PC:~$ modinfo b43
ERROR: Module b43 not found.
diego@diego-Presario-V3500-Notebook-PC:~$ modinfo wl
ERROR: Module wl not found.
diego@diego-Presario-V3500-Notebook-PC:~$ 

```

I should probably note I am getting "System program problem detected. Do you want to report the problem now?" multiple windows when I boot it up, as well, in System Settings>Software & Updates>Additional Drivers>Broadcom Corporation: BCM4311 802.11b/g Wireless LAN Controller. This Device is not working. [O] Do not use this device" and even if I try to select the radio button above to the "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)", it reverts back to the "Do not use this device".

---

### Post by Bucky Ball on 2014-06-25
Yep, that is telling it to you straight. The device is not working. You're right when you say the lights are on, but nobody is home. Seems the system can see the device, even offering you the correct driver, but is telling you:

> **arturodeliagmail. said:**
> This Device is not working. [O] Do not use this device" and even if I try to select the radio button above to the "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)", it reverts back to the "Do not use this device".

I'm presuming you are online with a cable while trying this?

---

### Post by Hadaka on 2014-06-25
Hi,arturodeliagmail

this -> Broadcom 802.11 Linux STA wireless driver source from bcmwl -kernel-source (proprietary) is also known
as the "wl" driver and is what you currently have loaded...it is not the correct driver for your device.
 The best driver for your broadcom wireless card [14e4:4311 is -> linux-firmware-nonfee

first let's make sure we get rid of the wrong driver and any of it's files..
with the cable attached and online wired, open a terminal crrl/alt/t and then
COPY and paste one iine at a time.
*Do every line,even if you get an error message...that is not a problem
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
now we should be ready load the correct driver...whith the ethernet cable still
attached and connected to the internet..please COPY and paste the following
```
sudo apt-get-update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
remove the ethernet cable...BOOT ...and test the wireless.
thanks.

---

### Post by varunendra on 2014-06-26
Yup, the "wl" driver (the thing that the "Additional Drivers" is trying to gift you) is NOT correct for this card, the native "b43" is.

But hey! What is this ?? -
> **arturodeliagmail. said:**
> ```
diego@diego-Presario-V3500-Notebook-PC:~$ modinfo b43
**[COLOR="#FF0000"]ERROR: Module b43 not found.[/COLOR]**
```
Crying out loud that the kernel is [FONT=Comic Sans MS][COLOR="#FF0000"]broken[/COLOR][/FONT]. Nothing is going to work, not what I or Hadaka or BB or anybody else suggested until that is fixed.

Please post the output of -
```
uname -mr
```
It will tell us which kernel version you are using. We can then download it manually from **[here]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/")** > copy it to your current installation > install with 'sudo dpkg -i <package name>' > reboot > celebrate.

Alternative is also easy - just reinstall Ubuntu - takes about 10-20 minutes depending upon system's speed. Good option if the installation is fresh and you have nothing to worry about (settings, additional programs, data etc.).

---

### Post by arturodeliagmail. on 2014-06-27
Bucky Ball -> Yup!
Hadaka -> Tried, but of course alas no network does not allow me to resolve to download the package... but moving on to....
varunendra -> Makes sense! Looking to much through my magnifying glass, seems like the more obvious made sense.


command output: 3.11.0-23-generic i686


Did a manual download (this device does NOT like to boot from a USB... PITA to have done it just once to get Ubuntu installed)... and failed to install:

```

(Reading database ... 185582 files and directories currently installed.)
Unpacking kernel-image-3.11.0-23-generic-di (from .../kernel-image-3.11.0-23-generic-di_3.11.0-23.40_i386.udeb) ...
dpkg: error processing /media/diego/UUI/kernel-image-3.11.0-23-generic-di_3.11.0-23.40_i386.udeb (--install):
 trying to overwrite '/lib/modules/3.11.0-23-generic/modules.order', which is also in package linux-image-3.11.0-23-generic 3.11.0-23.40
dpkg-deb (subprocess): decompressing archive member: lzma write error: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2

```

I re-downloaded but no luck. Maybe it will be easier to re-install. I can't boot off a USB... so what process would you recommend to maybe change the GRUB from the gui to look for the USB (like I did it before, but I did that from Windows last time)?

---

### Post by varunendra on 2014-06-28
You have to install "linux-image..." package, not "kernel-image..".

Please download this package : [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.11.0-23-generic_3.11.0-23.40_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.11.0-23-generic_3.11.0-23.40_i386.deb)

Copy it to your desktop > open a terminal > run the following commands to install it -
```
cd Desktop
sudo dpkg -i ./linux-image-*.deb
```
(make sure there is only one "linux-image..." file on the desktop, else the above command will install all of those it finds on the desktop.

I am not sure installing a running kernel is simple as above or requires geeky steps like booting into older kernel or 'chroot' from live session etc. But if the above steps finished without errors, you should have a working wireless (assuming you have already installed the firmware following instructions from others, else that would be another tiny step to make the wifi work.

---

### Post by arturodeliagmail. on 2014-06-28
Downloaded, installed (without errors), rebooted. Nothing. So I re-installed the linux-firmware-nonfree_1.14ubuntu1_all and no errors, but after a reboot, still nothing. I ran the old commands to see if there was anything that I can see and they seem identical the error messages...

```

diego@diego-Presario-V3500-Notebook-PC:~$ dpkg -l | grep bcmwl
diego@diego-Presario-V3500-Notebook-PC:~$ dmesg | egrep -i 'b43|firmware'
[    0.087329] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.130532] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-09] only partially covers this bridge
diego@diego-Presario-V3500-Notebook-PC:~$ modinfo b43
ERROR: Module b43 not found.
diego@diego-Presario-V3500-Notebook-PC:~$ modinfo wl
ERROR: Module wl not found.
diego@diego-Presario-V3500-Notebook-PC:~$ 

```

Unless I missed a step, I think at this point it may be easier to re-install, but without the BIOS supporting boot from USB, how can I get GRUB to detect the USB on boot? It would be a software (I imagine) like I got for Windows, that overwrote the boot manager.

---

### Post by varunendra on 2014-06-28
Interesting, and mysterious!

Anyway, I agree that reinstalling is easier at this point.
> **arturodeliagmail. said:**
> I think at this point it may be easier to re-install, but without the BIOS supporting boot from USB, how can I get GRUB to detect the USB on boot? It would be a software (I imagine) like I got for Windows, that overwrote the boot manager.

Some good answers here : [https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/how-to-boot-from-an-usb-stick-without-bios-support-using-grub2-776192/](https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/how-to-boot-from-an-usb-stick-without-bios-support-using-grub2-776192/)

Also, how to directly boot and install from the ISO on hard disk using Grub2 : [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by arturodeliagmail. on 2014-06-29
Thank you for all your help! I will proceed with re-installing. I'm not sure if I should now mark this thread as solved since really, it's a workaround. Thank you again!

---

### Post by Bucky Ball on 2014-06-29
Solved will help others. Post a new thread for any further issues, but let's see if the re-install fixes this one first (before marking as solved). Good luck. ;)

---

### Post by arturodeliagmail. on 2014-08-18
Hello again! Just wanted to update that I finally got another computer (for repair) that could boot from USB, so I swapped the HDD's, installed ver 14, and had the same issue. So I tried again but with ver 12 and that worked! Upon first desktop login, ethernet detected right away, so then I did the first set of instructions posted and the wireless light went to blue, and worked like a charm. I think it's just the older hardware that didn't like the updates so I made sure to set it to not update. It may be the last OS this laptop sees.
Thank you again, everyone for all your help! Learned lots!

---

