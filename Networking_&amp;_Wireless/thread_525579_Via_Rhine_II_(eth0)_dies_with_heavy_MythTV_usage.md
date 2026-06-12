---
title: "Via Rhine II (eth0) dies with heavy MythTV usage"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by oxbadfood on 2007-08-14
Hello,

I use to run a MythTV backend server with Fedora Core 3, 4, and 5... but by then it was getting more difficult to maintain a trouble-free Linux experience (as I feel Fedora Core 5 was more unstable than 3 or 4)... but I digress.  In order to learn new stuff and to promote stability I switched to Ubuntu Edgy, then Fiesty and have been relatively impressed and happy since.

My problem is that with the heavy network usage associated with MythTV (2GBi video files) and long up-times (weeks or months without reboot) with my mythtv-backend server, I have occasions when the frontend machine suddenly freezes while watching video.  When I look at all the usual suspects, I always find it is because my backend server (running Ubuntu) has lost eth0 connectivity to the world.  This is confirmed by the inability to ping any remote hosts by name or even local hosts (such as the gateway) by IP address.

The simple work-around-fix to get everything happy again is to restart the backend's network interface by performing a:

```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up
$ route add default gateway 192.168.0.1
```

So my questions are:
1)  Is there a known memory leak with the VIA RHINE II (rev 74) built-in Ethernet adapter driver that the rest of the world knows about?  Is there a later version or branch of driver development that I can compile from source that might fix this (because my system is up-to-date via the universe/multiverse and the card worked fine with MythTV and Fedora for years)

2) Is there some more data I should look for when this lock up happens?  Perhaps using /bin/dmesg ?  (Even after locking up, right now the ring buffer only shows that IRQ 18 was assigned to the Ethernet card at boot time, no other mentions of the RHINE II is there)

Here is the relevant lspci -v info regarding my RHINE II

```
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
        I/O ports at 9800 [size=256]
        Memory at d9800000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2
```

3)  Is there something I could post here that would help further troubleshoot this?  I've read numerous articles about known problems with the auto-power-management features causing laptops not to "wake-up" the NIC, but I don't think this is my problem... but how do I check to ensure this is the case?

Any advice or "I have the same problem" posts would be appreciated!
Thanks!

---

### Post by oxbadfood on 2007-11-13
Just an update for those of you that care or have had similar problems.  I am unable to confirm a fix, but rather found some more information that I would like to share.  I was using an Ethernet router (Linksys WRT54G) that had been flashed to support wireless bridging in addition to routing.  I was using Freeman (an off shoot/GNU release of Talisman from Sveasoft),  I noticed that this flash made the router somewhat unstable, and I would occasionally have to reboot/power cycle the router; this was in addition to the ifconfig up/down bouncing of the eth0 interface listed above.  It is important to note that theses events did not correspond 1 to 1, and that sometimes the router power cycle would not have to be accompanied by an interface bounce and vice versa.

Anyhow, I changed my firmware on the exact same router back to Linksys's official firmware and this helped a bit.  It still did not solve the problem completely, but reduced the frequency to at least half the occurrence rate.

Eventually I decided to upgrade to a Linksys Gigabit adapter and ditch the on-board Rhine II adapter mentioned above.  This was of course accompanied by a Linksys Gigabit switch.  Since those two changes, and the retirement of the old interface and router, I have had ZERO problems.

It sort of bums me out though that I didn't fix the problem and instead worked around it with improved, fasted, better supported hardware.  I still would like to know if anyone else has had these problems with the above problematic configuration, and if so, what they did to fix it.  I am still left with the hypothesis that the sheer amount of data going through the driver caused a memory leak which eventually froze the interface.  When I removed the bridge portion from the device that the interface was hooked up to, I must have inadvertently slowed the memory leak due to to a reduction of router ARP packets or the like (redirects, etc).  When I replaced the adapter completely, I was no longer using a buggy driver.... of course, who knows???  That's why I'm posting here for comment.

---

