---
title: "cannot enable eth1 (wireless)"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by maxxum on 2007-07-12
I know there are so many threads on wireless not working, but even after searching I couldnt find something that would solve my problem. I have kubuntu 7.04 AMD x64 version and an AMD turion processor on my Compaq F558US notebook. I was able to configure the wireless with ndiswrapper (its a Dell broadcom device) using a howto on the forums. It worked well and I saw the wireless signal monitor and everything.

Once I rebooted, its all gone! Now I see eth0 as the wired connection and eth1 as a "disbled wireless connection". I cannot enable it even as administrator. I try manual configuration - it tries to get it started and get stuck. Its tough to be with linux in this windows world, but please help me keep up the fight! :)

Let me know whatever command's output you want me to post!

EDIT: I was able to solve the problem by blacklisting the default ubuntu driver (bcm43xx) and restarting the computer. It should have been blacklisted earlier, as I followed a howto, but whatever. I tried and it worked.

---

### Post by kevdog on 2007-07-12
Please post your 

/etc/network/interfaces 
/etc/iftab

files.  By default ndiswrapper refers to the new interface as wlan0, not the previous eth1 interface, so basically we have to change any reference of eth1 in these two files to wlan0.  

I hope you installed a 64 bit driver for your wireless card with ndiswrapper.  Since you elected to go with the 64 bit OS, you will need a 64 bit driver.

---

### Post by maxxum on 2007-07-12
interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iftab :

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1b:24:25:2b:64 arp 1
eth1 mac 00:1a:73:49:38:b4 arp 1

I just downloaded the exe from dell and it worked. It probably was 32 bit, but it worked.

---

### Post by maxxum on 2007-07-12
Also, on second thoughts, I have 64 bit XP Pro and 64 Bit Vista installed in the same notebook. Could I somehow use the driver that works in either of them?

---

### Post by kevdog on 2007-07-13
You need to change your iftab file -- change eth1 to wlan0

As far as drivers, the winxp 64 bit drivers would work - with ndiswrapper,  

Change your iftab first, and see if "miraculously" something works.  If not, you are going to have to hunt down the windows drivers.

---

### Post by GrouchoMarx on 2007-07-13
1) You said that at first it worked and that you saw the wireless signal monitor. Were you actually able to browse the internet on wireless (without wired) before you rebooted?

2) > Now I see eth0 as the wired connection and eth1 as a "disbled wireless connection". I cannot enable it even as administrator.

Where do you see this? Are you using Network Manager, or system > administration > network?

---

### Post by maxxum on 2007-07-13
I renamed it wot wlan0 and restarted. Although it is listed as wlan0 now, but I still cannot enable it.

---

### Post by maxxum on 2007-07-13
Groucho,
Yes I was able to browse the internet. And I see the status of the connection by clicking on the icon in the bottom right of the kde desktop. I have also tried to go into it through System Settings->Network.

I am inclined to uninstall the driver and use the one in my XP pro installation directory with ndiswrapper, if I can find it. Any ideas how to go about that...?

---

### Post by GrouchoMarx on 2007-07-13
First, I hope this isn't a silly question, but did you try right clicking on the icon in the bottom right corner? That let's you toggle the interfaces through Network Manager (bottom right icon), rather than through system > administration > network (which doesn't seem to work well if Network Manager is active).

I don't think that the driver is the problem, given that you were initially able to browse the web. However, if you want to install the windows drivers (they currently work better anyways), then first you need to locate the appropriate .inf driver file. You can find it either on your windows system, or on the [windows driver list for ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/").

To determine which driver to download from the list, in the terminal type "lspci -nn" to print out a list of PCI devices. Your wireless LAN controller should be somewhere near the bottom, most likely last:
> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
Use the PCI ID (in this example, 14e4:4320 rev 02) and the device name (BCM4306) to find the appropriate driver in the [windows driver list for ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/").

Once you have your .inf file, you can follow the instructions in [the Ubuntu community docs]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%2FDriver%29#head-ccd66d4fcaaab3a6e7a5c47162c1b7c6f52d41e5") on how to set up and install the ndiswrapper driver.

Also, here is a good [troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), with a primer on useful commands to assist in debugging.

---

### Post by maxxum on 2007-07-14
Yes,  the first thing I tried was to right click on the icon in the panel and it shows "No Wireless Networks Avaibable".
However after the last wake up from hibernation I saw that in the network settings the wlan0 is no longer disabled. It is now an "Enabled Wireless Network Device". Now that's a start.
I am not going to uninstall the driver and try installing new yet because maybe I can get this to work after a little tweaking.
However, how do I check which driver is installed?

When I try "Connect to other wireless network" and enter my wireless essid and WEP hex key, It shows the name of the network, that's it. When I do ifconfig, I see 
"No DHCPOFFERS received"
"No working leases in persistent database - sleeping."

I think something I did while installing, to make sure that the driver starts during reboot went wrong. I remember renaming wlan0 to eth1 (reading from some howto). However earlier in this tread, I renamed it back to wlan0.

EDIT: nevermind, after another restart, it is disabled again and I cannot enable it even in admin mode. So I guess I need to uninstall it and reinstall the driver and/or ndiswrapper.

---

### Post by maxxum on 2007-07-14
Thanks for the help guys. I was able to get it working again. Somehow the blacklist didnt have bcmwlxx driver (which it should have been). I put it in and restarted and it immediately saw all the networks!:guitar:

---

### Post by GrouchoMarx on 2007-07-14
To check which driver is installed: ```
sudo lshw -C network
```Then find your wireless interface on the list, and the driver should be listed under the subheading "configuration".

Based on your system, I suspect that your wireless card is the Broadcom BCM4318, in which case the PCI ID will be 14e4:4318 (rev 02). This card is well known, and many users seem to run into problems. If it turns out that you have this card, then I would just try the ndiswrapper + windows driver setup. [Here is a thread]("http://ubuntuforums.org/showthread.php?t=494168&highlight=broadcom+4318+amd+turion") in which someone with a very similar system (and the BCM4318 card) managed to get his wireless working by installing the windows drivers.

---

### Post by GrouchoMarx on 2007-07-14
Good work!

---

### Post by merlin666 on 2008-01-03
I am having an eth1 problem as it also shows as eth1:avah. When I open iftab there is no eth1:

# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.  See iftab(5).
#eth0 mac 00:03:25:15:5f:eb

How do I get rid of the eth1 problem?

---

