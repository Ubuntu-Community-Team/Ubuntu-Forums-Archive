---
title: "wireless option has disappeared"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by ni ni on 2010-07-26
hello all,

in ubuntu I have no wireless option at all.  I used to with no problems.  now i only have "wired network" on my taskbar. 

The wireless switch is on because the light is lit on the outside of the laptop.

I HAVE the proprietary driver installed.

Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based

[HTML]niamh@niamh-laptop:~$ lspci | grep -i net
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
niamh@niamh-laptop:~$ [/HTML]

I'm such a beginner so please be kind (as everyone here always is xxxx)

thank you xxxx :KS:KS:KS:KS

---

### Post by P4man on 2010-07-26
Right click the network manager icon top right, and see if wireless is enabled. If it is; or rather; its not listed; can you also provide the output of
```

lsusb
```

---

### Post by ni ni on 2010-07-26
output of lsusb:
```
niamh@niamh-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
niamh@niamh-laptop:~$
```

I don't have a wireless option!

---

### Post by petrus250 on 2010-07-26
I had a similar problem but I, after hours of google, simply reinstalled ubuntu, sorry

---

### Post by ni ni on 2010-07-26
oh dear i hope i won't have to do that!:(:(

---

### Post by P4man on 2010-07-26
Weird. It sees no wifi card at all.

Can we see the full output of lspci (so whithout the grep) ?

Also; I assume you already tried toggling the hardware switch, or even leaving it OFF and running both lspci and lsusb to see if it shows up? 

if you have a livecd or usb stick, can you boot that and see if it shows up?

Last idea: perhaps it became unseated? if its an internal mini-PCI card it may just need to be plugged in properly again. You'll have to unscrew the plastic cover at the bottom (most likely).

---

### Post by ni ni on 2010-07-26
lspci: (I don't know what grep is )

```
niamh@niamh-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
niamh@niamh-laptop:~$ 

```

Yes I have tried toggling the Hardware switch but tbh, i won't know what to look for in those commands...

Yes, i may have to open her up and see does anything look loose.

Thanks for all the help so far :KS:KS:KS

---

### Post by P4man on 2010-07-26
> **ni ni said:**
> lspci: (I don't know what grep is ) 

grep searches for a string and filters the output. The first output you gave showed only the lines that contained "net". What you gave now is the full output that I wanted to see. Still no sign of a wifi card though.

> 
Yes I have tried toggling the Hardware switch but tbh, i won't know what to look for in those commands...

If anything extra shows up, that would be all you need to know :). It will most likely contain something like "wireless network controller". It would show up in lspci if its a (mini) PCI device or a PC card (those credit card sized cards you can slot in most laptops) and in lsusb if its an USB card (some cards are internally connected to the USB bus). 

That said; when did your wifi stop working? Did you install or uninstall something; or ran updates; or did it just stop for no reason? Do you have any idea of what sort of wifi card this is and can you also give us the brand and type of laptop?

---

### Post by ni ni on 2010-07-27
it's a fujitsu siemens amilo L7310GW.

I'm sorry, I've no idea what kind of wireless card it is.  :(

It stopped after a load of updates in March as the laptop had been off since that January.  and another thing (tho i don't know is it just a new Ubuntu thing) was that I used always to have to enter the default keyring password, after those updates i wasn't asked for it anymore, and the wireless was gone.  (Ubuntu always goes directly to my desktop, i never "Log in" as such.

---

### Post by P4man on 2010-07-27
Googling your laptop type I came across this:

[http://www.mernin.com/blog/?p=67](http://www.mernin.com/blog/?p=67)

Wont hurt to try Fn+F2 :)

If that doesnt help, I dont think you have mentioned which version of ubuntu you are using?

---

### Post by ni ni on 2010-07-27
I'm using Lucid Lynx 10.04.

LOL that Fn + F2 trick didn't work!

---

