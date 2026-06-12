---
title: "Wireless works when booting from live CD but not when booting from HD"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by orestesm on 2007-06-26
I am having a weird problem where I can connect to my router and internet with no problems when I boot using the Live CD but after installing and booting from the HD I cannot connect to the router.  Running off the installed image, the machine sees the router (along with several others in homes around me) but it cannot connect.

This is an IBM T22 notebook running Feisty using a Cisco PCMCIA (Aironet 350) wireless card connecting to a Netgear router.  WEP is in use but it does work off the live CD, not off the HD.

---

### Post by arvevans on 2007-06-26
You didn't say which window manager you were running, so I will assume that it is gnome and make my comments relative to that.

In the Live CD version, go to:
[INDENT]System - Administration - Network  and look at which ethrenet port is active and how it is configured.

Then reboot to the installed version and set up your Network options the same way.[/INDENT]

It is possible (probable...?) that you don't have your DNS server data entered and thus may be able to connect to the Internet via raw IP addresses but not able to use textual URL's.
Open up a terminal screen (go to Applications - Accessories - Terminal) and enter:

[INDENT]"ifconfig" then hit ENTER

If your system is getting an IP address via DHCP from the WiFi hub/server you should see an IP address and some data transfer information.

If you have an IP address, then in the terminal screen enter:
[INDENT]"ping -c4 72.14.207.99" [/INDENT] 

Check the Ping Response return to see if you actually have raw IP connectivity (0% packet loss)
If this works, then in the terminal screen try:
[INDENT]"ping -c4 ubuntu.com" [/INDENT]
If you cannot get a successful ping using the URL but can using a raw IP number, then your DNS setting  is at fault.[/INDENT]
_._

---

### Post by t4thfavor on 2007-06-26
I know its not very user friendly, but I use the command line iwconfig when working with wireless for this reason. I am not sure about the 350 cards, but I have a CB21AG(Atheros) and i use this script.

#!/bin/bash
sudo iwconfig ath0 essid "SomeSSID" key SOMEKEY
sudo dhclient ath0

Works like a charm.

I have always had problems with cloked SSID's and web under network-manager.

---

### Post by orestesm on 2007-06-26
Network settings on LiveCD show dashes ('-') next to wifi0 and eth1.  Hitting properties on these shows the "Enable roaming mode" check box checked and the rest of the fields grayed out.  The "Wired connection" item is checked but I assume this does not come into play in wireless.

Settings under installed image are the same for each tab except for hostname which is not "ubuntu" on the installed image (as expected).  DNS is set the same in both (set to the router IP address).

I also tried the commands suggested by t4thfavor and got: ath0: No such device.  I assumed that it was a typo and used "eth1" instead of ath0.  Then the first command worked but the dhclient command failed and returned:
No DHCP offers received.  No working leases in persistent database - sleeping

And still not network connection under installed image.

---

### Post by orestesm on 2007-06-28
Any other suggestions?  Anyone?  I guess I need to go back to Windows XP???

---

### Post by unisol on 2007-06-28
i dont have an answer for you right now as i am having some problems. but dont give up. stick with i,t you will be glad you did.

---

### Post by Keen101 on 2007-06-28
I had a similar problem awhile back. I asked my friend Joey Stanford about it, who works for launchpad. He told me that the roaming feature has a bug and to forget that it exists.  Now I did a little experiment, and for me roaming mode works only when unistalling or removing network manager from the sessions properties.


So, for this reason I never use network manager, because it is a pain. Instead I just use the network admin.


So, try removing network manager and see if that helps.

p.s.: if this does not work, don't give up! It must be a really simple problem. If that does not fix it, I am still willing to help!

-Keen101

---

### Post by orestesm on 2007-06-28
How do I go about removing network manager?

---

### Post by Keen101 on 2007-06-28
we'll the easiest way is not to actually remove it, but to disable it on startup. To do that go to preferences >sessions and there will be network manager, and you can uncheck it. 

But, if you do wan't to remove it, then just open synaptic package manager and search for "network manager" then right click on it and set it to remove, and then click the green apply button.

synaptic is the easiest and most comprehensive way in my opinion to add or remove packages.


