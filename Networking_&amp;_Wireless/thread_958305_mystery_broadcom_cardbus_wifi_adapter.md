---
title: "mystery broadcom cardbus wifi adapter"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2008-10-25
Hello folks

I've come upon a cardbus wifi adapter that I'm trying to get going in 8.04.1

Plugged in I get nothing, except the two power and link leds inside glow very faintly

'lspci -v | less' gives me this about the card...


```
03:00.0 Class 1800: Broadcom Corporation Unknown device 0018 (rev 03) (prog-if 18)
        Subsystem: Unknown device 0018:0018
        Flags: fast devsel, IRQ 11
        I/O ports at 4000 [disabled] [size=256]
        Capabilities: <access denied>

03:00.3 Class 1800: Broadcom Corporation Unknown device 0018 (rev 03) (prog-if 18)
        Subsystem: Unknown device 0018:0018
        Flags: fast devsel, IRQ 11
        I/O ports at 4400 [disabled] [size=256]
        Capabilities: <access denied>

(END) 


```

The 0018 device tag makes me think it's not the well-covered 43xx series, so does anyone know what I've got here? Or better, how to make it work?? Seems also not to work under Interpid RC live, so the new broadcom drivers may not help

Many thanks indeed
Roger

---

### Post by Ayuthia on 2008-10-25
Can you also post the results of lspci -nn?

---

### Post by rogerdean on 2008-10-25
Hiya. Thanks for taking an interest! The whole thing is...


```
ordban@ordban-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
03:00.0 Class [1800]: Broadcom Corporation Device [14e4:0018] (rev 03)
03:00.3 Class [1800]: Broadcom Corporation Device [14e4:0018] (rev 03)
ordban@ordban-laptop:~$ 

```


I think that's the card down the bottom...

Cheers
Roger

---

### Post by Ayuthia on 2008-10-25
Wow!  I have never seen this card before!  Can you see if lshw -C network shows anything?  Right now, I am not for sure about what driver to use for it.  Where did you get this card and when?

---

### Post by rogerdean on 2008-10-25
```
ordban@ordban-laptop:~$ sudo lshw -C network
[sudo] password for ordban: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:8b:d4:a2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.8 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:90:a4:2a:35:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ordban@ordban-laptop:~$ 

```

But I think that's the LAN only, right? 

Well, glad it's interesting at least! I got this on eBay UK last week, from listing [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=190261616830](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=190261616830)

---

### Post by Ayuthia on 2008-10-25
> **rogerdean said:**
> ```
ordban@ordban-laptop:~$ sudo lshw -C network
[sudo] password for ordban: 
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:8b:d4:a2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.8 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:90:a4:2a:35:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ordban@ordban-laptop:~$ 

```

But I think that's the LAN only, right? 

Well, glad it's interesting at least! I got this on eBay UK last week, from listing [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=190261616830](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=190261616830)
The first is definitely for your LAN, but the second one I am not too sure about.  The logical name is pan0.  Usually it is an eth1, wlan0, or ath0.  Acoording to this [site]("http://affix.sourceforge.net/affix-doc/c1051.html"), it is a Personal Area Network which is for bluetooth.  That also does not sound like the card that we are needing.

One other place to try is lsusb.  Can you post those results?  Hopefully that will show something else that will be helpful.  If not, do you have any Windows XP drivers (or anything else that is not Vista) for the card?  You might need to try ndiswrapper to make it work.  Vista drivers are not supported in ndiswrapper at this time.

---

### Post by rogerdean on 2008-10-25
```
ordban@ordban-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ordban@ordban-laptop:~$ 
```

There's no bluetooth or anything else on this machine, an old Thinkpad T40 without even an internal wireless card. As for WinXP drivers, and here's where it gets fun, they did include a CD but...

1) XP installation program on CD did not recognise the card, saying that the driver was incompatible (or somesuch)

2) The .inf on the CD did not allow mintwifi (a GUI for ndiswrapper I think) on Ubuntu to pick up the card

so on top of everything else I think the CD was wrong...

---

### Post by Ayuthia on 2008-10-25
Sorry, I don't think that I can help you any further.  Hopefully someone else will be able to help.  I have never seen this chipset before.

---

### Post by rogerdean on 2008-10-25
Hey thanks for trying Ayuthia, much appreciated.

---

### Post by rogerdean on 2008-10-25
Ok, I've peeled off a label and found another underneath, naming the card as a Sagem WPCB-165G. Does anyone know about this? Google results seem all to be in French...

---

