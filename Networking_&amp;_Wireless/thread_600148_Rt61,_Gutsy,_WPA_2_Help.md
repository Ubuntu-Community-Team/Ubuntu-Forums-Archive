---
title: "Rt61, Gutsy, WPA 2 Help"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by balak on 2007-11-02
Hi All,

I have a specific question regarding WPA2 networks. I have a ralink rt61 wireless card:

```
02:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

```

I haven't messed around with the drivers. I have a clean install of gutsy and WEP worked out of the box with the default drivers (rt61pci). I did read the thread for installing the windows driver using ndiswrapper etc. - however I ran into issues finding the 64-bit driver for my card. Well, I downloaded the self-extracting exe from ralink website, but it always extracts a 32-bit version of the driver in crossover office :(

Back to my question. I can connect to WEP at home. And I can connect to some WPA2 networks but not others. 

Here is a sample wpa_supplicant config. file for the network I CAN connect to now in gutsy. I actually use networkmanager to connect, but this is to give you the network details.

```
network={
        ssid="xyz"
        key_mgmt=WPA-EAP
        phase2="auth=MSCHAPV2"
        eap=TTLS
        ca_cert="/etc/cert/xyz.pem"
        subject_match="CN=xyz"
        identity="ME"
        passwd="MYPASSWD"
}

```

The other network I am not able to connect is the following. I cannot connect to this network either using networkmanager or using wpa_supplicant in commandline. Note that I can connect to this network from feisty installation (with my own compiled driver of rt61).

```

network={
      ssid="abc"
      key_mgmt=IEEE8021X
      eap=peap
      phase2="auth=MSCHAPV2"
      ca_cert="/etc/cert/abc.pem"
      identity="ME"
      passwd="MYPASSWD"
}

```

Anybody knows what is the difference between the two networks listed above?

---

### Post by balak on 2007-11-06
bump!!

Did anybody get the default rt61 drivers in gutsy to work with WPA2

---

### Post by wieman01 on 2007-11-06
I doubt the current Ralink driver supports WPA2-EAP. PSK is no problem for sure, but EAP...

You might have to replace the current driver with "ndiswrapper" and the native Windows driver. That should let you use WPA2-EAP through Network Manager.

---

### Post by balak on 2007-11-06
Thanks for replying wieman01 :) 

> **wieman01 said:**
> 

You might have to replace the current driver with "ndiswrapper" and the native Windows driver. That should let you use WPA2-EAP through Network Manager.

I tried using ndiswrapper but I need the 64-bit windows driver. Is there a place where this is available?

I downloaded the driver from the Ralink website, but its an .EXE file and it always extracts the 32 bit driver.

---

### Post by zero244 on 2007-11-07
I couldn't get WPA to work in Gutsy, but like you I did get WEP to work. Using WEP is better than using nothing. I am thankful that the RT61 chip works at all in Ubuntu.
I dont have to connect to WPA networks since I use my wireless at home only.
Let us know if you get it to work.
Good Luck.

---

### Post by wieman01 on 2007-11-07
> **balak said:**
> I tried using ndiswrapper but I need the 64-bit windows driver. Is there a place where this is available?

I downloaded the driver from the Ralink website, but its an .EXE file and it always extracts the 32 bit driver.
Mmm... 64-bit should be found somewhere. I know at least of one guy who got a Ralink card working using my tutorial on 64-bit system. I have helped him a bit and he eventually found out that all he had to do was use the 64-bit version of the driver. Take a look at the tutorial (see signature) and post there if you need help.

If Network Manager does not support WPA2-EAP (whatever type of EAP you plan to use), I should be able to work something out for you as well (see other tutorial). But let's do one step at a time.

---

### Post by wieman01 on 2007-11-07
> **zero244 said:**
> I couldn't get WPA to work in Gutsy, but like you I did get WEP to work. Using WEP is better than using nothing. I am thankful that the RT61 chip works at all in Ubuntu.
I dont have to connect to WPA networks since I use my wireless at home only.
Let us know if you get it to work.
Good Luck.
WEP is actually just as secure as... well, nothing. ;-) If you know what you are doing of course.

---

### Post by Ronin69 on 2007-11-09
Wow!  How did you get RT61 to work with Gutsy out of the box?

I've been struggling with this for 2 days.  My Access Point is blank and I can't ping the router.   Loopback works.  Not sure if Logical Name: wmaster0 makes any difference from wlan0 that is listed in the interface file.

Any help would be appreciated.

---

### Post by Andrew MacDonald on 2007-11-11
rt61 with WPA worked out of the box for me with Gutsy-amd64 using Network Manager. However, it seems the stock drivers (rt61pci module) are poor. My maximum throughput was around 1 Mbps.