-keen101

---

### Post by Keen101 on 2007-06-28
We'll, I just tried "roaming mode" on mine, and it did not work right. The network applet which i put on my desktop showed it green and available, but it did not work. So, apparently "roaming mode" still has a bug in it. 


So, just use network admin from >system>Administration>network and set your Essid manually and DHCP or whatever you use. Will try to respond later, but have to go now.


-keen101

---

### Post by orestesm on 2007-06-29
OK this actually helped a bit.  Thanks.

I did as you said and disabled network manager then entered all the config info into the Network admin UI.  After this the thing actually connected and I was able to browse the internet!  Yay!  Then I created a new user and switched over to that account to see if that would work and it did!

Then I tried rebooting to see if it stuck and it did not.  Boo.  After rebooting I could not get connected for several hours (several attempts at manual config, re-enabling/disabling network manager, reboots, cursing, praying, etc.) until after one of the reboots it randomly started working.

I can honestly say that this is the most frustrating computing experience I have ever had.  And I once configured Win98 as an internet gateway using MS internet connection sharing!

Anyone have a way for me to get this to be repeatable?

---

### Post by jppaynesr on 2007-06-29
Dont give up, it can be fixed.

I had wireless problems also until I took some advice here and installed this package,
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Download the package
Use System/Admin/Synaptic to uninstall network manager
Install WICD
It makes moving between wireless networks seamless, automatically connects on startup, no problems so far.

After you get that working, you might also enjoy EtherApe and Avahi zeroconf browser, both available from Applications/Add/Remove

Jon Payne
Atlanta GA

---

### Post by Keen101 on 2007-07-01
we'll sorry it has not been "stable", or whatever you would call it. But, at least it is a start. Perhaps there is a bug, and the best way would be to do updates whenever it DOES connect. This usually fixes most bugs. Also, which I am sure you have done is to make sure there is no interference. (or any 2 routers with the same essid that could be interfering with each other)

I'm sure it is your router, and it is very close. Otherwise I would suggest making sure it is not a weak connection. 


sorry, I can't help more, but like i said at least it is a start and it should get better in the future. :)

cheers
-Andrew
-Ken101

---

### Post by kevdog on 2007-07-01
Lets try to figure out what type of hardware you are dealing with first.  Please post output of following

lspci
lspci -n
lshw -C network

Thanks

---

### Post by orestesm on 2007-07-01
It seems that I get it to work every time as long as I completely shut down before powering up again.  Reboot via "Restart" results in no connection.  I have not tried WICD as suggested by JP yet.

lspci returns:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
00:04.0 PCI bridge: Texas Instruments PCI2032 PCI Docking Bridge
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
08:01.0 IDE interface: Silicon Image, Inc. PCI0648 (rev 01)
08:02.0 CardBus bridge: Texas Instruments PCI1420
08:02.1 CardBus bridge: Texas Instruments PCI1420

lspci -n returns:
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:02.0 0607: 104c:ac1b (rev 03)
00:02.1 0607: 104c:ac1b (rev 03)
00:03.0 0200: 8086:1229 (rev 0c)
00:03.1 0700: 11c1:045c (rev 01)
00:04.0 0604: 104c:ac22
00:05.0 0401: 1013:6003 (rev 01)
00:07.0 0680: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 03)
01:00.0 0300: 5333:8c12 (rev 13)
08:01.0 0101: 1095:0648 (rev 01)
08:02.0 0607: 104c:ac51
08:02.1 0607: 104c:ac51

lshw -C network returns:
  *-network
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 1
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 0c
       serial: <deleted>
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:07:85:92:ec:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.22 multicast=yes wireless=IEEE 802.11-DS

---

### Post by nc_jed on 2007-07-02
orestesm,
I just had the exact same issue (albeit with xubuntu and an Airlink 101 card PCMCIA card) and the script from t4thfavor worked for me (with one minor change).

As t4thfavor writes, his wireless port is ath0.  mine is ra0 (from ralink chipset usage).  Check yours with ifconfig, you may need to do a minor edit on that point.

Anyway, props to t4thfavor for the script.

Jed.

---

