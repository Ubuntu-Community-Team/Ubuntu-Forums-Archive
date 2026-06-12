---
title: "Airsnort, Kismet - How to get 'em working?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Spanky2k5 on 2008-05-18
Hey all,

I've got 3 wireless cards, 1 PCI and 2 USB
My PCI card is a Broadcom Airforce One 54g
One USB is Phillips SNU5600
Other is Netgear WG111v2 with rtl8187 chipset

I'm wanting to get one of these working with either Airsnort or Kismet (preferably Airsnort) so I can crack my WLAN's WEP key for use in my dissertation.

I can't get airsnort working properly, It's installed and all but doesn't seem to like my cards - i'm not sure how to configure it either.

Kismet is installed and I've played with the kismet.conf file but don't seem to be able to get the right combination for the 'source' section for any of my NICs.

I'm sure at least one of my NICs is compatible with one of the apps but don't know how to configure it correctly.

Can anyone help me with this?

---

### Post by Monicker on 2008-05-18
Aircrack-ng is a more up to date tool than airsnort, and the Netgear is listed as being compatible.

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers")

---

### Post by Spanky2k5 on 2008-05-18
Thanks for the reply
I've heard of Aircrack, however it's not one of the tools I've learnt of for my paper. 
Does it discover hidden SSIDs, utilise the FMS attack and provide output? or is it one of the tools that saves in pcap for another utility to read?

EDIT: I've just read through the site and realised it does do all of the above. I'll check it out in the morning in between revision.....need to get my hands on a prism2 based card, they rock!

---

### Post by nicedude on 2008-05-19
I would recommend using kismet to sniff & collect and then aircrack-ng to crack any keys from captured IV packets. You will need to study up on how to accomplish that though as it takes a bit of learning.

You will need to make sure that whatever drivers you are trying to use with your card are compatible as well as some will not be ( For example if you used Ndiswrapper to install an XP driver that wont work ) So google around for drivers for your models that allow "monitor mode" as you need that capability. 

Please note the file kismet.conf must be configured as well for use. At a minimum you need to change the "source= " line to represent your cards values ( Proper format for this is "driver","spawninginterface","name" ) 

Here is what my line looks like for my card so you can get the idea what I mean
source=madwifi_ag,wifi0,madwifi

And kismet will discover hidden ssid's easily, just give it some time in their presence :-)

Hope my recommendations help get you headed in the right direction :-)

PM me with particulars of your aircrack supported cards if you need help finding the proper drivers.

---

### Post by Monicker on 2008-05-19
Kismet is a fine tool, but if you just want to collect IVs for aircrack-ng,  the airodump-ng program in the suite works just fine for the job.

---

### Post by nicedude on 2008-05-19
Your right PLF as you should use a replay attack to collect the IV's quickly I just love to sniff and log with kismet as I like to sniff more than crack although I recently aquired a set of 60GB WPA Rainbow tables that I need to try out, but I live on a farm in the middle of nowhere and my neigbors all have WEP and I have to drive the truck up to the front of the property to even get them in range :-(. I use WEP too though since to be in range of my wireless you have to be on my land and easily within range of my AR-15 :-)

---

### Post by Spanky2k5 on 2008-05-19
I've tried configuring kismet, changing the userid, source and server settings, however I can't seem to get it working with any of my cards.

I know broadcom isn't a widely supported chipset but I thought that my rtl8181 WG111v2 would at least give me something....

---

### Post by hyper_ch on 2008-05-19
kismet needs to be run as root

---

### Post by Spanky2k5 on 2008-05-19
I can run kismet but I get the 'Fatal Error' output saying there's something wrong with the driver I selected in kismet.conf.

I've tried changing the driver I use but still get Fatal Error's

---

### Post by Monicker on 2008-05-19
> **Spanky2k5 said:**
> I can run kismet but I get the 'Fatal Error' output saying there's something wrong with the driver I selected in kismet.conf.