Next I tried ndiswrapper with some 64 bit Windows drivers. They seemed extremely sketch, so I was quite surprised when they actually worked, and I had good throughput. My intuition was correct in the end though, as after a week I traced the source of badass freezing (requiring hard reset) to this driver. If you want to try your luck with it anyway:
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=2699)

I ended up using the serialmonkey legacy drivers. The only downside is that I had to ditch Network Manager, and go with manual configuration. NM doesn't seem to be able to use them. Otherwise they're working flawlessly (including WPA2). The steps I followed:

1. Download the serialmonkey rt61 legacy CVS tarball [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

2. Remove the rt61pci module
```
sudo modprobe -r rt61pci
```

3. Blacklist the module, by adding the line ```
blacklist rt61pci
``` to /etc/modprobe.d/blacklist

4. Quit Network Manager if it's running.

5. Install the drivers following the directions in Module/README (the directions are excellent and include instructions on configuring WPA)

6. If it's working you can uninstall Network Manager at this point, or at least keep it from starting up (I just unchecked it in Preferences->Sessions).

7. To get wireless working on startup, I use the following stanza in /etc/network/interfaces (just following the serialmonkey directions)
```

auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 mode managed
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid [your SSID]
pre-up iwpriv wlan0 set AuthMode=WPA2PSK
pre-up iwpriv wlan0 set WPAPSK=[your ascii key]
pre-up iwpriv wlan0 set EncrypType=AES

```

---

### Post by brodiepearce on 2007-11-13
> **balak said:**
> 
Here is a sample wpa_supplicant config. file for the network I CAN connect to now in gutsy. I actually use networkmanager to connect, but this is to give you the network details.


Hi.. unrelated to your problems, but is there anything in particular you set to connect to WPA networks through the network manager (in the limited cases that you were able to)?  As of yet I've been unable to connect to my router using WPA-PSK and WPA2-PSK, tried disabling mac filtering etc. to no success.

---

### Post by balak on 2007-11-13
> **brodiepearce said:**
> Hi.. unrelated to your problems, but is there anything in particular you set to connect to WPA networks through the network manager (in the limited cases that you were able to)?  As of yet I've been unable to connect to my router using WPA-PSK and WPA2-PSK, tried disabling mac filtering etc. to no success.

I don't think I did anything special. Select WPA1/2 from the list and fill in your details.

It worked for the first network which is also using WPA2 and didn't work in the second which is also using WPA2. The only difference is that in the second network, the SSID is hidden. Maybe thats a networkmanager bug?

---

### Post by balak on 2007-11-13
Andrew: Thanks for your note. I had installed the legacy drivers for feisty but didn't want to go that way for gutsy. Looks like there is no other choice :(

As of now, I am dual booting feisty and gutsy and use the former while I am at work.

---

### Post by wieman01 on 2007-11-13
> **balak said:**
> I don't think I did anything special. Select WPA1/2 from the list and fill in your details.

It worked for the first network which is also using WPA2 and didn't work in the second which is also using WPA2. The only difference is that in the second network, the SSID is hidden. Maybe thats a networkmanager bug?
Yes, occasionally NM has issues with hidden ESSIDs.

---

### Post by Andrew MacDonald on 2007-11-13
Hiding your SSID does almost nothing to improve your security against a serious attacker anyway. ([http://en.wikipedia.org/wiki/SSID](http://en.wikipedia.org/wiki/SSID))

It's probably just easiest to broadcast it.

---

### Post by balak on 2007-11-15
> **Andrew MacDonald said:**
> Hiding your SSID does almost nothing to improve your security against a serious attacker anyway. ([http://en.wikipedia.org/wiki/SSID](http://en.wikipedia.org/wiki/SSID))

It's probably just easiest to broadcast it.


Well, in my case, I don't have control over the hidden part. It is decided by the corporate security gurus.

---

### Post by fairuz27 on 2007-11-23
My RT61 driver work with gutsy but the problem is, i have to enter the (WPA )access key manually every single time connecting to the network.
It doesn't seem to create some kind of profile to remember it.

No really much of a problem but kinda troublesome having to enter the key everytime my system restart.  The manual configuration doesn't seem to work at all. 

Any ideas?

---

### Post by JimboJet on 2007-11-26
> **Andrew MacDonald said:**
> 

I ended up using the serialmonkey legacy drivers. The only downside is that I had to ditch Network Manager, and go with manual configuration. NM doesn't seem to be able to use them. Otherwise they're working flawlessly (including WPA2). The steps I followed:

1. Download the serialmonkey rt61 legacy CVS tarball [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

2. Remove the rt61pci module

<snip...>


This worked perfectly for me. I had done something similar going from Edgy to Feisty, but it took about a week of trying different things and I couldn't be sure what eventually got it going. 

I'd been holding off going to Gutsy for a while knowing that I'd be disconnected. Took me about 20 minutes last night to get reconnected following the upgrade, I must be getting smarter.

Using a Linksys WMP54G ver 4.1

Many thanks!

---

