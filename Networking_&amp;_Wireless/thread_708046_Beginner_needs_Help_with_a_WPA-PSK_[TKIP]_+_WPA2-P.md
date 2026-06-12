---
title: "Beginner needs Help with a WPA-PSK [TKIP] + WPA2-PSK [AES] encryption"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by bajaboy1010 on 2008-02-25
I have a  WPA-PSK [TKIP] + WPA2-PSK [AES] encrypted network, safe but not hassle free. I would really apreciate any help on resolving the matter.

I can connect to the internet when no encryption is on with my old 2wire card
so I'm stuck

Thanks -

---

### Post by wieman01 on 2008-02-26
First off, what wireless cards have you got and second what chipset are they?

Please also post (from command line):
> sudo iwlist scan
> sudo lshw -C network
Post the results and we'll see. :-)

---

### Post by bajaboy1010 on 2008-02-26
[COLOR=Black]ok, so my wireless card is a 2Wire 802.11 b Wireless pc card. 

Chipset... I don't know. 2wire's website doesn't specify.   

for sudo iwlist scan 

 > eth1         scan completed: 
Cell 01 - Address: 00:18:4d:96:0E:96
 Essid:"(my ssid)"
 Mode:Master Frequency:2.437 Ghz (channel 6)
Signal level:-38 dBm Noise level: -98 dBm
Encryption key: on 

for sudo lshw -C network

>    *-Network: 0
Description: Wireless interface
physical id: 2
logical name: eth1
serial 00:02:2d:b6:fe:ee
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=L ucent/Agere 8.42 link=no multicast=yes wireless=IEEE 802.11b

---

### Post by wieman01 on 2008-02-26
Oh, "orinoco" driver. I don't think it does support WPA/WPA2 in fact. You will have to do some more research but in case it turns out that is does not, you need to replace that driver with "ndiswrapper" and the native Windows driver.

If you decide to go for "ndiswrapper", please post here for help. I'll try to support you.

---

### Post by bajaboy1010 on 2008-02-26
I did some poking around, and it seems to vary source to source.. but no obvious support for the newer encryption.   

I figure that if I can get "ndiswrapper" to work, I might as well try.

I see if I can find a tutorial on how to, but if you have any specific advice, or a link to a good tutorial please let me know.

I apreciate the help!

---

### Post by bajaboy1010 on 2008-02-26
I forgot to mention some hangs that keep popping up for me when trying to follow tutorials.

My laptop is very, very old. 

(Xubuntu ftw!)

So I don't have a Cd drive or floppy- just usb, which often complicates things... like installing ndiswrapper.

---

### Post by wieman01 on 2008-02-27
There is a Ralink tutorial in my signature. It could help you getting started (ndiswrapper). Do you have a working Ethernet connection?

---

### Post by bajaboy1010 on 2008-02-27
Actually this laptop doesn't have an Ethernet port..

However, I think i have an old adapter that i can dig up - so yes.

---

### Post by bajaboy1010 on 2008-02-27
I'm almost done with your tutorial,

I'm stuck here:

Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):

> sudo ndiswrapper -i <your_ralink_driver>.inf

I unzipped the driver archive to the home folder.

then lots of files popped up, and I saw this file: WLTWOALL.inf

so I

> sudo ndiswrapper -i WLTWOALL.inf

But when I checked the driver's install it said this:


> rt2500pci : invalid driver!
wlrwoall : invalid driver
wltwo2x.cat : invalid driver
wltwo9x.cat : invalid driver
wltwoall : invalid driver

I attempted several different inputs- none worked..

---

### Post by wieman01 on 2008-02-27
> rt2500pci : invalid driver!
wlrwoall : invalid driver
wltwo2x.cat : invalid driver
wltwo9x.cat : invalid driver
wltwoall : invalid driver
This normally points to either a wrong driver (wrong version, etc.) or the fact that 'ndiswrapper' does not support your device. Please check this website for more:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

Is your device listed there?

---

### Post by bajaboy1010 on 2008-02-27
hmm.... no its not

looks like I'll have to buy a new card.

---

### Post by wieman01 on 2008-02-27
Too bad. There is a sticky in the wireless & networking section. Check it out for compatible hardware.

---

