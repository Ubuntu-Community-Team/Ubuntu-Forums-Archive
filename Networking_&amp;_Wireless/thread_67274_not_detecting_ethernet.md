---
title: "not detecting ethernet"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by vr04 on 2005-09-19
hi all, i'm trying to configure my old machine to connect to the internet, but the ethernet device doesn't get recognized automatically.

dmesg |grep eth0 gives me the following:

Digital DS21143 Tulip rev 65 at 00012000, 00:50:8B:30FD:78 IRQ 11

i don't think it matters much, but my cable modem is a toshiba pcx2500, and works with my newer pc without a hitch.

any help would be greatly appreciated. thanks!

---

### Post by OwenH on 2005-09-20
does your cable modem connect direct to your PC?

and can you post the output from 
```
ifup eth0
```
and 
```
ifdown eth0
```

---

### Post by vr04 on 2005-09-20
Owen,

Thanks for the response. Yes, my computer is directly connected to the cable modem.

Here's the output:

```
vr@avenger:~$ sudo ifup eth0
ifup: interface eth0 already configured
vr@avenger:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4687
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:8b:30:fd:78
Sending on   LPF/eth0/00:50:8b:30:fd:78
Sending on   Socket/fallback
```

I should also say that I went into the Network settings, checked the "This device is configured" box, and selected DHCP manually. Another note: I'm using 5.10. I tried Hoary but had the exact same problem, so I don't think it's a "Breezy-only" thing.

---

### Post by mlomker on 2005-09-20
I've seen other threads about two drivers getting loaded for one card and causing trouble.  You'll want to do a search on **tulip**.  Another good diagnostic is to use a Knoppix CD and see if it works well with your hardware.  If it works with Knoppix then you can look at the drivers, settings, etc. that it is using and that'll give you some good clues.

---

### Post by vr04 on 2005-09-20
i searched for tulip and tried some of the things that people did to make it work - no luck though. i tried adding tulip to /etc/modules. didn't work.

here's my output of ifconfig:

```
vr@avenger:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8B:30:FD:78
          inet6 addr: fe80::250:8bff:fe30:fd78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:13 dropped:0 overruns:0 carrier:23
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:27733 (27.0 KiB)  TX bytes:27733 (27.0 KiB)
```

**EDIT: **Also, I tried Knoppix like you suggested, It booted up fine until this message:

"Network device eth0 detected, DHCP broadcasting for IP."

It hangs there. My modem lights don't react, just the ethernet port on the back of my PC lights up in orange. I guess there's just no signal. I never get to see any GUI stuff. Knoppix never boots completely.

---

### Post by vr04 on 2005-09-22
does anyone have any ideas?

---

### Post by mlomker on 2005-09-22
> It hangs there. My modem lights don't react, just the ethernet port on the back of my PC lights up in orange. I guess there's just no signal. I never get to see any GUI stuff. Knoppix never boots completely.

Knoppix is a really reliable distro.  I tend to figure if something doesn't work with the latest version of Knoppix then it probably isn't going to work on linux at all.

Did you previously use this network card/connection with Windows?  I assume this is a plug-in network card and not a built-in one?  Network cards are really inexpensive...maybe try a different one?

---

### Post by vr04 on 2005-09-22
It does work with Windows, yes. I guess I could just buy a new NIC from newegg or something. Don't they cost somewhere around 15-20$? The decent ones, I mean.

---

### Post by mlomker on 2005-09-22
> Don't they cost somewhere around 15-20$?

Sure, for a new one.  Not sure if you have any used computer places around but I've bought cards for $3-5.  Basically any name-brand card (3COM, Intel, others) will work great.

---

### Post by vr04 on 2005-09-22
Awesome. Thanks for the advice.

---

### Post by skoal on 2005-09-22
Stop your grinnin', and drop your linen.  What exactly are doing, vr04?  I'll take a stab at it and you tell me where I went wrong here...

