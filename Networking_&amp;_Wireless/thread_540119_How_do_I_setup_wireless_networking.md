---
title: "How do I setup wireless networking?"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by bobthebullet990 on 2007-09-01
Hi all... 

Yesterday I took the decision to finally remove Win XP from my system and move into the world of Linux!!! ...After learning and using Linux day in day out at uni, I have a good basic idea about its structure and how to do basic bits and bobs!

I am currently using my wired network connection directly to my router; however, I would really like to setup my wireless network card so I can get rid of the long wire to my router! 

I have a [Sitecom Wireless 54Mbps PCI Card], if this is not supported, I also have a USB D-Link one that came with the router that I could use!

Could anyone let me know how I go about setting up this wireless connection! many thanks!

---

### Post by dutchie86 on 2007-09-01
I am can't help you with the PCI card you have, how ever I would suggest you use the USB one as that *should* work straight out the box. When you plug it in and you click on the networking icon in the system tray, which is by default top right of the screen, you should see a list of wireless networks. Simply click on your wireless network, enter in your WPA key (you do use WPA don't you?) and hey presto it should all work if you have DHCP enabled on your router, which is normally the default. 

If you have any further issues let us know and also include the model number of the dlink usb wireless card and which version of ubuntu you use.

Cheers,

Ray:)

---

### Post by bobthebullet990 on 2007-09-01
Thanks... I just plugged it in, and clicked the icon, but it just comes up with eth0 and another option lo! ...I'm sure this can't be the correct place??? 

...Also, how do I find the ubuntu version I am running? ...I have made several updates of key components including kernel updates! ...I made the ubuntu CD about 8 months ago!

---

### Post by dutchie86 on 2007-09-01
What model of card do you have? The easiest way is to go to the System menu and there should be a About ubuntu item or an help item. 

Also when the card is plugged in, right click on the network icon in the system tray and ensure wireless networking is ticked if it is there, if it isn't open up a terminal screen by clicking Application -> Accessories -> Terminal and type in iwconfig or iwlist (can't remember which one off the top of my head lists the icons, i am currently on a non linux machine so i cant check either sorry), and past the output here (the right command will output a list of network cards).

Cheers.

Ray

---

### Post by bobthebullet990 on 2007-09-02
OK, here is the output from iwconfig:

```

matt@matt-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

```

NOTE: I have three network cards; one on-board ethernet chip, one PCI sitecom 54g wireless card and one D-Link USB wireless dongle [came with the router!]

Models: 
D-Link DWA-110 USB
Sitecom WL-115 PCI

---

