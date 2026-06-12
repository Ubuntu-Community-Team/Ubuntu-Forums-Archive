---
title: "ipw3945 Slowness in Edgy"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by DnasTheGreat on 2007-04-07
Hi,

I have recently noticed a slowness with the ipw3945 wireless in my laptop. When ssh'ing to my server, I get horrible delays in between when I type a character and it shows up. This problem does not occur on a wired connection and booting into Windows on the same machine shows no such problems. My wireless also hiccups on and off occasionally. (And I'm only... 10 feet away from the router.)

Also, my ping times when on a wired connection and when on wireless are considerably different, so I suspect it's more than an ssh configuration problem.

To router:
Wired:
```
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=0.314 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=0.326 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=0.312 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=0.336 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=0.347 ms
```
Wireless:
```
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=1011 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=41.3 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=20.6 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=1001 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=127 time=760 ms
```

To google.com:
Wired:
```
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=43.2 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=240 time=45.9 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=241 time=45.6 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=241 time=44.6 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=240 time=46.1 ms
```
Wireless
```
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=240 time=56.7 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=240 time=1064 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=240 time=114 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=240 time=57.9 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=5 ttl=240 time=73.4 ms
```
(interesting, Google seems to redirect pings to various different servers.)

These tests are on a relatively fresh boot, and, as far as I can remember, I do not have a modified system wireless-wise save for a modification to the resume scripts to bring the ipw3945 regulatory daemon back up if it somehow died on suspend. (Happens occasionally.)

So... my ping times on wired are decent and consistent, but on wireless, they're slower by a couple orders of magnitude with an extremely high variance.

Very-verbose lspci output of my wireless card thing:
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at f0800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
```

I do not recall (and a quick glance through dpkg.log does not show) a wireless-related update recently. Nor did I play much with my system as far as networking or wireless is concerned. It's possible that I've had this problem since I got the machine (wireless at the university sometimes works and does not work at random) however I did not notice it until recently, so I do not have ping times, etc. to confirm or deny it.

Has anyone else experienced such a problem? Does the newest ipw3945 driver work nicer? Any suggestions for fixing it?

Thanks!

EDIT: A check confirms that the problem is not network-manager, so it's probably the driver. (Hrmm... I think it might be worth it to get nm really stable so that the static thing can be scrapped... or at least having them both modified so they play well with each other. It took a *long* to convince nm to watch both wired and wireless again,)

---

### Post by DnasTheGreat on 2007-04-08
So it seems someone else has the same problem

[http://ubuntuforums.org/showthread.php?t=396987&highlight=ipw3945](http://ubuntuforums.org/showthread.php?t=396987&highlight=ipw3945)

But I don't really want to resort to ndiswrapper.

The fix in ieee8021 in 1.2.15 looks enticing.
[http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)

> Fix TKIP and WEP decryption error on SMP machines

Which coincides exactly with my two problems with wireless. (Home uses WEP (Ubuntu, at least at one point... not sure how it is now, didn't play well with WPA) and university uses TKIP.)

I did try to compile a new version, but the supplied ipw3945 didn't work with it and getting a new one of that caused errors... and I was already treading on I-don't-want-to-go-there territory with fussing with my known-to-be-mostly-stable kernel. (I come from Gentoo in which much of the kernel-related stuff is dealt with by Portage.)

I'll try rolling my own kernel or stealing 2.6.18 from feisty and praying it works. :)

Perhaps Ubuntu should consider changing its update policy? I know it's nice to have very few changes for corporate users and stuff, but one of the most common "I don't want to use Linux" reasons is the supposed lack of driver support. Part of this is because most distros run old stuff. Back in Gentoo I had much fewer problems with drivers because I would run relatively recent versions of stuff. (And no, I am not putting Gentoo on this guy... nice distro, but not for laptops.)

EDIT: Okay, I compiled the latest kernel, used the in-kernel ieee8021 and the latest ipw3945. The version for ieee8021 in /sys/module still is "1.1.13-git", but diffing the source and the website's notes seem to suggest that it's more-or-less the same as the latest standalone one.

The connection still pings horribly and delays during ssh, etc., but the delays do not feel quite as bad. (Definitely not just a placebo... I can actually use ssh now.)

I guess I will stick with this until something better shows itself.

---

