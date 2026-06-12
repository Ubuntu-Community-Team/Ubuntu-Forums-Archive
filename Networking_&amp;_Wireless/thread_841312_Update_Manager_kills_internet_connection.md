---
title: "Update Manager kills internet connection"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by attercop on 2008-06-26
This is quite a recent thing, which never used to happen. Now when i use the Update Manager it works for a few meg of download, then the connection drops. No internet. As you can imagine this makes any decent sized update a massive chore.

At first the only solution i knew was reboot. Which works. Then i found that by Disconnecting then re-Connecting the connection using the usual router web browser interface, the internet connection came back.

I'm no network expert but it's almost like the Update Manager is giving the router a stuck session. Is anyone else getting this?

Thanks in advance.

Notes: I'm on 8.04. Using a _wired_ connection to a Belkin Wireless G Modem Router. I think the part # is F5D7632UK4A. Bog standard nForce integrated NIC.

---

### Post by spd106 on 2008-06-26
It's probably worth checking for a router firmware update. I've found these Belkin router to be rather flaky out of the box.

Next perhaps try using a different update server such as the official archive.

---

### Post by superprash2003 on 2008-06-26
does it happen only in ubuntu? if possible try with another pc!!

---

### Post by attercop on 2008-06-27
I couldn't be sure if it's Ubuntu specific. But i can say i haven't encountered this issue on the admittedly rare occasion i boot into XP.

It seems to be a feature of one of the more recent kernels. There have been several in a short space of time so it's hard to determine with which one the issue started. But it certainly got much worse on the latest -19 update.

I've done a firmware upgrade on the router and will report back on my findings when a decent sized number of updates come through from the Update Manager.

---

### Post by attercop on 2008-07-01
Updating the router's firmware has not solved the problem. Although i have discovered that Update Manager is not the cause. The issue also occurs when i download any file of decent size (7MB plus roughly). The connection dies and the router's internet connection has to be restarted.

---

### Post by attercop on 2008-10-07
Update:

Although this problem still exists with this router on a fully up to date Ubuntu (32-bit), i have found that by running Frostwire at the same time as downloading large update files, or larges files from the internet in general (such as streaming video etc) then the connection doesn't drop/freeze/stop.

Maybe something in Frostwire keeps ports open that aren't usually or stops something clogging up the router session?

---

### Post by paulb42 on 2008-10-20
I've had a similar problem ever since I installed Ubuntu. During download of large files via Firefox, or during System update, my connection stops. If I use the connection for something else eg mail or normal browsing it continues where it left off. Wondered if it was something to do with my router setup? I'll take a look at this Frostwire ...
[ D-Link DSL-300T modem, Safecom wireless router ( but using wired ) ]

---

### Post by Whelk on 2009-01-07
I hate to resurrect an old thread, but I couldn't find anything else on this particular issue.  If I overlooked it, please direct me to the appropriate topic.

I'm having a very similar issue here.  Downloading from a WindowsXP station on the same network has no problem.  In fact, if I reboot my computer and load up WindowsXP instead of Ubuntu, I can download fine.

My experience: 

In Ubuntu I start a download of a size over a few MB.  This can be in Firefox or the Update Manager.  The result is that my ping time shoots up dramatically over a few seconds (from the 20s to the 1000s) and then the connection drops for about 10-20 seconds.  The connection then restores itself and the download takes an additional 30 seconds (give or take) to resume downloading, at which point ping times shoot up again and the connection drops again, etc. in a repeating cycle.

This cycle happens several times but seems to eventually go away if it's one large download that lasts over about 5-10 minutes.  Eventually the ping times will stick around the 20s and the download will continue without any connection drops or other problems.

If I start a new download later, however, the entire cycle starts over.  Extremely frustrating, to say the least.

Has the cause of this ever been discovered?

---

### Post by bgold2005 on 2009-01-11
Me too, with a twist: update manager is fine for Ubuntu, but kills
my router for Win XP.
Tried release/renew with flushDNS and registerDNS, still cannot
obtain IP address (even though can see/connect with router, is stuck at 'no IP address' and 'Limited Connectivity')

pulling plug on router cures every time

Ubuntu: 8:10 (interpid...ibex)
Win XP: Home
Router: DI-524 (Dlink)

- B Gold

---

### Post by simseve on 2009-07-31
Exactly the same problem here, with different PCs running Ubuntu (intrepid/Jaunty).

Router: Zyxel P-660HW-D1.

Everytime update manager start updating the sytem the router every now and then reboot (Both LAN and WLAN connection).

Works perfectly on Win XP.

Simone

---

### Post by joelunchbox on 2009-09-30
I'm having the same trouble. Using a wired connection works fine but if I try to do an update or download via wireless, it kills the router's connection to the WAN. The computer still shows connectivity to the router and strong signal strength. Wired connections do not drop. Wireless connectivity also drops for other computers (XP) using this router when I try an Ubuntu update.

Re-booting the router solves the problem. I'm betting that the best (least frustrating) solution might be buying a new router.

Router: Belkin 54G (unsecured)
Asus EEEpc 1000
Ubuntu Netbook Remix 9.04

---

