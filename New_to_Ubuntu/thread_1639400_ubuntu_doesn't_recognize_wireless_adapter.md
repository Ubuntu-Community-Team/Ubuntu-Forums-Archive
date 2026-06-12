---
title: "ubuntu doesn't recognize wireless adapter"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by vonfreeware on 2010-12-06
I installed ubuntu 10.10 about 2 weeks ago (first time using linux), and I am still trying to connect to the internet via my D-link wireless adapter.  I installed ndiswrapper from the ubuntu software center and then installed the windows driver from my D-link CD-ROM.

Ndiswrapper says the drivers are installed, and that hardware is 'present'.  However, no wireless networks show up under the network manager.  I have absolutely no clue as to how to proceed.  Has anybody else had a similar problem?  Or does anybody have any tips?

---

### Post by spikoley on 2010-12-06
Post the results of the following command.  It will show the details of your wireless card.

```
lspci
```

---

### Post by vonfreeware on 2010-12-06
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller

---

### Post by tad1073 on 2010-12-06
actually
```
lshw -C network
```
will narrow it down to just your wireless adapter

---

### Post by vonfreeware on 2010-12-06
don't know if it worked but here it is


  *-network               
       description: Ethernet interface
       product: 82567V-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:25:11:3f:8b:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.8-5 latency=0 multicast=yes
       resources: irq:43 memory:fe9e0000-fe9fffff memory:fe9df000-fe9dffff ioport:cc00(size=32)

---

### Post by TBABill on 2010-12-06
Must be USB? The above is your wired internet. Output of ```
lsusb
``` and sorry to have to keep asking for info to know what chipset your wireless has.

---

### Post by vonfreeware on 2010-12-06
ya its usb sorry should have said

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0461:4d64 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 002 Device 002: ID 0bda:0182 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by uRock on 2010-12-06
**sudo apt-get install linux-firmware-nonfree** in a terminal should fix the problem. You can also install the linux-firmware-nonfree package in the Ubuntu Software Center.

---

### Post by cariboo on 2010-12-06
I think I have the same device, I get the same output from lsusb. If you are running a 64-bit version, you'll need to install a 32-bit version, as none of the 64-bit windows drivers worked.

what is the exact message you get when trying to connect? If it says unclaimed, ten you may have to manually enter an essid in order to connect the first time.

Try selecting connect to a hidden wireless network and enter the essid of your wireless network.

---

### Post by vonfreeware on 2010-12-06
Still no wireless networks showing up in network manager.

---

### Post by vonfreeware on 2010-12-06
I have the vista 32 driver installed.  I haven't been able to try to connect because I can't select any wireless networks.  Am I just looking in the wrong place?

---

### Post by uRock on 2010-12-06
Is the SSID on your router enabled?

---

### Post by vonfreeware on 2010-12-06
I don't really know what that means lol (I don't have any experience setting up wireless networks) but Ill see if I can find out.

If it helps, before installing ubuntu I was using my adapter on windows with the same driver and had no problems connecting.  Other PCs in my house are currently connected to it as well.

---

### Post by zipteye on 2010-12-06
You have to use the Windows XP (or 2000) drivers for i386.
Look for those on your drivers disc.
Uninstall the Vista drivers.
 
I believe the command to uninstall is:
sudo ndiswrapper -e "yourfile".inf
 
^ SOMEONE CORRCT ME if this is wrong please.
 
Then sudo gedit /etc/modules
modules should show: lp
add ndiswrapper on the next line hit reurn, then save the modules file.
 
Reboot.

---

