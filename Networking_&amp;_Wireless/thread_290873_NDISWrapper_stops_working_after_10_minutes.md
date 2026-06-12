---
title: "NDISWrapper stops working after 10 minutes"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by aandreev on 2006-11-01
Hi,

I've got a Dell D820 with the BCMWL5 card, running Edgy. I compiled ndiswrapper from the source in apt, but about 10 minutes after connecting my wireless card suddenly disappears. I tried reloading ndiswrapper, playing with iwconfig, etc., but eth1 is just not there.

PS It all worked fine on Dapper with the same Windows drivers.

---

### Post by AndyC_772 on 2006-11-23
I have the same card and the same problem - it worked in Breezy and in Dapper, but now I've upgraded to Edgy it works for a while and then stops. My laptop is a Dell Inspiron 8200.

Any clues?

---

### Post by FrodoB on 2006-11-23
Folks, it is probably faster to go back to Dapper if it was reliable there. I use a Broadcom bcm4311 in Edgy, but I know that there are a lot of issues to deal with.  Which chipset do you guys have and which versions of ndiswrapper are you using?

---

### Post by AndyC_772 on 2006-11-23
I've just upgraded to the stable version 1.29 from sourceforge, following (almost!) the link at [http://www.ubuntuforums.org/showthread.php?t=140214&page=3&](http://www.ubuntuforums.org/showthread.php?t=140214&page=3&)

Fingers crossed that it now works :) I can't honestly say I'd regard regressing back to an earlier release of the OS as progress, given that I can't be the only one with this problem. In any case, I like Edgy so far - I can actually swap PCMCIA memory cards in and out without having to mess about mounting and unmounting them in disks-admin (which is just as well, since that tool seems to have gone AWOL anyway).

---

### Post by FrodoB on 2006-11-23
Thanks for pointing out that ndiswrapper 1.29 is released. Very good news.

---

### Post by AndyC_772 on 2006-11-24
Sadly it seems to have made no difference :(

It does, however, seem to be the case that as long as I'm actively using the PC, the connection stays up. It's only if I leave it, do something else for 10 minutes or so and then come back, that I find the connection has dropped.

I wonder whether the wireless card goes into a power saving mode when it's not being used, from which it never wakes up?

A way to test this theory should be to set up a background task that just pings my wireless router every 10 seconds or so, to keep the connection active. Could somebody please suggest how I might do that? (Scurries off to check the manual for 'cron'...)

---

### Post by Stinger on 2006-11-24
> **aandreev said:**
> Hi,

I've got a Dell D820 with the BCMWL5 card, running Edgy. I compiled ndiswrapper from the source in apt, but about 10 minutes after connecting my wireless card suddenly disappears. I tried reloading ndiswrapper, playing with iwconfig, etc., [COLOR="Red"]but eth1 is just not there.[/COLOR]

PS It all worked fine on Dapper with the same Windows drivers.
I thought ndiswrapper used wlan0 as alias ? I'm using ndiswrapper myself , ASUS WL-138g, here is my /etc/modprobe.d/ndiswrapper file
```
alias wlan0 ndiswrapper
```
:-k

---

### Post by Sendervictorius on 2006-11-24
> **AndyC_772 said:**
> Sadly it seems to have made no difference :(

A way to test this theory should be to set up a background task that just pings my wireless router every 10 seconds or so, to keep the connection active. Could somebody please suggest how I might do that? (Scurries off to check the manual for 'cron'...)

Just

ping <ip address> -i 10
:D

---

### Post by wieman01 on 2006-11-24
The alias in Edgy appears to be "eth1". Seen it before.

As for the disconnection issue, could you please set the router's **"beacon interval"** to a lower value than the current one? I am just testing my theory here. This resolved the problem for me while changing the default value from "100" to "10". I know this is an ugly fix, but I cannot help it.

Have not had a disconnection issue since. Pinging did not help.

---

### Post by AndyC_772 on 2006-11-25
Sadly my wireless router (the otherwise excellent, completely reliable 3com OfficeConnect 11g) doesn't have this option.

Instead I've tried configuring Thunderbird to check for new email every 2 minutes instead of every 10 - an equally if not even more ugly workaround, but just maybe it will help.

The whole setup is still quite clearly broken, though. Occasionally after a reboot I have no wireless connection and get the dreaded 'SIOCGIFFLAGS error: no such device' when I click the status monitor icon. Reboot again and the problem is usually gone. A search reveals plenty of people who have a similar, even more persistent problem with this error - but absolutely no clues as to what causes it or how to fix it.

Also I invariably have no wireless connection the one boot in 30 when Ubuntu decides to run a check on the hard disc during startup.

These last two errors were there in Dapper too - they're nothing new, and since they become apparent the moment the desktop appears, rebooting again isn't too much of a headache.

The loss of my connection during a session definitely is, though. I can recover it by disabling the wireless connection and re-enabling it, but (for reasons I can't imagine), disabling the wireless connection also removes my WEP key, so I have to type it in again before I can reconnect. Annoying if, like me, you're not good at remembering 128-bit hex strings.

It feels like I should be reporting some of these issues as bugs to the developers, but:

1) since they're so obvious, I can't help but assume somebody else must have done so already

2) maybe because of (1), nobody bothers to report them?

---

### Post by FrodoB on 2006-11-25
It could also be that your router does not maintain the connection unless there is constant out going traffic. I have an older model Linksys that seems to have problems maintaining connections unless they are in constant use. So I periodically have to tell it to reconnect in its setup pages. Or it could be that your ISP just drops the connection after 10 minutes of inactivity and experts you to reconnect.

You might try an experiment.  Send a low rate ping to another site for about 30 minutes and see if the link remains on:

$ ping -i 240 [www.google.com](www.google.com)

this will send a single ping to Google every 4 minutes. If this keeps you connections from dying, it is either your ISP, your router or it could be power saving on your device, but unless you specifically have setup power saving, then I doubt it.

---

### Post by AndyC_772 on 2006-11-25
It's definitely not that I'm afraid, I did try setting Thunderbird to check my email every 2 minutes instead of every 10, but it hasn't helped.

In any case, my other PC (connected by Ethernet) has no problem, nor did my laptop under Dapper or Windows. No doubt this is an Edgy issue. Thanks for the suggestion, though.

---

### Post by falkenberg_cph on 2006-11-26
Maybe you have made the same stupid mistake as me:
[http://www.ubuntuforums.org/showthread.php?p=1809544#post1809544](http://www.ubuntuforums.org/showthread.php?p=1809544#post1809544)

/carsten

---

### Post by AndyC_772 on 2007-01-21
I think I found my silly mistake ](*,) 

I had a typo in my /etc/modprobe.d/blacklist file, which meant the bcm43xx module was loading. I suspect I was actually using that driver all along.

With the typo fixed, though, I had no wireless network at all. In desperation I gave up, backed up my Ubuntu partition to an external USB drive, and reinstalled from scratch. It now seems fine.

---

