---
title: "Networking Linksys Wireless"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by mtairhead on 2007-01-15
Hey all,

I have a Linksys wireless-g (Model wpc54g version 3) PC card that I've been attempting to setup for some time. When I insert the card, Ubuntu recognizes it (Or, at least a "wireless connection" option appears in the networking dialog box) but I don't know what to do to actually connect the laptop to my wireless network. 

When I click "properties" to configure the wireless connection, I am asked for the ESSID and the WEP information.. To keep life uncomplicated, for the duration of the wireless installation, I disabled all security on my WAP... Do I just leave the WEP information blank, then?

At any rate, something must not be working correctly, because when I click "activate" the laptop putzes around thinking much longer than it does when I "activate" the wired network, and Network Manager tells me I'm disconnected.

What am I doing wrong?

~Andrew

---

### Post by Metaljaz on 2007-01-15
try these steps:

    * download the appropriate driver for your card -> Linksys WPC54G v3
    * from the download extract the driver file (bcmwl5.sys) and inf file (LSBCMNDS.inf)
    * fire up the Synaptic Package Manager and install wpasupplicant & ndiswrapper
    * open a shell and change directory to the location the driver and inf file were extracted to
    * install the driver: sudo ndiswrapper -i ./LSBCMNDS.inf
    * check that the driver was installed correctly: ndiswrapper -l   if it was installed correctly it should output “driver present, hardware present”
    * write the module configuration file: sudo ndiswrapper -m
    * load the module: sudo modprobe ndiswrapper
    * add ndiswrapper to /etc/modules so the kernel module is loaded at boot time

keep us posted
good luck

---

### Post by Metaljaz on 2007-01-15
Check here for driver if you don't have it:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Try leaving the wpa supplicant out of the above thread for now. just get ndiswrapper.
You also did not say what version of Ubuntu you were using.

---

### Post by mtairhead on 2007-01-15
[php]
andrew@aj-laptop-01:~$ ndiswrapper -l
Installed ndis drivers:
lsbcmnds                driver present
[/PHP]

It doesn't say "hardware present"... Does it matter?

~Andrew

---

### Post by Metaljaz on 2007-01-15
it should say hardware present too.
try typing in a terminal window:
lshw
look under network and see what chipset is listed for your card. You may
have the wrong drivers for the card you are using.
You will see product "which is the name of your card"
and vendor "which is the chipset"
Once you find the chipset post back if you can't find the drivers
or try:
lspci
look at the ethernet controller line for the nic and you should see helpful info as well.

---

### Post by mtairhead on 2007-01-15
Response to the command lshw...
[PHP]
     *-network DISABLED
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@03:00.0
          logical name: eth1
          version: 02
          serial: 00:13:10:67:da:1b
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:f4000000-f4001fff irq:11
[/PHP]

Obviously, the network is listed as "disabled" right now - I enable it, but it doesn't seem to make a difference. 

Are you telling me that I'm looking for a driver for the "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller" card with a chipset of "Broadcom Corporation"??

So I'm not using the driver I downloaded from Linksys in corporation with ndiswrapper?

Also: I apoligize - I failed to state that I am using Ubuntu Version 6.06.

Thanks for everything,

~Andrew

---

### Post by Metaljaz on 2007-01-16
This thread should get you up a running. Any problems post back.

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by Metaljaz on 2007-01-16
Are you telling me that I'm looking for a driver for the "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller" card with a chipset of "Broadcom Corporation"??

yes is the answer to the above question.

Read through the below thread. Try the thread that seems easiest to you. You may have to try both.
Any drivers previously installed will have to be blacklisted or deleted.

[http://www.ubuntuforums.org/showthread.php?t=117001](http://www.ubuntuforums.org/showthread.php?t=117001)

---

### Post by mtairhead on 2007-01-18
Ok! I was able to connect to the Internet via my WAP this morning! You are my hero, Metaljaz.

Currently, I'm using this command in the terminal to connect:
[PHP]
sudo iwconfig wlan0 essid "your network name"[/PHP]

I'm doing this because my Network Manager still doesn't list available networks. There's a red  X on the network icon in the (I want to call it a) system tray, even now when I'm connected.

I've installed KNetworkManager, which succesfully lists the networks available, but when I tell it to connect to one, it always fails at the "configuring device" state. It sits at 28% (The "configuring device" stage) for several seconds, and then finally reports that it's "disconnected."

Is there a setting I'm missing? Right now everything works, just not as it was intended.

~Andrew

---

### Post by Metaljaz on 2007-01-18
which drivers did you end up using? I guess you are using k desktop instead of gnome.

---

### Post by mtairhead on 2007-01-21
I promise, I know what I'm doing with Windows-based PCs.. I'm no idiot, but I don't know how to give you the information your asking for...

I used the driver provided on the CD-Rom, like the forum post you linked to told me to (bcwml5.inf file, I believe).

: / It really is ok that I have to type in that command, to enter a wireless network... Just weird. :)

Really, thanks for all the help you've provided. You've gone far beyond what I would have had patience for.

Thanks,

~Andrew

---

### Post by mtairhead on 2007-01-21
Oh, and I think I'm using Gnome. At least there's an "About GNOME" option in the "System" menu..

~Andrew

---

### Post by Metaljaz on 2007-01-21
ok so you are now able to get online?

---

### Post by mtairhead on 2007-01-24
Yea, I can get online, I just can't use the network manager to connect to a WAP. I have to enter the command I previously posted into the terminal, with the SSID.

---

