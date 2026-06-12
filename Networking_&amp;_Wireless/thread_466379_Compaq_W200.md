---
title: "Compaq W200"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-06-06
I followed directions at [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200) for installing the orinoco driver for this device, but got errors about /dev not existing with 

make

and

sudo make install

This may be due to the upgrade to the -16 kernel.

Is there another way to go about activating this device in Feisty?

Many thanks!

-merlin

---

### Post by chili555 on 2007-06-06
At the top of the page, did you see this:> In order to compile, edit lines 4287, 4288 of orinoco.c replacing dev->dev.parent with dev->class_dev.devI believe if you gedit or kate or your favorite text editor these lines, it will 'make' just fine. It did just fine here.

---

### Post by merlinus on 2007-06-06
Brilliant!  Absolutely brilliant!  Thanks so much....

Now...  I only use the W200 to connect to external wireless networks, e.g. airports, cybercafes.

So in System/Administration/Network, should I leave Enable roaming mode checked, or uncheck the box and fill in the other info?

If so, what goes where?

-merlin

---

### Post by chili555 on 2007-06-06
Enable Roaming if you want to use Network Manager, which works well for some and not well for others. I have a laptop with it and one without. They both connect easily.

---

### Post by merlinus on 2007-06-06
How do you use Network Manager?  I cannot find it in the Gnome menus, only System/Administration/Network, which opens the Network Settings dialog box.

Or are you referring to Places/Network?  And will that show wireless networks available at aiports, etc.?

Thanks again!

-merlin

---

### Post by chili555 on 2007-06-06
There is an icon in the notification area up by the clock; it looks like five progressively higher bars. Click on it and select the network you want to connect to.

---

### Post by merlinus on 2007-06-06
Just saw this caveat at the help.ubuntu.com site:

Feisty Status 2007-04-27: Using the GNOME Network Manager in Roaming mode seems to hang the system. This needs further investigation. Manual Connection with either static IP address or DHCP is working.

This happened to me earlier this afternoon whilst testing the WLAN connectivity.  I had to do a hard shutdown twice.

I imagine that using a static IP address would not work at an airport or cybercafe, though.  So would DHCP be the way to go in the Manual Connection dialog?  Are there other options?

Thanks...

-merlin

---

### Post by chili555 on 2007-06-06
I am an old grey-beard manual configuration kinda guy. When I go to a coffee shop or motel, I do:```
sudo iwlist eth1 scan
```Substitute your wireless interface here if it's not eth1. Scan may take a few tries. You will probably see a cell broadcasting its ESSID, such as 'motel6'  Then do:```
sudo iwconfig eth1 essid motel6
sudo dhclient eth1
```If there is no encryption, you should connect.

Other options include wifi-radar, wlassistant and Wicd. Search this forum for them. They are all essentially GUI front-ends for the above.

---

### Post by merlinus on 2007-06-06
I'm with you, but my beard is more white now than grey.  I started with DOS 1.x.

But my partner is often traveling with the laptop, and a gui would be much, much easier for her.

Thanks again for all your assistance and expertise.

-merlin

---

### Post by merlinus on 2007-06-07
I tried the terminal commands you suggested, and located an unencrypted network.

But then this:
```

sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:cd:8c:79:ee
Sending on   LPF/eth1/00:0b:cd:8c:79:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I have no idea what all this means, but I was not able to connect to the Internet.

Thanks for any clarification....

-merlin

---

### Post by chili555 on 2007-06-07
It means your laptop asked for an IP address, a connection, and has not received one from the access point. It could mean that you made a small error in the ESSID; Linksys is not the same as linksys and belkin54 is not the same as belkin54g. Scan again and recheck your commands.

It could mean MAC address filtering is in place in the access point; if it is and your MAC address is not hard-coded in the access point, you will not connect.

It could mean you are too far away to get enough signal strength to connect. Here is an example:```
eth1      Scan completed :
          Cell 01 - Address: 99:9C:41:19:58:77
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=**84/100**  Signal level=-49 dBm  Noise level=-49 dBm
                    Extra: Last beacon: 308ms ago
```If the signal strength were 29/100, I could probably not connect.

It could also mean your card is shy. Let's try adding the MAC address of the access point to our commands:```
sudo iwconfig eth1 essid myrouter1
sudo iwconfig ap 99:9C:41:19:58:77
sudo dhclient eth1
```eth1 *is* your correct wireless interface, correct?

---

### Post by grahams on 2007-06-12
Hi, do you find the W200 driver to be stable on feisty for use over extended times i.e. > 1 day?

I ask because on edgy the network would drop on the w200 after a few hours, due to a know but unfixed bug.

---

