---
title: "Which Network Card Wireless"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by KevinGW on 2006-11-05
I have an old P3 that I am going to install Ubuntu on (likely the recent server version). On setup it recognized my d-Link wireless card but it does not seem to be working. Is there any thing I can do to check the status of the card or get it to work?

Alternatively, is there a sure fire wireless card that will work with Ubuntu?

Thanks

---

### Post by FrodoB on 2006-11-05
Kevin;

Can you be more specific as to what type of adapter you need(PC CARD, PCMCIA, USB, PCI, etc.)?

If you open a terminal you can run several commands to get information:

lspci
lsusb

iwconfig
ifconfig
netstat -rn

What type of device do you have now?

FrodoB

---

### Post by .t. on 2006-11-05
Yeah, post iwconfig especially.

---

### Post by capoyeti on 2006-11-05
hope you don't mind me jumping on this train..

Had wireless card working in Edgy (WPA through network manager), but after upgrade of kernel on Wed, my Atheros wireless card isn't seen anymore
```

chad@beastly:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

lspci does see it tho'

```
....
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
....
```

the upgrade mentioned above broke X as well, but recompiled with latest Nvidia drivers to get that working...

anything specific to check why iwconfig (and most everthing else) e.g. 
```
chad@beastly:~$ dmesg |grep ath
chad@beastly:~$ 

```

lets me think my wifi card has gone walkabout?

Also disabled everything except auto lo and iface lo in /etc/network/interfaces

```
chad@beastly:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#iface eth0 inet static
#address 10.0.0.7
#netmask 255.0.0.0
#auto eth1
#iface eth1 inet dhcp
#auto eth2
#iface eth2 inet dhcp
#auto wlan0
#iface wlan0 inet dhcp
#auto eth0

```

Any suggestions?

---

### Post by FrodoB on 2006-11-05
Can you run dmesg and see if you can find where the atheros card starts and see if it loaded firmware correctly, etc. Maybe the firmware is not working with your card?

---

### Post by KevinGW on 2006-11-05
Sorry I was not exact.  I am looking for a PCI network card, but would consider a USB. Basically, looking for whatever is the easiest and most reliable.

Kevin

---

### Post by FrodoB on 2006-11-06
For a PCI card I would find something with an Atheros chipset:

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

This likely will just work in Edgy, there are positive posts for Dapper out there at any rate.

For USB I would look for something that has either a Zydas or Ralink chipset, but you will likely have to compile the drivers.  A good place to look at Linux compatibility is:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

Don't buy anything that you can't take back unless it is extremely cheap.

I have a Zydas USB device that I bought at Wal-Mart for about $40, it is a Belkin F5D7050 ver 4000, it uses the driver from [http://zd1211.ath.cx/](http://zd1211.ath.cx/).

The F5D7050 ver 3000 is a Ralink chipset and uses the RT73 driver from Ralink's web site.

An Atheros PCI card is likely to work easier, but beware of Atheros USB devices, they do not work with the madwifi driver.

---

### Post by Sinisterff on 2006-11-06
I am also looking for a nice usb network adapter to buy, and the F5D7050 sounds nice, this may be a noob question but... if i buy it tomorrow do you think i will get one with version 3xxxx or 4xxxx? or is there a way of to know the version by looking at the box?

---

### Post by capoyeti on 2006-11-06
FrodoB - Thanks for the 'reminder' to look at the MadWiFi site.

The How To link especially helped and Edgy had no problems seeing the card after following the instructions on this page. Network-Manager saw it immediately and I no longer have a cable running through the house anymore.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by FrodoB on 2006-11-07
As for the Belkin F5D7050, I should just withdraw my comments about it being good for Ubuntu.  They do both work as you would expect in Slackware and Freespire, but on Ubuntu Edgy, at least, they both seem to be problematic. I will do some further investigation and report back my findings.

I can state that they can be make to work in Edgy by using a startup script that is run from the command line, but they do not seem to want to work with the GUI Networking tool, which probably makes them undesirable to most users.

Sorry for the confusion.

---

### Post by FrodoB on 2006-11-07
Ok, here is the situation that I have found so far on Edgy.  The F5D7050 ver 3000 and ver 4000 work, but not through the GUI tool. You can use the GUI tool to setup the correct entries in /etc/network/interfaces and then you have to use a command line to bring them up.

The F5D7050 ver 3000 requires that you issue a command in a terminal to bring the interface(rausb0) up and then you can use ifup like this:

$ sudo ifconfig rausb0 up
$ sudo ifup rausb0

Then it should come up if you had a good install. I will also note that to get the RT73 driver to see the device you have to add a line to rtmp_def.h with the devices USB ID like so before you compile it.

 {USB_DEVICE(0x050d,0x705a)}, /* Ralink */      \

in the USB Devices section at the end of the file.


The F5D7050 ver 4000 (wlan0) does not require the ifconfig wlan0 up:

# sudo ifup wlan0

Here are my /etc/network/interfaces entries for the two devices (set your WEP keys to suit):

iface wlan0 inet dhcp
wireless-essid My ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

iface rausb0 inet dhcp
wireless-essid My ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

As I said, you should be able to create those entries using the GUI tool, it just will not bring the interface up, you will have to do that from a command line or put it in the end of you startup scripts.

So, these may or may not be what you are looking for.

Good Luck,

FrodoB

---

### Post by FrodoB on 2006-11-07
I should also give the scripts that I use to manually start these devices. 

Here is the F5D7050 ver 3000:

#!/bin/sh
/sbin/ifconfig rausb0 up
/sbin/iwconfig rausb0 mode "Managed"
/sbin/iwconfig rausb0 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/sbin/iwconfig rausb0 essid "Your ESSID"
/sbin/dhclient rausb0

Here is the F5D7050 ver 4000:

#!/bin/sh
/sbin/iwconfig wlan0 mode "Managed"
/sbin/iwconfig rausb0 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/sbin/iwconfig rausb0 essid "Your ESSID"
/sbin/dhclient wlan0

Set your WEP keys to suit.

---

### Post by FrodoB on 2006-11-07
asalford made a nice post on LinuxQuestions regarding the ver 3000 device, but he does not seem to have overcome the issues that I described earlier:

[http://www.linuxquestions.org/questions/showthread.php?t=449166](http://www.linuxquestions.org/questions/showthread.php?t=449166)

---

### Post by mikkelwe on 2006-11-22
> **capoyeti said:**
> 
Had wireless card working in Edgy (WPA through network manager), but after upgrade of kernel on Wed, my Atheros wireless card isn't seen anymore

Make sure you have installed the linux-restricted-modules *for your new kernel*. sudo apt-get install linux-restricted-modules-$(uname -r) should do it.
I don't know why it wouldn't be updated as well but it sounds like the atheros modules are missing and they are in that package. If you know it's already installed make sure the ath* modules are loaded in /etc/modules.

---

### Post by FrodoB on 2006-11-22
That is it. You installed from the Alternative CD and have no restricted modules?

Atheros normally works out of the box on Dapper and Edgy.

---

### Post by Sinisterff on 2006-12-06
Nice scripts, but, is there a way to have an static IP with this method?, I tried with the GUI, but it didn't work, I want to use it for Port Forwarding. Thanks for your answers

---

### Post by FrodoB on 2006-12-06
This document shows an example of what a static setup looks like in /etc/network/interfaces. Normally the best way to setup these values would be to use the Networking tool:

System -> Administration -> Networking

Fill out the necessary information.

---