You have a newer computer.  It has another NIC (whatever model, doesn't matter) and it works with the Toshiba cable modem, right?  

You have an older computer, with a NIC using a tulip chip, and when you _disconnect_ the cat5 cable from your toshiba modem into the newer PC, and stick that cat5 into your older PC, that's when you can't connect, right?

Several questions:

1. What OS are you using on each machine, old and new?
2. How are you connecting on the new computer? Logging in first using some app?
3. Are you using a router between the cable modem and either computers?
4. Are you using the PPPoE login app on Ubuntu? If you are on KDE, you can use KPPP.  I dunno about Gnome, but I'm sure there is a GUI app for that.
5. Error messages on bootup from Ubuntu (just before X login)?  Anything?
6. 'ps -A | grep -i dhcp' return anything? dhcpd daemon running?

Several things (assumptions):

1. Your tulip card should be up and running on Ubuntu (older PC I assume), even though it fails to give you a proper IP.  Type 'lsmod | grep 'tulip\|mii' and see what's returned.

2. Some modern broadband modems actually do either of the following with respect to the initial login; 1. internally store the MAC from that NIC, or 2. send it off to an ISP intranet server.  Their are various ways you can reset that behaviour so different NICS on different machines can still use 1 provider.  A router would make that easier.  This might not be the problem directly anyways, but potentially one (based on your provider).

\\//_

---

### Post by vr04 on 2005-09-22
> Stop your grinnin', and drop your linen.Done and done!
> You have a newer computer. It has another NIC (whatever model, doesn't matter) and it works with the Toshiba cable modem, right?Yes.
> You have an older computer, with a NIC using a tulip chip, and when you _disconnect_ the cat5 cable from your toshiba modem into the newer PC, and stick that cat5 into your older PC, that's when you can't connect, right?You're probably thinking correctly here too. When I disconnect the cat5 from my new pc and plug it into the old one, my old PC cannot get online. Even after a reboot, restarting of the modem - nothing works.> 1. What OS are you using on each machine, old and new?The new machine has Ubuntu 5.04 installed. The old one has 5.10.> 2. How are you connecting on the new computer? Logging in first using some app?No. I don't have to log in. The cable modem is "always on," as they say. I just fire up Firefox and I'm online.> 3.Are you using a router between the cable modem and either computers?I'm not using a router.> 4. Are you using the PPPoE login app on Ubuntu? If you are on KDE, you can use KPPP. I dunno about Gnome, but I'm sure there is a GUI app for that.I'm not sure about that. Like I said, there's no logging in. My apologies if I'm missing something here.> 5. Error messages on bootup from Ubuntu (just before X login)? Anything?Yes. It can never synchronize the clock with ubuntu.com (or whatever the URL is)> 6. 'ps -A | grep -i dhcp' return anything? dhcpd daemon running?Nothing appears to be running. There's no output when i punch in that command.> lsmod | grep 'tulip\|miiThis returns 'tulip 45088 0' (the cable modem was not connected when I punched in that command)

---

### Post by skoal on 2005-09-29
vr04, sorry 'bout the ~week absence.  THanks for the informative reply.  Just two things (from my initial observations of that reply):

1. There ain't nothing wrong wit a tulip chip NIC.  In fact, it's one of the better (well supported) chipsets on Linux, historically.  Why isn't the MII transceiver module loaded (mii.ko)?  Does breezy have it statically compiled in with kernel?

2. I would imagine you probably have 'dhclient3' running. check it with 'ps -A' (for example).

* By the way, I had used TCI cable modem in the past.  WRT my 2nd assumption in prior post, you can try dc'ing all cables from cable modem, turn off power to it, boot breezy computer, let it fail at networking, connect all cat5 cables (as normally with hoary box), turn on modem power, and then restart "networking" service.  On some ISP broadband modems, you need to re-register the associated NIC MAC with it.  That's how I did it directly into a two different comps, and the technique is similiar when registering a router MAC instead.

\\//_

---

### Post by vr04 on 2005-10-01
[QUOTE=skoal]Why isn't the MII transceiver module loaded (mii.ko)?  Does breezy have it statically compiled in with kernel?[/QUOTE]I have no idea. :(> 2. I would imagine you probably have 'dhclient3' running. check it with 'ps -A' (for example).Yes, dhclient3 is indeed running.

I'm gonna try what you suggested and see if it works. Again, thanks for taking the time to reply.

---

### Post by vr04 on 2005-10-01
Ah, I just tried booting up, cycling through the modem and such, but I don't really know how to restart the networking service or how to re-register the associated NIC MAC.

I did disable/re-enable my eth0 device, though, and it still doesn't work.

---