### Post by vonfreeware on 2010-12-06
Uninstalled the vista driver and installed the XP one (couldn't get those terminal commands to work but System>admin>windows wireless drivers does the job).  Still no luck tho.

Device is D-link WUA-2340 btw.

---

### Post by Finnius on 2010-12-06
Gday,

Why dont you try connecting to the network manually if you have not already tried...

To get the <interface> for the wireless usb adapter:
```
sudo iwconfig
```Then tell it to connect to the router:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid 'yournetworkname'
sudo iwconfig <interface> key 123yournetkey123
sudo ifconfig <interface> up
sudo dhclient <interface> 

```That should get your router to give you an IP address on the network.
I have found network manager to be buggy and not let me connect to networks that i know it should be able to connect to...

If it doesn't work, post what the output is.

Seeya

---

### Post by vonfreeware on 2010-12-06
output:


lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Finnius on 2010-12-06
Hello again,

Follow this solved thread - **How to set up a D-Link WUA-2340 USB Wireless Adapter**   
[http://ubuntuforums.org/showthread.php?t=861855](http://ubuntuforums.org/showthread.php?t=861855)

The thread documents how to use ndiswrapper to get your exact adapter working...

cya

---

### Post by vonfreeware on 2010-12-07
read the thread...I already have ndiswrapper and the exact driver they mention installed, that is netA5GUA.inf.  And that thread didnt seem to be solved - I read through and the guy never gave confirmation that it had worked.

One thing that was baffling:

When I tried sudo ndiswrapper -l as the thread recommended to see if the driver was actually installed, the terminal stopped working entirely every time:-?
All the other ndiswrapper options like -v seemed to work fine though.

---

### Post by vonfreeware on 2010-12-07
Managed to get it to work (just had to uninstall/reboot/reinstall...ive found ndiswrapper is kind of buggy)

b@b-Aspire-M5800-M3800:~$ sudo ndiswrapper -l
[sudo] password for b: 
neta5agu : driver installed
	device (07D1:3A08) present

weird.  Ill see if I can connect manually without using network manager.

---

### Post by vonfreeware on 2010-12-07
no luck again.

I found this guide for my device online

[http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Setup+a+DLINK+WUA-2340+USB+Wireless+Adapter+in+Ubuntu+Hardy/b8mxw](http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Setup+a+DLINK+WUA-2340+USB+Wireless+Adapter+in+Ubuntu+Hardy/b8mxw)

It seems I have everything installed and working, (according **sudo ndiswrapper -l**).  The problem is I can't follow the next step because the guide is for hardy and im using meerkat.  Could somebody maybe 'translate' the following steps into meerkat speak for me?

[I]sudo ndiswrapper -l

You should see that the driver is installed and the device is present.  [**ive completed this step**]

Now in a perfect world, you would be done now. However network-manager in hardy will not display any wireless networks for you to connect to. Rest assured your wireless adapter is installed and working, the problem is with network-manager.

Next Step

* Open System->Administration->Network
* You should see your wireless connection in the list, click the Unlock button to make changes.
* Select your wireless connection and hit the properties button.
* Deselect 'Roaming'
* Select your wireless network from the list and enter in your WPA/WEP information for the card.
* Click ok, and now you have a working wireless connection. Congrats!
[I]

So basically could someone tell me how to do that^ in meerkat?

---

### Post by vonfreeware on 2010-12-07
> Gday,

Why dont you try connecting to the network manually if you have not already tried...

To get the <interface> for the wireless usb adapter:
Code:
sudo iwconfig
Then tell it to connect to the router:
Code:
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid 'yournetworkname'
sudo iwconfig <interface> key 123yournetkey123
sudo ifconfig <interface> up
sudo dhclient <interface>
That should get your router to give you an IP address on the network.
I have found network manager to be buggy and not let me connect to networks that i know it should be able to connect to...

If it doesn't work, post what the output is.

Seeya

This the output

b@b-Aspire-M5800-M3800:~/Documents$ sudo ifconfig lo down
b@b-Aspire-M5800-M3800:~/Documents$ sudo dhclient -r lo
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
b@b-Aspire-M5800-M3800:~/Documents$ sudo iwconfig lo essid [my network]
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device lo ; Operation not supported.
b@b-Aspire-M5800-M3800:~/Documents$ sudo iwconfig lo essid [my network]

---

### Post by vonfreeware on 2010-12-07
anyone?

---

### Post by zipteye on 2010-12-07
> **vonfreeware said:**
> Uninstalled the vista driver and installed the XP one (couldn't get those terminal commands to work but System>admin>windows wireless drivers does the job). Still no luck tho.
 
Device is D-link WUA-2340 btw.
 
Can you open the terminal and type:
cat /etc/modules
 
What is the output?

---

### Post by vonfreeware on 2010-12-07
no such file or directory

---

### Post by vonfreeware on 2010-12-08
maybe its time to give up...doesn't seem like anyone knows how to fix the problem and I'm getting nowhere.  Anybody know of a usb wireless adapter that works out of the box on maverick?

---

### Post by albert s on 2010-12-08
I dont know, but Im on 10.04 and for the past 3 releases Ive got an 'edimax' that has always worked plug and play,
EW-7318USg

---

