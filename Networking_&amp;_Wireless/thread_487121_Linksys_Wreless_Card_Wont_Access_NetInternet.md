---
title: "Linksys Wreless Card Wont Access Net/Internet"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2007-06-28
I installed a Linksys Wireless WMP55G card into a 6.10 machine.  It was recognized and configured, but I cannot see the network or access the Internet.  I ran ifconfig and iwconfig, and the outcome is below:

```

steve@Steves-Linux-Box:~$ ifconfig

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)


steve@Steves-Linux-Box:~$ iwconfig

lo no wireless extensions.eth1
IEEE 802.11b/g ESSID:"" Nickname:"Broadcom 4306"
Mode:Managed Access Point: Invalid
RTS thr: off Fragment thr: off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0eth0
no wireless extensions.sit0
no wireless extensions.

```

Help!

---

### Post by kevdog on 2007-06-28
Can you post the following:
lspci
lspci -n

---

### Post by sjrlaw on 2007-06-28
Kevdog:

Thanks for responding.  The data yielded by those two commands was as follows:

```
steve@Steves-Linux-Box:~$ lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1(rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


steve@Steves-Linux-Box:~$ lspci -n

00:00.0 0600: 8086:2570 (rev 02)
00:02.0 0300: 8086:2572 (rev 02)
00:1d.0 0c03: 8086:24d2 (rev 02)
00:1d.1 0c03: 8086:24d4 (rev 02)
00:1d.2 0c03: 8086:24d7 (rev 02)
00:1d.3 0c03: 8086:24de (rev 02)
00:1d.7 0c03: 8086:24dd (rev 02)
00:1e.0 0604: 8086:244e (rev c2)
00:1f.0 0601: 8086:24d0 (rev 02)
00:1f.1 0101: 8086:24db (rev 02)
00:1f.2 0101: 8086:24d1 (rev 02)
00:1f.3 0c05: 8086:24d3 (rev 02)
00:1f.5 0401: 8086:24d5 (rev 02)
01:01.0 0280: 14e4:4320 (rev 03)
01:08.0 0200: 8086:1050 (rev 01)


steve@Steves-Linux-Box:~$ 


```

---

### Post by kevdog on 2007-06-29
Just curious, I cant find your card WMP55G on the linksys US website.  I see WMP55AG. Well anyway, I dont know if it will matter.

Ok you've got two choices - 
bcm43xx-cutter method -- much easier installation.  Max transfer speed 11Mb/sec

ndiswrapper
A lot more difficult installation but Max transfer speed 54 Mb/sec

With ndiswrapper you will need a copy of the windows drivers.  (This card isnt officially tested or listed on the ndiswrapper website, so if you can make it work, we can post a success message there also!)

What do you want to do -- both should work!

---

### Post by sjrlaw on 2007-06-29
Oops.  My bad!  WMP54G!!

This card was listed on a compatibility chart as working with Ubuntu having the drivers, so I thought I didn't have to use the ndiswrapper.  Also, when I went into System > Administration > Networking, I saw a "Wireless Connection" entry under the Connections tab.  I understood that to mean that I had a working driver already installed and simply needed to activate the card. I selected the entry and clicked on the "Properties" button, clicked "Enable this connection" and filled in the appropriate information (SSID, network name, passcode, and connection settings). However, when I try to go to the network under Places or launch Firefox, I am unsuccessful in getting anything.

I would rather have a full 54Mbps connection, bbut as I am still in the tinkering stage, I will take whatever connection I can get!  Tell me about the easier one for 11 Mbps.

---

### Post by database_dan on 2007-07-01
sjr,
I am a little confused. You said that you were using a Linksys WMP54G (which is the same wireless card that I have). Now according to your output, you are using a Broadcom card...

