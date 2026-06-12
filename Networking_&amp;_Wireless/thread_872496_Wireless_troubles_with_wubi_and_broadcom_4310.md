---
title: "Wireless troubles with wubi and broadcom 4310"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by mfrag on 2008-07-28
Howdy folks.  Could use a little help with setting up my wireless.  I just went through a wubi installation on both my desktop and my laptop.  I have my wireless setup just fine with wubi on my desktop.  The laptop is another story.  I've spent several hours looking at posts and have tried several suggestions to no avail.  A wired ethernet connection works fine on the laptop.  The little WiFi led light is on which is good news I think.

My laptop has wubi installed on XP.  I have a dell inspiron 1520.  As near as I can tell my wireless card is a broadcom 4310. Here is output from various commands.  I would appreciate any help you can give.

ifconfig gives me this:

eth0      Link encap:Ethernet  HWaddr 00:1d:09:d9:fb:dd  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fed9:fbdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11864529 (11.3 MB)  TX bytes:1207496 (1.1 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:16:44:be:c5:56  
          inet6 addr: fe80::216:44ff:febe:c556/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:23603
          TX packets:163 errors:68 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:24461 (23.8 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89739 (87.6 KB)  TX bytes:89739 (87.6 KB)

###############################################################

sudo lshw -C network gives me this:
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:be:c5:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:d9:fb:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.102 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

################################################################

lspci -nn | grep 14e4 gives me:

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)


Thanks in advance for any help!

---

### Post by mfrag on 2008-07-28
It appears eth1 is my wireless card.  So I ran:

sudo ifup eth1

and got the following ouput

There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:44:be:c5:56
Sending on   LPF/eth1/00:16:44:be:c5:56
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Now ifconfig produces, in addition to what it produced above, the following:

eth1:avahi Link encap:Ethernet  HWaddr 00:16:44:be:c5:56  
          inet addr:169.254.7.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 

However, I still can't get the internet without the landline...

---

### Post by Ayuthia on 2008-07-28
You might want to check and see that b43 is not running:
```
lsmod|grep b43
```
if it is out there, you will need to remove the module:
```
sudo modprobe -r b43 b44 ssb wl
sudo depmod -ae 
sudo modprobe wl
sudo modprobe b44
sudo ifconfig eth1 up
sudo iwlist scan
```
The commands above actually will remove the b43 module and the b44 module (your wired connection) and then load the wl module (your wireless) and then load the b44 module back.  The removal of the b44 module is more of a precaution because sometimes the ssb module interferes with other wireless modules.  

If you are able to see wireless sites, you can try to connect.  If things connect, you can blacklist the b43 module:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
```

There is a good chance that you might not be able to connect if you have encryption set on your router.  I have not seen any 14e4:4315 chipsets have encryption working with the wl module yet.  I think some have gotten encryption to work with ndiswrapper though, but I don't recall the Windows driver that was used to make it work.

---

### Post by mfrag on 2008-07-28
Thanks for your help.  I ran lsmod|grep b43 and got no output.  I went ahead and ran your code anyway and after running iwlist scan I see different wireless networks pop up, including mine.  So, I guess this is good news.  Apparently the wireless card is working, I just can't connect to the router.  I have no security in place whatsoever at the moment and still can't connect.

Maybe the problem is I don't know how to set up the wireless connection  with the router properly?  On my desktop, when I open up "network" from "system -> administration," I enter the ESSID and leave the password blank since I'm checking this with no security for now and then enable dhcp.  Things work just fine on the desktop.  I assumed the same would work on the laptop, but that's not the case.  I assumed I didn't even have the wireless card up and running since I didn't see any wlan0's when I ran ifconfig. Why is it that my wireless card is coming up as eth1 and not wlan0?  

Since I get the following output from "sudo ifup eth1"

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:44:be:c5:56
Sending on   LPF/eth1/00:16:44:be:c5:56
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I assume the wireless card and the router cannot talk to one another.
Or maybe the router isn't talking to the wireless card.  Any ideas on how to get them to talk?

Thanks again for any help.  I new to ubuntu.  I've been using suse 10.0 for sometime now at work.  When I heard of wubi I couldn't wait to try it.  My wife didn't feel safe without her windows and didn't want the dual boot option either.  I convinced her that that with wubi we could just uninstall through windows if she isn't happy with it.  So far everything works like a charm and I'm glad to be using linux at home.  Now if I can just get this wireless connection on the laptop working, everything will be perfect.  I'm really impressed with ubuntu so far.  Every, and I mean every application I use was found in the package manager.  I use a lot of applications that I have to compile myself and update myself at work.  texlive and gap4.4.10 for instance are not supported by suse.  I may have to change things at work as well.

Again, thanks for any help.

---

### Post by Ayuthia on 2008-07-28
> **mfrag said:**
> Thanks for your help.  I ran lsmod|grep b43 and got no output.  I went ahead and ran your code anyway and after running iwlist scan I see different wireless networks pop up, including mine.  So, I guess this is good news.  Apparently the wireless card is working, I just can't connect to the router.  I have no security in place whatsoever at the moment and still can't connect.

Maybe the problem is I don't know how to set up the wireless connection  with the router properly?  On my desktop, when I open up "network" from "system -> administration," I enter the ESSID and leave the password blank since I'm checking this with no security for now and then enable dhcp.  Things work just fine on the desktop.  I assumed the same would work on the laptop, but that's not the case.  I assumed I didn't even have the wireless card up and running since I didn't see any wlan0's when I ran ifconfig. Why is it that my wireless card is coming up as eth1 and not wlan0?  

Since I get the following output from "sudo ifup eth1"

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:44:be:c5:56
Sending on   LPF/eth1/00:16:44:be:c5:56
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I assume the wireless card and the router cannot talk to one another.
Or maybe the router isn't talking to the wireless card.  Any ideas on how to get them to talk?

Thanks again for any help.  I new to ubuntu.  I've been using suse 10.0 for sometime now at work.  When I heard of wubi I couldn't wait to try it.  My wife didn't feel safe without her windows and didn't want the dual boot option either.  I convinced her that that with wubi we could just uninstall through windows if she isn't happy with it.  So far everything works like a charm and I'm glad to be using linux at home.  Now if I can just get this wireless connection on the laptop working, everything will be perfect.  I'm really impressed with ubuntu so far.  Every, and I mean every application I use was found in the package manager.  I use a lot of applications that I have to compile myself and update myself at work.  texlive and gap4.4.10 for instance are not supported by suse.  I may have to change things at work as well.

Again, thanks for any help.

You might try the following and see if it makes a difference or not:
```
sudo dhclient -r eth1
sudo iwconfig eth1 essid the-essid
sudo dhclient eth1

```
Just replace the-essid with the essid of the router.

Ubuntu is nice that it has a ton of programs available.  As for me, I have converted almost all my computers to Linux.  I do keep Windows on them mainly for BIOS updates but that is about the only time I really go into Windows.  My wife prefers Windows over Linux mainly because that is what she has only used.  She is slowly getting used to Linux though.

---

### Post by mfrag on 2008-07-28
Thanks for trying to help Ayuthia.  I now have it fixed.

After stumbling around for a couple of days now with this I finally figured out what I was doing wrong.  I tried following the steps here

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

but it didn't work at first.  The reason why was the wl module was running and (maybe?) preventing the steps from working correctly. I needed to run

```
sudo rmmod wl
```

to remove the wl module or turn it off.  This caused my "Wifi" led light to shut off.  But after going to

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) and going through

through steps 1, 2e (since I have 4310), 3, the "Hardy bug Fix step", and lastly the "Making if permanent" step, things finally work.  eth1 was somehow removed and replaced by wlan0 and I could view wireless networks up in the corner of the screen.  

Now for a question.  Why did I need to go through all this?  Is there a reason why the ubuntu folks (I not complaining, just asking) have the wl module running from the get go.  It does get the wireless card running, but apparently can't connect to anything.  Apparently several people with broadcom cards need to go through these crazy steps to get their cards to work.

Is this because ndiswrapper, which I think is what I'm using to get this to work, uses the windows drivers (I think this is what is happening) and it is somehow a No-No to have a linux distro setup to have hardware work with windows drivers?

---

### Post by Ayuthia on 2008-07-29
> **mfrag said:**
> 

Now for a question.  Why did I need to go through all this?  Is there a reason why the ubuntu folks (I not complaining, just asking) have the wl module running from the get go.  It does get the wireless card running, but apparently can't connect to anything.  Apparently several people with broadcom cards need to go through these crazy steps to get their cards to work.

Is this because ndiswrapper, which I think is what I'm using to get this to work, uses the windows drivers (I think this is what is happening) and it is somehow a No-No to have a linux distro setup to have hardware work with windows drivers?

Why use wl first?  Well, it is the driver that Broadcom has made special for this card.  The b43/b43legacy drivers are made by other developers that are not with Broadcom and they have not done any work with this specific card.  Broadcom just released the driver recently and the Ubuntu developers added it to linux-restricted-modules.  Some people have been able to get the driver to work, but it has only been with unencrypted networks, but more have been successful with ndiswrapper.

To be fair about this, it is a new release from Broadcom so I am sure that it will improve over time.  Also, there could be other issues that are affecting the driver to connect with the router.  It seems that there has been some problems with network manager also that has caused some grief.

Ubuntu can't really use ndiswrapper with the windows drivers because the drivers are proprietary so they cannot be included.  In order to use the particular windows driver, you have to agree to the terms from the place where you get the driver.

---

### Post by mfrag on 2008-07-29
> Why use wl first? Well, it is the driver that Broadcom has made special for this card. The b43/b43legacy drivers are made by other developers that are not with Broadcom and they have not done any work with this specific card. Broadcom just released the driver recently and the Ubuntu developers added it to linux-restricted-modules. Some people have been able to get the driver to work, but it has only been with unencrypted networks, but more have been successful with ndiswrapper.

To be fair about this, it is a new release from Broadcom so I am sure that it will improve over time. Also, there could be other issues that are affecting the driver to connect with the router. It seems that there has been some problems with network manager also that has caused some grief.

Ubuntu can't really use ndiswrapper with the windows drivers because the drivers are proprietary so they cannot be included. In order to use the particular windows driver, you have to agree to the terms from the place where you get the driver.

Oh, that makes sense.  Well I would rather use the wl module since it is what is supported.  On my next reinstall or upgrade or whatever, I'll have to deal with wl again, right?  I'll hunt for what folks have done to get wl to work.  Most of my searches centered around the keywords broadcom, wubi wireless, dell wireless, and such.  Ndiswrapper kept popping up in nearly every post so I figured this was the way to go.  Hey, it does work.  It would be nice to have wl running though I guess.

Thanks for the discussion.

---

### Post by Ayuthia on 2008-07-29
> **mfrag said:**
> Oh, that makes sense.  Well I would rather use the wl module since it is what is supported.  On my next reinstall or upgrade or whatever, I'll have to deal with wl again, right?  I'll hunt for what folks have done to get wl to work.  Most of my searches centered around the keywords broadcom, wubi wireless, dell wireless, and such.  Ndiswrapper kept popping up in nearly every post so I figured this was the way to go.  Hey, it does work.  It would be nice to have wl running though I guess.

Thanks for the discussion.
Another thing that you can do is also check and see when there is an update to the Broadcom driver.  Here is a link to updates:
[http://feeds.ubuntu-nl.org/HardyChanges](http://feeds.ubuntu-nl.org/HardyChanges)
The changes will appear in hardy-proposed first.  After a few days or so, it gets moved over to the regular release.  Just look for the updates under linux-restricted-modules.

---

