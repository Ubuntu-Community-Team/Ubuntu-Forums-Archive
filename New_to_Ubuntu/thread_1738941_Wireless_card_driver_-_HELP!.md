---
title: "Wireless card driver - HELP!"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by ctyonahl on 2011-04-25
I'm a total noob to Ubuntu and I'm having trouble finding the driver for my (old) wireless card for my IBM Thinkpad A31. 

I **THINK** it's this one: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Truemobile_1400](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Truemobile_1400)

Is there any way to check for sure what kind of wireless card I have? From there, do I need find the Windows version of the driver online then unpack it with ndiswrapper? 

There should be a Ubuntu "driver checker and installer" for noobs like us!

Thanks for any help you guys can give me with this! :)

---

### Post by grahammechanical on 2011-04-25
There is. In fact there are two. One is called Network manager the other is called Additional Drivers. Do you see a Network Manager icon? It will be on the top panel towards the right. Does it have a red exclamation mark against it? What do you see if you right and left click the icon?

If you do not have a Network Manager icon then you will need to make a wired connection to your modem/router. When you have established a connection go to System>Administration>Additional Drivers. If you are offered a driver to install, then do so and one will be installed over the Internet.

If this does not bring improvement then read this trouble shooting guide.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by ctyonahl on 2011-04-25
Thanks, grahammechanical. The funny thing is, I CAN indeed connect to my wireless network. Ubuntu notifies me that there is a "Connection Established", but when I open I browser and try loading Google.com, I can't connect. I have tried the "Additional Drivers" program you mentioned, but it doesn't list my driver. Any other ideas?

---

### Post by josephmills on 2011-04-25
could you please go to applications-->accessories-->terminal then type in  ```
lspci -nn
``` then paste it here thanks

---

### Post by ctyonahl on 2011-04-25
Ok, so I found out using lshw -C network that I have a Intersil Prism 2.5 Wavelan chipset. Does anyone know where to find the drivers for this card?

@josephmills 

I got the same result with lspci -nn

---

### Post by josephmills on 2011-04-25
could you please post the outcome of lspci -nn there is more on that list that we need to see the numbers that are in bold are the important part ```
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller** [14e4:4318]** (rev 02)

``` thanks again

---

### Post by wolfen69 on 2011-04-25
If you have a connection but can't get on the net, try unplugging your modem and router for 10 seconds, plug back in, and wait a couple of minutes. It's an old trick that has worked for me.

---

### Post by ctyonahl on 2011-04-25
Here you go josephmills:

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev 80)
02:00.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev 80)
02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)

---

### Post by ctyonahl on 2011-04-25
> **wolfen69 said:**
> If you have a connection but can't get on the net, try unplugging your modem and router for 10 seconds, plug back in, and wait a couple of minutes. It's an old trick that has worked for me.

OK, I will try that also. Thanks!

---

### Post by josephmills on 2011-04-25
ok lets make sure that everything is in order here could we see a ```
dmesg | grep -e oco -e wlan -e wifi -e eth1 -e hostap
``` ```
lsmod | host
``` and a ```
lsmod | grep orinoco 
``` and a ```
dmesg | grep orinoco 
```
also is your wifi password a wep or a wpa/wpa2?

---

### Post by ctyonahl on 2011-04-25
> **josephmills said:**
> ok lets make sure that everything is in order here could we see a ```
dmesg | grep -e oco -e wlan -e wifi -e eth1 -e hostap
``` ```
lsmod | host
``` and a ```
lsmod | grep orinoco 
``` and a ```
dmesg | grep orinoco 
```
also is your wifi password a wep or a wpa/wpa2?

Code #1

