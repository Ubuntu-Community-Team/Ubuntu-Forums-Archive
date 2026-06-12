---
title: "BT HomeHub"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by johnupatree on 2009-09-11
OK, total Ubuntu virgin, so please be _very_ gentle with me!!

Just installed 9.04 on my Dell Inspiron, no problems with that, dead easy.  BUT cannot connect to my BT HomeHub.  Opened Network and entered BTHomeHub into the SSID, but no matter where I try and enter the key it will not connect. This is so simple I know. Go on, someone put me out of my misery!
Will have a go when I get home, work is getting in the way of playing with my new found friend :P

---

### Post by nothingspecial on 2009-09-11
Can you see your home network in network manager - the icon on your panel (top right default I think)?

Also post your wireless info. Open a terminal (in your menus applications > accessories > terminal) and type

```
sudo lshw -C network
``` 

Then copy and paste the output here.

---

### Post by benj1 on 2009-09-11
ive just recently got one and it worked fine.
are you trying to connect wirelessly? is it showing up in network manager?

if so remember you need to be relatively close to the router the first time you connect to exchange keys etc, after that you should be able to roam farther afield without problems, another issue could be it hasn't found the best channel yet, which will affect the range, i don't know how it sets that but you can set it manually on the router.

---

### Post by aeiah on 2009-09-11
its more likely to be an issue with your wireless card, not your router.

---

### Post by Truefire on 2009-09-11
Is the wireless light on? Do any networks show up, and finally, can you connect wired to get updates? I've noticed that once you update ( and perhaps go to System > Administrator > Hardware/Device Drivers ) things *just work.* Good luck :D

---

### Post by johnupatree on 2009-09-11
Thanks for all the replies, makes me feel very welcome!
OK. The router is working fine and well within range, about 6' away from my comfy chair, yes it is wireless. All works without problem in XP on the same machine in the same location etc.
Could not see home network in network manager, so entered details manually.

Will post info later when I get home and have had a relaxing beer :P

Thanks again for all the advice

---

### Post by johnupatree on 2009-09-19
Sorry for the delay in posting further regarding my ongoing connection problem, family issues!
OK. Drop down box at top of screen has tick next to enable Wireless.  Wireless network window states 'Device Not Ready' so puzzled! As stated before all is working well when I am using XP. Posted this via same machine on XP.
Have enclosed output as requested by nothingspecial, hope it helps. Did notice that it states that wireless network is disabled.

	 	 john@john-laptop:~$ sudo lshw -c network  
   *-network:0              
        description: Ethernet interface  
        product: BCM4401 100Base-T  
        vendor: Broadcom Corporation  
        physical id: 1  
        bus info: pci@0000:02:01.0  
        logical name: eth0  
        version: 01  
        serial: 00:11:43:6e:2c:82  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s  
   *-network:1  
        description: Network controller  
        product: BCM4306 802.11b/g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 2  
        bus info: pci@0000:02:02.0  
        version: 03  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=32 module=ssb  
   *-network:0 DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:0b:7d:13:88:d0  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
   *-network:1 DISABLED  
        description: Ethernet interface  
        physical id: 3  
        logical name: pan0  
        serial: ce:fb:31:39:2b:7d  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 john@john-laptop:~$  
 

Thanks again

---

### Post by nothingspecial on 2009-09-19
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7704375")

---

### Post by mapes12 on 2009-09-19
Hi John

Your BTHomeHub is OK. The problem is your PC's wifi adapter. I've found this fix that may help you out: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Even if it works in XP doesn't mean it will work in Ubu because completely different drivers are used.

Best wishes.

Mark

---

### Post by dnairb on 2009-09-19
Also, check that you are uing the correct SSID.
As an example, my network's SSID is BTHomeHub2-G934.

---

### Post by johnupatree on 2009-09-19
Thanks to mapes12, I followed the link and eventually found a link to b43-fwcutter for Jaunty.  This means I am now online and able to post to this forum using Ubuntu, thanks again to everyone involved in helping me sort out my problem.

---

### Post by mapes12 on 2009-09-20
Hi John

Glad you fixed it.

Just a tip from experience. Keep a bookmark or something, to keep track of any tweaks you need to make to your machine. Everyones set up is different and if you keep a tab on the location of resources that helps your stuff work i.e. in your case the wifi adapter, then when you upgrade or need to do a fresh install you will have everything ready to make your system work without having to go hunting down fixes again.

Mark

---

### Post by johnupatree on 2009-09-20
Hi Mark,

Thanks for the tip, sounds like an excellent idea and one I will take up with immediate effect!

All the best

John

---

