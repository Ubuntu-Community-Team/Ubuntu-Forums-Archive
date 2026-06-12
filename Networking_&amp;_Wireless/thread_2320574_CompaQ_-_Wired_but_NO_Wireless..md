---
title: "CompaQ - Wired but NO Wireless."
date: 2016-04-15
forum: Networking &amp; Wireless
---

### Post by Yazan on 2016-04-15
Hello Guys.

The same problem for Ubuntu 2.2 in 2006 and now in Ubuntu 14.04, my wired connection works but not my wireless.

I am lost. I tried the sticky with no luck yet.

I also tried some commands, nothing.

So, I attached my wireless info text, please review and help me on this.

Thanks in advance.

---

### Post by chili555 on 2016-04-15
From your wireless-info:> ##### lspci #############################

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 0461:4de7 Primax Electronics, Ltd webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################
We see no wireless card here at all. Is it an internal (PCI) card or an external (USB) card?

If it is internal, is it possible that it is not enabled in the computer's BIOS? If USB, was it inserted at the time you ran the script?

Please have a look in the BIOS, insert the USB wireless and then run and post:```
lspci -nnk
lsusb
```Thanks.

---

### Post by Yazan on 2016-04-15
We see no wireless card here at all. Is it an internal (PCI) card or an external (USB) card?

- Its internal.   In windows I just connect without any external USB or devices.

If it is internal, is it possible that it is not enabled in the computer's BIOS? If USB, was it inserted at the time you ran the script?

-It could be not enabled maybe? I'm not sure. The wireless f12 button on the keyboard stays red how many times I press it.


There you go:

```
losama@Osama-COMPAQ:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
	Subsystem: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310] [1002:9802]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: snd_hda_intel
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: piix4_smbus
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ohci-pci
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
	Kernel driver in use: pcieport
00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
	Kernel driver in use: pcieport
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ohci-pci
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
	Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: rtsx_pci
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:3577]
	Kernel driver in use: r8169
osama@Osama-COMPAQ:~$ lsusb
Bus 002 Device 002: ID 0461:4de7 Primax Electronics, Ltd webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Bucky Ball on 2016-04-15
I see nothing. Is it USB? Presume not. You might want to have a look in there and make sure the card is in properly.

---

### Post by Yazan on 2016-04-15
> **Bucky Ball said:**
> I see nothing. Is it USB? Presume not. You might want to have a look in there and make sure the card is in properly.

I'm not sure what you mean. it's just a normal laptop. Didn't use USB for internet before or anything.
Thanks

---

### Post by chili555 on 2016-04-15
Sorry. We see no wireless device at all.

---

### Post by Yazan on 2016-04-15
> **chili555 said:**
> Sorry. We see no wireless device at all.

OK then what? :s

In windows the wireless works fine...
Also on Ubuntu 2.2 I had the same problem, then I did something which I seriously have no idea what since it was long time ago and it worked? :S

Could formatting the computer had something to do with this??

What's the next step?

Thanks

---

### Post by Bucky Ball on 2016-04-15
It still works fine currently in your Windows install? If so, that is extremely weird it is not showing up in Ubuntu ... :-k

---

### Post by Hadaka on 2016-04-15
Hi, What is the exact model of compaq presario ?
Is wifi "enabled" checked ? click the up/down arrows to verify.
also boot into bios and and see if there is a "default" bios setting
if yes...set it to that. while in bios verify wifi is enabled in all the
places it should be. as a last resort, if you havent already created backups
of your files, i would suggest you do so and consider reloading Ubuntu as you
state the wireless functions correctly in windows.
good luck and keep us posted on your findings.
thanks.

---

### Post by Yazan on 2016-04-15
> **Hadaka said:**
> Hi, What is the exact model of compaq presario ?
Is wifi "enabled" checked ? click the up/down arrows to verify.
also boot into bios and and see if there is a "default" bios setting
if yes...set it to that. while in bios verify wifi is enabled in all the
places it should be. as a last resort, if you havent already created backups
of your files, i would suggest you do so and consider reloading Ubuntu as you
state the wireless functions correctly in windows.
good luck and keep us posted on your findings.
thanks.

Hey. 
It's Compaq 435.
What do you mean up/down arrows? 
I will try the BIOS option and post back.

Thanks

---

### Post by Yazan on 2016-04-15
> **Bucky Ball said:**
> It still works fine currently in your Windows install? If so, that is extremely weird it is not showing up in Ubuntu ... :-k

Yes it always did actually but recently I formatted the computer and installed fresh ubuntu.
Can formatting the computer have anything to do with it?  I think on Windows usually I need to install some kind of driver.

---

### Post by Yazan on 2016-04-15
> **Yazan said:**
> Hey. 
It's Compaq 435.
What do you mean up/down arrows? 
I will try the BIOS option and post back.

Thanks

Just tried setting the BIOS back to default. No luck.

I remember the solution back in Ubuntu 2.2 was so simple that it feels bad I cant remember the actual solution :S

---

### Post by Hadaka on 2016-04-15
Hi, by "up/down" arrows im referring to the connection type icon next to the envelope 
and speaker icon on the same level as the time. "up/down" is ethernet...and wifi has a fan looking
icon, like a radio signal transmitting outward.
Normally if..
```
lspci -n
#or
lsusb
```
does not show some kind of indication of a network card, that means it;s not there
or is not working. However you state your wifi card works fine in windows. 
Please open a terminal ctrl/alt/t and do..
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

```
You may get a "file not found" but do them anyway one at a time.
```
sudo apt-get update
sudo apt-get dist-upgrade #this does not upgrade to the next ubuntu version
sudo modprobe -rf b43
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
boot
any improvement ??

---

### Post by Yazan on 2016-04-15
Nope. Still the same after the boot.
```
osama@Osama-COMPAQ:~$ sudo ifconfig wlan0 down
[sudo] password for osama: 
wlan0: ERROR while getting interface flags: No such device
osama@Osama-COMPAQ:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
osama@Osama-COMPAQ:~$ sudo apt-get dist-upgrade #this does not upgrade to the next ubuntu version
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
osama@Osama-COMPAQ:~$ sudo modprobe -rf b43
osama@Osama-COMPAQ:~$ sudo modprobe -rf b43
osama@Osama-COMPAQ:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
osama@Osama-COMPAQ:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
osama@Osama-COMPAQ:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
osama@Osama-COMPAQ:~$ ^C
osama@Osama-COMPAQ:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
osama@Osama-COMPAQ:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
osama@Osama-COMPAQ:~$ sudo modprobe b43
osama@Osama-COMPAQ:~$ 

```
Please see attachement

---

### Post by praseodym on 2016-04-15
Maybe Windows deactivates the card while shutting down?! Try to boot the network before the OS in the BIOS settings, if possible

---

### Post by Yazan on 2016-04-15
> **praseodym said:**
> Maybe Windows deactivates the card while shutting down?! Try to boot the network before the OS in the BIOS settings, if possible


Now there is no Windows however. I formatted the computer.

---

### Post by Yazan on 2016-04-15
I tried Booting like you said but still no luck

---

### Post by Hadaka on 2016-04-15
There is no indication that a wifi card is present,
```
ERROR while getting interface flags: No such device
```
from any printout you have provided and now you state you no longer
have windows on the machine, so we have no way even if we asked for
windows printouts, which was going to be my last resort effort to try
and determine what if any type of wireless card you had, I regret that
I was unable to provide you with a solution, I have no further suggestions.
good luck to you.

---

### Post by Bucky Ball on 2016-04-15
> **Yazan said:**
> Now there is no Windows however. I formatted the computer.

In other words we now have no idea whether this card is functioning in Windows or at all. It is coincidental, but the wireless card could have simply died around the time of the reinstall. It happens.

---