```
   0.063046] NET: Registered protocol family 16
[    0.114619] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.177325] NET: Registered protocol family 2
[    0.180732] NET: Registered protocol family 1
[    1.154985] NET: Registered protocol family 10
[    1.156088] NET: Registered protocol family 17
[   12.920122] NET: Registered protocol family 23
[   13.574747] hostap_pci: Registered netdevice wifi0
[   13.574757] wifi0: Original COR value: 0x0
[   13.815332] wifi0: NIC: id=0x8013 v1.0.0
[   13.820269] wifi0: PRI: id=0x15 v1.0.7
[   13.821655] wifi0: STA: id=0x1f v1.3.6
[   13.826734] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[   13.832396] [drm] Loading R100 Microcode
[   13.843312] wifi0: Intersil Prism2.5 PCI: mem=0xf8000000, irq=11
[   13.844975] wifi0: registered netdevice wlan0
[   14.540670] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[   14.540985] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.798078] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[   14.800619] wifi0: LinkStatus=2 (Disconnected)
[   14.800824] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  396.406578] prism2: wlan0: operating mode changed 2 -> 1
[  396.407376] wifi0: LinkStatus=2 (Disconnected)
[  396.407680] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  396.622840] wifi0: LinkStatus=1 (Connected)
[  397.631511] wifi0: LinkStatus=2 (Disconnected)
[  397.642296] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  397.654582] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[  397.654591] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
[  397.656182] wifi0: LinkStatus=2 (Disconnected)
[  397.682262] wifi0: LinkStatus=2 (Disconnected)
[  397.705290] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  398.036852] wifi0: LinkStatus=1 (Connected)
[  398.037156] wifi0: LinkStatus: BSSID=00:22:b0:c7:ba:17
[  398.037958] ADDRCONF(NETDEV_CHANGE): wifi0: link becomes ready
[  398.038737] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  408.176051] wlan0: no IPv6 routers present
```

Code #2
```
: host [-aCdlriTwv] [-c class] [-N ndots] [-t type] [-W time]
            [-R number] [-m flag] hostname [server]
       -a is equivalent to -v -t ANY
       -c specifies query class for non-IN data
       -C compares SOA records on authoritative nameservers
       -d is equivalent to -v
       -l lists all hosts in a domain, using AXFR
       -i IP6.INT reverse lookups
       -N changes the number of dots allowed before root lookup is done
       -r disables recursive processing
       -R specifies number of retries for UDP packets
       -s a SERVFAIL response should stop query
       -t specifies the query type
       -T enables TCP/IP mode
       -v enables verbose output
       -w specifies to wait forever for a reply
       -W specifies how long to wait for a reply
       -4 use IPv4 query transport only
       -6 use IPv6 query transport only
       -m set memory debugging flag (trace|record|usage)
```

Code #3 

Didn't get anything for lsmod | grep orinoco

Code #4 

Same as Code #3

My password is a 128-bit WEP key.

---

### Post by josephmills on 2011-04-25
```
[  408.176051] wlan0: no IPv6 routers present
``` are you tring to use wpa2? please take a good look at these links 
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=1260%3A3873+driver+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=1260%3A3873+driver+&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ctyonahl on 2011-04-25
What does that mean? :D Sorry, I'm such a noob!

---

### Post by josephmills on 2011-04-25
> **ctyonahl said:**
> What does that mean? :D Sorry, I'm such a noob!

IPV6 stands for internet protocol version 6. It is helps to connect to the internet. please take a look at this for ipv6
[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)
I think that n00bs are people that do not listen they think that they have got it all figured out and when looking for help they will not ask that many questions because they think that they all ready know the answer. kinda like a maocho man/women. But I don't know really. What I do know is that you are asking questions that need to be answered. anyhow any how I dont think that you are a n00b. I think you are awesome welcome to the forum by the way.

---

### Post by ctyonahl on 2011-04-25
yes. it looks like I'm using IPv6.

---

### Post by josephmills on 2011-04-25
yes you might be but your router is not set up for that. but frist you need to get your driver for your wireless up and running did you look at the googubuntu link? also when was the last time you updated and upgraded your system?

---

### Post by ctyonahl on 2011-04-25
I actually just installed Ubuntu yesterday! :D But I updated it right after the install. Everything *should* be up-to-date, but I will check again.

EDIT: Everything is up-to-date

---

