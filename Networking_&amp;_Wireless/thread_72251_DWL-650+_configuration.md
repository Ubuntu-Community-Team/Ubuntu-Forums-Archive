---
title: "DWL-650+ configuration"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by augereffect on 2005-10-05
I just bought a Dlink DWL-650+ card because I found a list that said it worked out of the box.  I have stuck it in and tried the configure thing under network connections, and so far the LED will go on, but that's it at the moment.  I'm using a regular wireless base station, without any kind of encryption or password.  Would someone tell me how to configure the thing?

---

### Post by jdong on 2005-10-05
Go to System->Administration->Networking. Is your network card (should be called "ath0") listed? If so, configuring it will be a breeze. If not, then come yell at me :)

---

### Post by augereffect on 2005-10-05
ath0 doesn't bring up anything.  wlan0 does bring up a thing that says its signal stringth, but configuring it doesn't do much.  What should I do?

---

### Post by jdong on 2005-10-05
OH, DWL-650+,  not G650... sorry, got my D-Links confused!

This should be a TI-ACX1xx based card, which is supported under Linux, but perhaps with more effort than desired. I'll go out and research this a bit, but most likely you'll be compiling drivers from [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)


If someone else can walk him through the process that'd be great -- I have an exam tomorrow :). Maybe searching up acx1xx, acx111, acx100 will get you something (at the forums)

---

### Post by augereffect on 2005-10-06
Whoa!  This is really wierd.  I found this site, [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php),
which is a delightfully newbie-friendly guide to setting up cards such as the DWL-650+.  I didn't need to install the driver, since the driver was already there and the lights were on, but I did use the ping business and whatnot and got the card connected to my wireless router.  My connection worked, but only for a few seconds at a time.  It would load several pages, but then when you kept going for too long or went to a new domain, it would stop and become "idle".  Plugging in the ethernet cable for even a second would fix this, and the card would start loading again.  Does anyone know about this?

Then I made the foolish mistake of executing the last commands on the page above, with the hopes of making the card run the next time I booted up.  I booted up again, and now the driver is completely gone.  I would go through the stuff on the page, but the make business didn't work last time.  The only thing I can think to do is to reinstall Hoary and start again from the top.  Any ideas?

---

### Post by Pvt_Beeano on 2006-02-21
I've been trying to use this guide too, it worked a treat on Open SuSE 10, but I wanted Ubuntu.....

Basically, you have to install the linux-source package from synaptic and also grab the older version of GCC (3.4?) before the make commands will even try to work.

Anyone around with a bit more experience than me care to lend a hand?  :confused:

---

### Post by dbott67 on 2006-02-21
I had some issues with my D-Link DWL-650+ after upgrading from Hoary to Breezy.  Try reading this [thread]("http://www.ubuntuforums.org/showthread.php?t=69951&page=2").  Take a look at your **/etc/network/interfaces** file to see if the "map wlan0" command is in there.  My post (#11) contains some output & config files for comparison sake.  Post 13 contains the "magic bullet" that seems to fix the problem.

-Dave

---

### Post by dbott67 on 2006-02-21
By the way, I did not need to download or compile the acx driver.  The module included with Breezy loaded properly, it just seems that the "map wlan0" command was missing from the /etc/network/interfaces file.

-Dave

---

### Post by Pvt_Beeano on 2006-02-21
Okay, I took a look through that thread and made the changes to the interface file, but I'm still not having any luck, here's what I have:

**iwconfig:**

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"tux"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**iwlist wlan0 scan:**

```
wlan0     No scan results
```

**interfaces:**

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map wlan0

# The primary network interface
iface eth0 inet static
	address 192.200.1.2
	netmask 255.255.255.0
	network 192.200.1.0
	broadcast 192.200.1.255
	gateway 192.200.1.1

iface wlan0 inet static
address 192.100.1.2
netmask 255.255.255.0
gateway 192.100.1.1
wireless-essid tux
wireless-key s:knowledgeable

auto wlan0



auto eth0
```


Any idea where I'm going wrong? :confused:

---

### Post by Pvt_Beeano on 2006-02-21
WoooHoooo, figured it out.......no more Redmond OS for me :).  Just had to take the stuff about eth0 out of there and it worked a treat, even picked up a few unsecured wlan's in my village.  Must mention that down the pub ;)

---

### Post by dbott67 on 2006-02-21
I was just about to post that you can only have 1 active interface, as your computer won't know which route to take when surfing.  Disabling the eth0 is a quick fix.

You can setup a multi-homed network (2 nics) but you need to define the default & static routes.  

The other thing I noticed is that your wireless network is on a different subnet than your wired network (192.**100**.1.xxx vs. 192.**200**.1.xxx).  Do you have 2 different routers (i.e. a wired & wireless) --- or is the network part of a campus/corporate network?

-Dave

---

### Post by Pvt_Beeano on 2006-02-22
I have two separate network appliances, the wired one is a 2003 server XP client network and the wireless one is a basically a free hotspot provided by me for people in my village to connect to.

Well spotted though ;)

---

