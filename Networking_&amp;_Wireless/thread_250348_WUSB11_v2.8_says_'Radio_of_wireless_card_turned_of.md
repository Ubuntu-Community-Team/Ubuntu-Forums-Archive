---
title: "WUSB11 v2.8 says 'Radio of wireless card turned off'"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by digivore on 2006-09-04
Hi, I recently purchased a Linksys WUSB11 v2.8.
I tried it on my windows box and it works fine.
However, i am having problems getting it working in Kubuntu.

As far as i can tell it is installed, it shows up in System Settings -> Network Settings.  It is named wlan0 and the icon is 2 little red antenna (should these be green?) Als shows a green checkmark and says it is enabled.

I figure this is good because it means kubuntu recognizes it.
But when i go to Kmenu -> Internet -> Wireless Assistant 0.5.5 it gives me an error when it tries to scan for networks which really throws me off.  Maybe someone has seen this or can explain/correct it for me.

Error Message: "[COLOR="black"]**Radio of your wireless card seems to be turned off using an external switch on your computer. You need to turn it on to be able to use wireless networks.**[/COLOR]"

So basically thats where i'm at, I have tried some other things, but it doesn't seem like a driver issue since it recognizes that a USB wireless adapter has been plugged in...

Is there commands i can try to get it to work?  or another program instead of 'Wireless Assistant 0.5.5' ?  
i'm very new to Linux, but would like to get this going.

---

### Post by Poirot on 2006-09-04
Hello,

I think I have a similar problem. It seems the radio on my wireless card might be switched off too.

I type this
```
sudo lshw -C network
```
and get this
```
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth1
       version: 02
       serial: 01:23:45:67:89:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-amd64-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e2000000-e2001fff irq:11

```

so I can see that it is recognised and a driver (the correct one I think) is being used. My card is a Belkin F5D7001uk, I believe it has a broadcom chipset. BUT it says network DISABLED.... What's going on?

I also did this
```
sudo iwconfig eth1
```
and got this reply from my computer (slightly modified for security)
```
eth1      IEEE 802.11b/g  ESSID:"wireless network"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I noticed that access point is invalid and everything is off or zero.

I also tried scanning for networks like this
```
sudo iwlist eth1 scan
```
and let out a sigh of resignation when I was told this
```
eth1      Interface doesn't support scanning : No such device
```

:confused: Now I am beaten. Can anyone help?

digivore, can you post similar command line responses for comparison?

---

### Post by digivore on 2006-09-04
Hey,   thats weird about your wireless card being eth0.
 mine comes up as wlan0.  but whatever, 

As for me, i have noticed that if I type:
"sudo iwconfig wlan0 essid any"

and a combination of 
"sudo ifconfig wlan0 up"   and
"sudo ifconfig wlan0 down"
it will evntually let me scan for networks, and shows my router, but it won't let me connect to it.

I think the key to my breakthrough was the 'essid any'  part.
still don't know what my current solution is though...

---

### Post by Poirot on 2006-09-05
I fixed my problems using this excellent howto [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

This activated the card and, like you, I could see the router but not connect. I finally got my wireless up and running after I disabled IPV6 using section 4.5.2 in this guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) 

Hope this helps.

Poirot

---

### Post by digivore on 2006-11-13
Hey, yah to i had it working in Breezy, all was good, and then i went and installed Enlightenment Desktop environment, and that screwed up, and now i just installed edgy, and can't for  life of me figure out what i did last time to make it work.  I don't think i had to disable IPV6 last time...  but i'll try it now..  I can see the access point in the list, but the connection always fails.  This time i'm making notes!  writing it down so i don't have to go through this again!.  Glad you got yours working!

---

