---
title: "Feisty &amp; Linksys wusb54gc"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Bad_Byte on 2007-04-19
Feisty sees the usb wifi but it does not manage to get it to work. With edgy [Albrecht Gebhardt's page]("http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/") worked, now with feisty that breaks down at compile time (Error 2). I have also tried the sticky wusb54gc thread and still nothing.

Any help would be nice.

---

### Post by deuber on 2007-04-28
I clicked through enough links to find a forum posting that got me to do the following (and for 
the life of me, I can't find the posting again to reference, so thanks to whoever posted it)...

Unplug your WUSB54GC device.

sudo bash
lsmod | grep rt

That should list something like rt73usb and another rt2x00lib module.  Put both of those modules in /etc/modprobe.d/blacklist 

as such: 

blacklist rt2x00lib
blacklist rt73usb

Save that.  Then run:

ndiswrapper -l

If you don't have any drivers installed, copy the drivers folder from the cdrom that came with your device onto your hard drive.  Cd into that folder and run:

ndiswrapper -i rt73.inf
ndiswrapper -l

the second command should who the new driver installed. 

Plug your device in and run:

lsusb

You should see your device.  Run:

lsmod | grep ndis

You should see the ndiswrapper module loaded. Run:

ndiswrapper -l

Now, you should see your driver and your device. 

Unplug your device.  Reboot your machine. Login.  Plug your device in.

It will come up and you will be working (hopefully).  I was.

Ubuntu and Ubuntu forums rock!

Bobd

---

### Post by fluteflute on 2007-04-30
Did as you said. I can see available networks but cannot connect. I am running a 64ibit WEP network.

---

### Post by p110011 on 2007-05-02
Is broadcast ssid on in your router settings? Since Feisty install I have to have mine on.

---

### Post by fluteflute on 2007-05-02
> **p110011 said:**
> Is broadcast ssid on in your router settings? Since Feisty install I have to have mine on.

It was already on. (I can see my netowork in Fiesty but just can't connect).

---

### Post by cwk on 2007-05-02
After spending all last weekend trying to get my wireless adapter to work, I put Ubuntu aside until I came across deubner's instructions. 

I did a clean install and followed his instructions to the letter, but it's even worse than before (when I could see the hardware and the network, just couldn't connect). Now I see my hardware in the device manager but not in the network settings. ndiswrapper -l shows:

rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)

What do I do now? How come Ubuntu sees my adapter in some places, but not in others? Why don't I see my network anymore? 

I have to say I'm pretty frustrated by the situation. I want to switch over to Ubuntu, but this network stuff is total crap. This is exactly what happened when I tried Dapper - a week of late nights reading forums and screwing around in the terminal only to end up no closer than I started, and headed back to XP. Can't anyone come up with a set of instructions that work?

---

### Post by cwk on 2007-05-02
Christ, this is awful. Nothing I do makes any difference whatsoever.

I give up. Someone tell me device that will "just work." I have some credit at microcenter.

---

### Post by p110011 on 2007-05-02
> **cwk said:**
> Christ, this is awful. Nothing I do makes any difference whatsoever.

I give up. Someone tell me device that will "just work." I have some credit at microcenter.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by p110011 on 2007-05-04
[QUOTE=deuber;2554302]I clicked through enough links to find a forum posting that got me to do the following (and for 
the life of me, I can't find the posting again to reference, so thanks to whoever posted it)...

Unplug your WUSB54GC device.

sudo bash
lsmod | grep rt

That should list something like rt73usb and another rt2x00lib module.  Put both of those modules in /etc/modprobe.d/blacklist 

as such: 

blacklist rt2x00lib
blacklist rt73usb

Save that.  Then run:

ndiswrapper -l

After that command I get

root@hotdog:~# lsmod | grep rt
rt73                  220544  0 
rt73usb                33536  0 
rt2x00lib              11904  1 rt73usb
crc_itu_t               3072  1 rt73usb
mac80211              175364  5 rt73usb,rt2x00lib,rc80211_simple,prism54usb,prism54common
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
agpgart                35400  2 drm,amd64_agp
usbcore               134280  8 rt73,rt73usb,prism54usb,usbhid,xpad,ohci_hcd,ehci_hcd
root@hotdog:~# ndiswrapper -l
rt73 : invalid driver!

should that driver be in there?

---

### Post by tbannon on 2008-02-02
Wanted to bump this with some key search words I've been using in search of solution  (Im a nub so if I break any rules plz forgive)

Spent weeks trying to get wireless working properly.

I was experiencing LOW WIRELESS SIGNAL AFTER RESTART

I've finally fixed the problem with the advice below on 7.10 Gutsy with the Linksys compact Wireless WUSB54GC.

Man, it's a pain in the ... for a noob to get Ubuntu working right, but once you get there...  :guitar:

> **deuber said:**
> I clicked through enough links to find a forum posting that got me to do the following (and for 
the life of me, I can't find the posting again to reference, so thanks to whoever posted it)...

Unplug your WUSB54GC device.

sudo bash
lsmod | grep rt

That should list something like rt73usb and another rt2x00lib module.  Put both of those modules in /etc/modprobe.d/blacklist 

as such: 

blacklist rt2x00lib
blacklist rt73usb

Save that.  Then run:

ndiswrapper -l

If you don't have any drivers installed, copy the drivers folder from the cdrom that came with your device onto your hard drive.  Cd into that folder and run:

ndiswrapper -i rt73.inf
ndiswrapper -l

the second command should who the new driver installed. 

Plug your device in and run:

lsusb

You should see your device.  Run:

lsmod | grep ndis

You should see the ndiswrapper module loaded. Run:

ndiswrapper -l

Now, you should see your driver and your device. 

Unplug your device.  Reboot your machine. Login.  Plug your device in.

It will come up and you will be working (hopefully).  I was.

Ubuntu and Ubuntu forums rock!

Bobd

---