### Post by josephmills on 2011-04-25
let make sure go to system-->addmin-->synaptic package manager then go to setting--> repositories and mke sure all are ticked see pic then close software sources and press the reload button in sysnaptic then close out of synaptic then open you terminal and type in ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade
``` then ```
sudo reboot 
```after rebooting you are 100% updated now that you are 100% go to system--admin-->additional drivers  is there any driver available to activate?

---

### Post by ctyonahl on 2011-04-25
Nope, sorry, no drivers are listed! :(

(btw, I'm going to be gone for a couple hours, but I'll check this thread again when I get back. Thanks for your time!)

---

### Post by frank604 on 2011-04-25
Hi OP,  you have two options:

1) Ensure that ubuntu is correctly loading the right driver for your wifi card
2) Use ndiswrapper to allow ubuntu to load the windows version of your wifi card

Often with so many variations of drivers, ubuntu loads the one that it thinks is the best one for your device; however this sometimes backfires and it is the incorrect driver.

I have googled around for you and put a lot of stars on the thread that I think will work best for you.

Just a FYI, conforming to option #1 as provided above, you will need to "blacklist" drivers from starting up.  This will disable ubuntu from ever loading them as long as they remain in the blacklist.  This is useful as then ubuntu will load the non-blacklsited driver, which is what you want.  

There seems to be 3 drivers for your chipset.  Orinco, hostap, and prism2 with "pci variants".  Follow the thread I've star'd below.  





Bibliography (please read these as they might shed some light, use caution in following other people's advice):

Solution was going towards ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=664586](http://ubuntuforums.org/showthread.php?t=664586)

Useful commands to use to check things out:
[http://ubuntuforums.org/showthread.php?t=1734727](http://ubuntuforums.org/showthread.php?t=1734727)

Solved thread for wpa + ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=630763](http://ubuntuforums.org/showthread.php?t=630763)

******This guy solved it by manually selecting the right driver for him and flashing his card:
[http://ubuntuforums.org/archive/index.php/t-606861.html](http://ubuntuforums.org/archive/index.php/t-606861.html)




EDIT: Oh yeah, start off with bare settings.  This means, turn off any password encryptions for the router first.  Try to connect, then enable WEP or WPA whichever you prefer.  This will eliminate driver/connectivity issues from encryption issues.

---

### Post by ctyonahl on 2011-04-26
OK, all of this is getting really confusing for me. After several attempts, I've decided to stop wasting time trying to figure it out, but I'm still open to other ideas (if you have any). Thanks for all of your help. I'll post here if I find anything new.

---

### Post by wolfen69 on 2011-04-26
> **ctyonahl said:**
> OK, all of this is getting really confusing for me. After several attempts, I've decided to stop wasting time trying to figure it out, but I'm still open to other ideas (if you have any). Thanks for all of your help. I'll post here if I find anything new.

At this point, I would probably just order a new USB wireless adaptor for $8 that is compatible with linux and call it a day. Btw, that's what I paid for mine that I use for my test installs and for the times I install win7 for customers. It works "out of the box" on everything. FYI, it's an Encore Electronics ENUWI-G2 802.11g

$8 seems like a pretty cheap fix, considering how much time you've spent trying to get it going. What's your time worth?

---

### Post by 3rdalbum on 2011-04-26
Since you can detect networks and connect, there's probably nothing wrong with your driver.

If Firefox can't find any websites, then you probably have a DNS problem. Some routers don't pass DNS information in a way that any non-Windows computers can understand.

This is a common problem, with an easy solution: [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

If it doesn't work then you can try a different adapter.

---

### Post by frank604 on 2011-04-26
> **3rdalbum said:**
> Since you can detect networks and connect, there's probably nothing wrong with your driver.

I've had similar issues in regards to connectivity with my RT2860 adapter.  Ubuntu was loading RT2860PCI instead of RT2860STA.  Both could detect the network, yet the sta can actually connect via WPA encryption.  However, the provided STA driver from Ubuntu was outdated and I needed to compile the latest STA driver from RT to get to N speed.  What I'm trying to get at is that with his adapter, people had similar issues as my RT adapter.  They resolved it by blacklisting the drivers that were not compatible, but were loaded as default.

---

### Post by BertN45 on 2011-04-26
I would switch of IPv6 for the wifi, it messed up my network too. First work with IPv4 only. 

Go network applet -> edit connections -> wireless ->  select the wifi network and press the edit button. On the IPv6 tab choose method: "Ignore".

---

### Post by ctyonahl on 2011-04-27
> **wolfen69 said:**
> At this point, I would probably just order a new USB wireless adaptor for $8 that is compatible with linux and call it a day. Btw, that's what I paid for mine that I use for my test installs and for the times I install win7 for customers. It works "out of the box" on everything. FYI, it's an Encore Electronics ENUWI-G2 802.11g

$8 seems like a pretty cheap fix, considering how much time you've spent trying to get it going. What's your time worth?

Heh, my time isn't worth much (I'm a student):D. Thanks for the tip!

---

### Post by ctyonahl on 2011-04-27
It looks like it's a problem with my wireless router. Thank's for your help, everyone!

---

### Post by jthirt on 2011-04-30
I don't think so!

I have numerous ubuntu systems working at home using wireless and the one that doesn't, since 10.04 is my IBM A31 with the same "Intersil Corporation Prism 2.5 Wavelan" network controler. 

It lists all the available wifis (I have two setup at home with different routers) but it won't connect any. 

I'm curious to know if anyone managed to make this IBM A31 model to work properly with wifi.

Cheers.

---

### Post by mightyiam on 2011-10-30
To solve this with this prism2 card I upgraded the firmware on the card to 1.8.2 using this guide:
[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

---