```

$ lspci
01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

I did notice that the built in system > admin > network applet does not have the ability to handle WPA encryption, but handles open and WEP networks just fine. So if you are trying to connect WPA, then you are out of luck.

I think Linksys made four or five revisions of the WMP54G card, but they should all be based on the RaLink RT2500 chipset, which is pretty popular as far as I can tell. If memory serves, the RT2500 was natively supported by Ubuntu since the Dapper Drake release, so Edgy Eft should have no problems. I was able to get my WMP54G working out of the box with no external utilities by using the built in system > admin > network applet. I never could get ndis wrapper to work for me. I have also recently found a wireless manager that enables WPA encryption for RT series cards, but cannot seem to make it work with my setup.

Best of luck,
~Dan

---

### Post by kevdog on 2007-07-01
Your card works has a Broadcom chipset.  I understand you want to use fwcutter, which is totally reasonable.
Im pointing you to this post since its directions are excellent:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by weblordpepe on 2007-07-01
broadcom?? Noooo...

I never got my broadcom chipset to work with WPA. I can use it with WEP and unsecured wifi fine tho.
I have another wifi card, a d-link one. That works on wpa with a restricted driver, but wont work on WEP or unsecured. Yay!

---

### Post by kevdog on 2007-07-01
I have a broadcom chipset

Here is mine:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

And mine works with WEP/WPA.  Its most likely a driver related issue, and not a broadcom issue.
You have a very common chipset

---

### Post by Ayuthia on 2007-07-01
If you take a look at the ndiswrapper site:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)
it does show that there are different versions of this card and it looks like Linksys does have some cards using Broadcom and some with RaLink.  So this card is most likely a Broadcom Card BCM4306 with a 14e4:4320 pci id.

---

### Post by sjrlaw on 2007-07-01
Thanks, Kevdog.  The instruction page you sent me to says the method requires an Internet connection, so I should hook up the machine via CAT5 cable to my ethernet card.  That is somewhat problematic for me.  Can I download the files via another machine then transfer them to the Ubuntu machine via "sneakernet" or do I have to have an active connection during the install?

---

### Post by kevdog on 2007-07-01
I believe there only a couple of files that need downloading.  Al can be downloaded to USB and then transfered to ubuntu computer via USB stick

---

### Post by weblordpepe on 2007-07-01
> **kevdog said:**
> I have a broadcom chipset

Here is mine:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

And mine works with WEP/WPA.  Its most likely a driver related issue, and not a broadcom issue.
You have a very common chipsetBut theres been so many tutorials and so many configs and messy stuff and ahhh I broke it waaa! :cry:

---

### Post by MrFSL on 2007-07-01
@weblordpepe

I have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) and don't have any problems whatsoever. And setup with WPA is very simple. 

When I install ubuntu I copy the firmware over with a simple: 

sudo cp ./firmware/* /lib/firmware
sudo cp ./firmware/* /libfirmware/`uname -r`

Then I install wicd:
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

sudo dpkg -i wicd<version>.deb

This works perfectly and oddly enough I don't get any drop offs like I used to with Windows.

---

### Post by weblordpepe on 2007-07-01
*sniffle* *sniffle* yea?
Ive got it going now without WPA but Im afraid to touch anything :/

---

### Post by kevdog on 2007-07-01
So you got everything working with the bcm43xx cutter method?? 

Great.

Why complain???

For WPA
First install wpasupplicant:

sudo aptitude install wpasupplicant

The the tricky part begins.  Are you using network manager or wicd??

---

### Post by MrFSL on 2007-07-01
For the record I also have an internal:

Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Which simply does NOT work reliably with Network-Manager and WPA. This is why I originally switched to WICD. I have never looked back. Wicd is buggy (and I wish it wasn't) but it solved 100% all my wireless networking Ubuntu/Debian/Linux issues.

Cheers.

---

### Post by imdano on 2007-07-01
Hey want to do me a favor and tell me some of the bugs you've noticed in wicd?  Also make sure you download the newest version, we've been rapidly fixing a lot of them (especially related to the tray freezing).

---

### Post by weblordpepe on 2007-07-01
> **kevdog said:**
> 
Why complain???

I dont know. I am awkward in my puddle of halfworkingwifiness :(

---

### Post by MrFSL on 2007-07-01
WICD Bugs.... Sure!

Where do I start...

1) When I am using static addresses it often locks up trying to set the static DNS entries. I have to kill and restart the wicd daemon to kill this hang. I resolve this bug by manually entering the namerservers in /etc/resolv.conf and leave the static entries blank in WICD.

2) Wired Connections - I would like to use one network utility for ALL networking in Linux. If I install WICD on a system with no wireless adapters it locks up my whole box, or makes the whole box run slow as you can imagine.

I have a lot of network security at the house so I often want to use the wired connection on my laptop to create a small network with a computer I am working on. I have always used the ICS (internet connection sharing) section of Fireburner to do this and it works well. - HOWEVER, using wicd the wired connection simply does not get its static addresses correctly. I have to use /etc/network/interfaces and ifup/ifdown to configure my static wired connection. I don't know about the latest WICD but as of 1.2.7 if I use the WICD utility to try and configure the wired address I have to kill the WICD daemon and restart before I can even use ifup/ifdown to configure my wired connection.

**NOTE** - I understand that wicd (WIRELESS internet connection daemon) is focused on WIRELESS connections but this is short-sited in my mind. It offers the ability to configure Wired connections but that whole section is where I notice most of my bugs. 

There are a handful of other (non-critical) bugs like repeat AP entries in the gui but these don't matter that much to me. I also have not had no success setting up wireless WPA protected AD-Hoc connections either. 

I also think its important to note that network-manager suffers from just as many (if not more) bugs. At least WICD delivers (for me) on their primary goal of providing me good wireless connectivity with minimal setup.

Hope this helps. You WICD folk make a good product.

Cheers
MrFSL

---

### Post by imdano on 2007-07-01
Thanks for the input. I think a few of the issues you're having are fixed in newer versions (I know some static address issues were fixed, and wired support got improved in 1.2.9).  Try using 1.3.0 (or 1.2.9, but I think the static address problems were still in that release) and see if some of these problems are solved, or if you see any new problems.  I'm actually looking into some kind of integrated ad-hoc network creation as well, although it's probably not something that will be added in the short term.

---

### Post by MrFSL on 2007-07-01
I'm not complaining. I used to script this out myself with wpa-supplicant back in my Debian days. Wicd has provided me with a 90% solution to my Linux networking issues. I do use Ad-Hoc networking extensively thought. At these times I disable WICD and use the old manual methods. Wicd in conjunction with Ubuntu still offers me a solution that I can install for other computer users who are fed up with Windows and cannot afford Macs. Keep up the good work and I will continue to recommend the wicd project exclusively (for now with a short disclaimer concern its buggy-ness) ;)

Cheers
MrFSL

---

### Post by imdano on 2007-07-02
Thanks for the endorsement, it's great seeing people recommending wicd on the forums here.  Also, we're most likely going to have support for creating an ad-hoc network integrated into the next released of wicd.  I've already got support for it without encryption working, and WEP support should follow that.  WPA could create be a challenge, though.  Have you been able to get that working at all (outside of wicd)?

---

### Post by MrFSL on 2007-07-02
I think I have but it's been awhile since I required security on my Ad-Hoc networks. Usually I only encrypt my Ad-Hoc networks when I am on the road with other people from the office (and it's been a while since that has happened). 

I'll try to set it up with WPA when I get a chance this week and will let you know how it turns out.

I'm pretty sure I have done this before but it has been awhile.

---