I've tried changing the driver I use but still get Fatal Error's

What is the exact error message?

I have an Alfa AWUS036H usb wireless adapter which also uses the rtl8187 chipset, and it works fine with both kismet and aircrack.


Here is what I have in my  kismet.conf in regards to sources:

```
source=rt8180,wlan0,rt8180
enablesources=rt8180
```

---

### Post by Spanky2k5 on 2008-05-19
This is the error message I get not after changing my kismet.conf so it's similar to yours

```

root@USB-Ubuntu:/# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to martin (1000) gid 1000
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'rtl8180' in source 'rtl8180,wlan0,Netgear USB'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

---

### Post by Monicker on 2008-05-19
It looks like capture source type is not specified correctly.  It should be rt8180 and not rtl8180

Just to clarify, for the following
```

source=rt8180,wlan0,rt8180
```

You have 3 values after the equal sign.  The first value is the capture source type, the second is the actual network interface to use, and the third is just a label ( though I have it the same as the source type in my config).  The label must match in the source and enablesource lines.

The capture source types are predefined for specific chipsets.  You can find them all in section 12 of this link:  [http://www.kismetwireless.net/documentation.shtml]("http://www.kismetwireless.net/documentation.shtml")

---

### Post by Spanky2k5 on 2008-05-19
Bah, don't I feel like a douche.
Cheers dude, I''ll check that out tomorrow morning. Supposed to be packing up my flat at the minute...

---

### Post by nicedude on 2008-05-20
On top of your card being supported you have to make sure to use the proper driver as well. For example if you used Ndiswrapper to make your wifi work then you have zero chance of using kismet. What you need to research is how to configure your wifi card into "monitor" mode as by default it will be in ad-hoc or managed mode and most factory drivers do not support monitor mode as the manufacturer had no intention of you using it.

A simple iwconfig command can tell you what mode you are currently in here is the relevant part of my iwconfig output for the adapter that I am using to write this

ath0      IEEE 802.11g  ESSID:"some*******name"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 

see where it says managed , if yours says managed there as well then it won't work.

LOL I had to bleep out my essid as I remembered it contains swear word haha I leave it like that so its unique :-) If you ever see an essid with the ******* filled in with a curse word then I am near by :-) 

I don't have the cards you list so I don't know what patched drivers you should be using but maybe someone else here does.

Hope that helps you understand where to look for solutions.

---

### Post by Spanky2k5 on 2008-05-20
thanks man.
I played a little with aircrack yesterday and was able to put my Broadcom card into monitor mode but its said the Netgear one was unsupported.

It got a little complex after that as I tried to disable and re-enable ath0, but there was no reference to it in the list the command threw up anyway.

Does Aircrack require you to know the MAC of the AP you wish to access? Or is it possible to sniff packets/probe for WLAN's nearby and make an attempt using data gleaned from them?

---

### Post by nicedude on 2008-05-20
Do  your recons with kismet as it will give you the network info of all locally transmitting wifi sources including non broadcasting hidden networks . then use aircrack from there, research using a replay attack which is what will speed up collection of encrypted packets so you can get enough to break the WEP key without having to wait a long time for enough to be broadcast naturally by legit users using the wifi network to be attacked.

Enjoy your learning and I would suggest getting a wardriving or pentesting book to read either via a bookstore or via bit torrent ( I got mine from the later ) :-)

nicedude

---

### Post by nicedude on 2008-05-20
oops sorry I double posted due to watching movie while posting

---

### Post by Spanky2k5 on 2008-05-22
I tried out Kismet again, this time with the correct kismet.conf settings
Got another fatal error only different this time 
```

root@USB-Ubuntu:/# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to martin (1000) gid 1000
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'rt8180' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
root@USB-Ubuntu:/# 


```


EDIT: Are there any GUI tools that sniff and exploit replay & FMS attack?
      ....aside from Airsnort which doesn't like my cards

---

