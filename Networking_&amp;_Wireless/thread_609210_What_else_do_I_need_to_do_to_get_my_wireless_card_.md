---
title: "What else do I need to do to get my wireless card working?"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by EduMan on 2007-11-10
This is the current data on my wireless card and wireless network  in Ubuntu 7.10: 


warden@DeskMatrix:~$ 

warden@DeskMatrix:~$ cd wg311v3

warden@DeskMatrix:~/wg311v3$ sudo ndiswrapper -i wg311v3.inf

driver wg311v3 is already installed

warden@DeskMatrix:~/wg311v3$ 



warden@DeskMatrix:~$ sudo ndiswrapper -m

[sudo] password for warden:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...



warden@DeskMatrix:~$ ndiswrapper -v

utils version: 1.9

driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

version:        1.45

vermagic:       2.6.22-14-generic SMP mod_unload 586 



warden@DeskMatrix:~$ sudo apt-get install wpasupplicant

Reading package lists... Done

Building dependency tree       

Reading state information... Done

wpasupplicant is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


warden@DeskMatrix:~$ lspci –v

02:0e.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

        Subsystem: Netgear WG311v3 802.11g Wireless PCI Adapter

        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10

        Memory at feae0000 (32-bit, non-prefetchable) [size=64K]

        Memory at fead0000 (32-bit, non-prefetchable) [size=64K]

        Capabilities: <access denied>



warden@DeskMatrix:~$ sudo apt-get install network-manager-gnome

[sudo] password for warden:

Reading package lists... Done

Building dependency tree       

Reading state information... Done

network-manager-gnome is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

warden@DeskMatrix:~$ 



At this time the Network Settings shows:

1. A “Wired Connection” -  with Roaming Mode Enabled

2. A “Modem Connection” – This network interface is not configured


My wireless card does not show yet in the settings.  What is the next step I need to take to configure the wireless card? 

Thanks!

Eduard

---

### Post by Bob69 on 2007-11-10
I am not an expert in Linux but have installed the same card in an old pc with success.

After where it says: adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper add the following command:

modprobe ndiswrapper

Then to see if wlan0 is recognized type:  iwconfig

This should list wlan0 and the current settings.

I had to manually configure wlan0 using the iwconfig commands.

Example:  iwconfig wlan0 essid "linksys" (this would be your essid)
                iwconfig wlan0 channl 6
                iwconfig wlan0 mod managed 

you can type iwconfig --help to see all the options you have.

Hopefully someone with more knowledge will respond to your help.

Bob69

---

### Post by EduMan on 2007-11-10
Thanks. I think I need a little more detailed explanation before I understand what I need to do.

---

### Post by kevdog on 2007-11-11
Can you post

ndiswrapper -l

Are you trying to connect via WPA or unencrypted first of all prior to moving towards WPA to see if everyting works prior to adding network encryption?

---

### Post by EduMan on 2007-11-11
Hi!

Thanks for helping. Here is the command output:

warden@DeskMatrix:~$ ndiswrapper -l

wg311v3 : invalid driver!


So, the driver is not working, right? What do I do now? I have to tell you more about my computers and wireless hardware so that you will understand where I am now: 

I bought my wireless hardware in July 2007: 1. A Wireless G Router (WGR 614v7), and 2. Two Wireless WG 311v3 PCI adapters for the two computers I have. I configured the router with WPA-PSK security, and I used the WG 311v3 version 1.1 (March 14, 2006) driver to configure the adapters. 

About a month ago I upgraded one computer (an OptiPlex 755) to Vista Business (64 bit), and used the latest version of the WG 311v3 PCI adapter, version 3.0, released on October 18, 2007, to setup the adapter. I had not trouble with the driver, though Vista is 64 bit and the driver is 32 bit (I think!). I use this computer for work. 

I reinstalled Windows XP home on a new drive which I installed in the other computer (a vpr Matrix) on November 1, 2007, and I also upgraded the driver for the WG 311v3 PCI adapter on this computer to the latest version of the firmware, version 3.0. The wireless connection works well.

On November 4, 2007 I installed Ubuntu 7.10 on the same Matrix computer in dual boot, and I tried to find the WG 311v3 INF and SYS files for the latest version of the firmware, version 3.0. All I found was a zip file for version 1.0, and I used these INF and SYS files for Ubuntu. 

So, at this time I am trying to use two WG 311v3 drivers for the same WG 311v3 adapter in the vpr Matrix computer. I use the WG 311v3 version 3.0 driver for Windows XP, and I have been trying to install the WG 311v3 version 1.0 driver for Ubuntu 7.10. It seems that it did not work.

Now, how do I get out of this mess and finish setting up my Ubuntu 7.10 wireless connection? 

Sorry for this long message. I though you might need to know all this in order to be able to help me. 

Eduard

---

