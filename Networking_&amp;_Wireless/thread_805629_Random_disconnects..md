---
title: "Random disconnects."
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Poomerio on 2008-05-24
So yeah, I'd be minding my own business, playing World of Warcraft on my Ubuntu Hardy 8.04 setup, when I'd randomly get disconnected. I can't connect again until a reboot, and it's bugging the crap out of me.
I'm using a Belkin G USB Adapter to connect to a BT Voyager 2100 box.
Worked fine with Windows, and I want answers.

Thanks,
 - Poomie

---

### Post by chili555 on 2008-05-24
> I want answers.So, yeah, may we please see:```
sudo iwconfig
```Run it, please, while you are actually connected. We'll troubleshoot from there.

---

### Post by Poomerio on 2008-05-24
Sure thing.

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"BTVOYAGER2100-33"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:11:F5:1E:08:33   
          Bit Rate=24 Mb/s   
          Encryption key:10C7-2B4E-AEB3-1FD9-9D7B-B530-625B-C437-83F6-6C17-B199-EA74-CF93-0BF6-58C9-05CA   Security mode:open
          Link Quality=94/100  Signal level=29/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

 - Poomie

---

### Post by Sense on 2008-05-24
This is probably a bug in network manager. Can you please look at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) if this is already reported? If it isn't please report it and the Ubuntu Bugsquad will take it from there.

---

### Post by mapes12 on 2008-05-24
Please could we see the output to:

```
sudo lshw -C network 
```

Did you use ndiswrapper to configure a wifi drive or did your usb wifi work when you installed Ubuntu?

And please could you let me know the exact model number for your wifi USB device.

---

### Post by Poomerio on 2008-05-24
```
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:76:41:fc:57
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:8c:a6:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11b/g

```

I'm using a "BELKIN F5D7050UK WIRELESS 54G USB NETWORKING ADAPTER" which worked out of the box, so to speak.

 - Poomie

---

### Post by mapes12 on 2008-05-25
Looks like Ubuntu hooks up OK to your wifi adapter so can't see where the problem is there, Having dug around some more there are others saying the card works and others having problems. The card isn't listed as supported:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

but other models close to it are listed but note the variation in the range of chipsets. This may be the problem.

My advice..........get yourself a fully supported card. I got a Comatrend RT2500 and all my problems are over. Like you, I have a BTHomehub router wireless network here. I got my card from these guys for £10:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

:guitar:

---

### Post by Poomerio on 2008-05-25
Great, thanks.
I'll try and get my hands on a supported adapter sometime this week, then I'll update the threat title.

You guys have been great :)

 - Poomie

---

### Post by Poomerio on 2008-05-28
Good news. My new adapter arrived today, and it's working wonderfully.
Edited the title to reflect this.

 - Poomie

---

### Post by mapes12 on 2008-05-28
I read on a Linux Guru site a while ago that if you want to keep your sanity you just sometimes, just sometimes, have to help the kernel out and give him the hardware he knows how to work with................

Well done and good luck with Ubuntu.

:guitar:

---

### Post by Poomerio on 2008-05-30
Hmm. Yesterday, I started getting the same problems.
I'm sure it isn't a hardware issue now. I'm not even using the same USB extension that I had.
Perhaps an Ubuntu bug?

 - Poomie

---

### Post by Poomerio on 2008-05-30
These disconnections are starting to really do my head in.
Countless times today I have had to reboot, just to finish watching that 1 youtube video, or just to be able to get Dash for my kitty in WOW.
Bump too, btw.

 - Poomie

---

### Post by Poomerio on 2008-05-31
C'mon, can I get a little more help with this?
These disconnections are starting to bug the hell out of me :(

 - Poomie

---

### Post by ayenack on 2008-05-31
How long is it before the disconnect? If I remember correctly there's a bug in the kernel that causes the USB bus to reset/disconnect after a certain amount of time. In my experience it effects different devices in different ways. This could be your problem.

The problem could also be with network manager. I have a D-Link USB WIFI dongle (DWL-G122 rev C1) that was totally unreliable until I removed network-manager and network-manager-gnome. It's now about 90% reliable. Not perfect but far better. The symptoms were the same as you have described needing a reboot to get things up again.

---

### Post by Poomerio on 2008-05-31
The times that it disconnects appear to be random. Sometimes a few seconds, or a few hours. But when it does disconnect, the USB device does appear to stop working (the light not coming on), and it seems to happen in clusters, i.e. it will disconnect once, then a few more times in a short timeframe. Then I get frustrated and just grab my guitar or something.

 - Poomie

---

### Post by Poomerio on 2008-06-15
Problem still unsolved.
If I leave my computer on after it disconnects, then about 10 minutes later it'll reconnect.
Little help here?

---

### Post by Poomerio on 2008-06-16
Anything? =/
This is getting really bad.

---

### Post by LeGollemux on 2008-06-16
I have the same problem on two different machines. One has a broadcom card and the other an intel.

To reconnect I type "iwconfig wlan0 essid MYLAN" then "sudo /etc/init.d/networking restart". 

I found that by opening a terminal window and pinging my gateway, and leaving the pinging to just tick away (minimized of course) I was not being disconnected.

Give it a try. perhaps it works for you.

---

### Post by Poomerio on 2008-06-24
Edit: My bad.

---

