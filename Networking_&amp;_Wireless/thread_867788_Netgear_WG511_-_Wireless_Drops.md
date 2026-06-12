---
title: "Netgear WG511 - Wireless Drops"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Michelexub on 2008-07-23
Hi.
I have installed Xubuntu Hardy Heron on Laptop Acer Aspire 1312.
I use a PCMCIA NETGEAR WIRELESS CARD WG511 (v1).

When I boot, Linux recognises the card and I can connect without any problem to my network (WPA).

The issue is that after few minutes (they could be 5 or 20) the connection drops and when it tries to reconnect, even if the signal is strong, the connection fails.

Weirdly enough, if I try to connect again, it cannot find any wirelss network around.

Note that I had the same issue changing to a WEP network.

I did not use ndiswrapper to install the drivers, since *buntu recognised the card without any problem.

Thanks.
Michele

---

### Post by chili555 on 2008-07-23
Please see post #2 and following. I think the module to blacklist now is *p54pci.*

[http://ubuntuforums.org/showthread.php?t=375182](http://ubuntuforums.org/showthread.php?t=375182)

---

### Post by Michelexub on 2008-07-23
Hi chili,
I have followed the posts but had some problems.

First, I have installed ndiswrapper and installed the windows drivers (XP).

Then I blacklisted p54pci, since prism54 is blacklisted by default.

But when I reboot, the card is not even recognised.

Is it because I have installed the drivers using ndiswrapper in the wrong way?
Or because I should have done something else afterward?

Any suggestion is appreciated.

Michele

---

### Post by chili555 on 2008-07-24
Is it recognized after you do:```
sudo modprobe ndiswrapper
```Also, what is the output of:```
sudo ndiswrapper -l
```Thanks.

---

### Post by Michelexub on 2008-07-24
Hi.
When I do
sudo modprobe ndiswrapper
nothing happens.

See below:
michele@michele-laptop:~$ sudo modprobe ndiswrapper
michele@michele-laptop:~$ 

If I do sudo ndiswrapper then:
michele@michele-laptop:~$ sudo ndiswrapper -l
netwag51 : driver installed

Do I have to blacklist p54pci and try the same command?

Thanks.
Michele

---

### Post by chili555 on 2008-07-24
> Do I have to blacklist p54pci and try the same command?I thought you already did.

When you modprobe, or many other commands, for that matter, and nothing happens, it simply means, roughly, "OK, I did as you commanded and have no errors or warnings to report. What next?" I am a little mystified that *ndiswrapper -l* doesn't report 'device present.' May I please see, with the card inserted, of course:```
sudo lshw -C network
iwconfig
```Thanks.

---

### Post by Michelexub on 2008-07-25
Hi.
I have blacklisted p54pci and execute those 2 commands:
sudo modprobe ndiswrapper
nothing happens.

sudo ndiswrapper -l
netwag51 : driver installed

If I do:
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:22:2d:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.2 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10

and finally:
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

Any idea?
I wonder if the driver is not the correct one.
But I am pretty sure that my card is the version 1 and that I got the correct drivers from the Netgear website.

Michele

---

### Post by chili555 on 2008-07-25
Did you follow the procedure in the forum post I referred to above? I think you actually want *netwg511.inf.*> I wonder if the driver is not the correct one.Me, too.> I am pretty sure that my card is the version 1Me, too.

---

### Post by Michelexub on 2008-07-25
Hi chili,
I read again your post and I believe that I followed your instructions, making few amendments given that prism54 is no longer used and that my card is not v300 but version 1.1

I went to:
[http://kbserver.netgear.com/products/WG511v1.asp](http://kbserver.netgear.com/products/WG511v1.asp)
and downloaded version 1.1
Is this my mistake?

Should I have downloaded v3.0 instead?

Now I have a doubt that I got confused between card version and drivers version :confused:

Michele

---

### Post by chili555 on 2008-07-25
> Should I have downloaded v3.0 instead?Yes. This is version 3.0, the latest, for the WG511v1 card.> I got confused between card version and drivers versionIndeed. I have made these mistakes plenty of times myself. I wonder why the manufacturers don't remove the old stuff when they post the new stuff.

---

### Post by Michelexub on 2008-07-30
Hi Chili,
using the v3 drivers I have got the card working.
Still have to test it fully (for a long time) but it seems to be fine.
The only drawback is that I had to change the wireless security to WEP instead of WAP.
If you find a way to get the card working using WAP please let me know.

Thanks for your help.
Michele

---

### Post by Michelexub on 2008-08-06
Hi chili.
I think that I started celebrating a bit too early.

I have the same issue as before (or very similar).

When I boot xubuntu then login, everything is fine.

Xubuntu see the card, the card see the wireless network, then the card connects to it and I'm happy surfing.

After 15/20 minutes (or less!) the connection drops and the network manager try to connect again to the same wireless network.
It asks for the passphrase and even if I type the correct passphrase, it keeps trying to connect.
If I look at the signal, it is strong and the card can see it.

I'm puzzled.
Any idea what I could do about that (apart from kicking my laptop)?.

Thanks.
Michele

---

