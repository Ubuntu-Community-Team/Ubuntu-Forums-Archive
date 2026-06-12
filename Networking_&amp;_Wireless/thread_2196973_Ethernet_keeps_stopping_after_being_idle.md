---
title: "Ethernet keeps stopping after being idle"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by mitch-jouse on 2014-01-01
I was running 13.10, but kept having issues.  So I tried to reinstall 13.10, and had different issues.  

Re-installed 13.04 now, and now I'm having a problem I never had before.  When the computer sits for a log time idle, the ethernet connection stops working.  Rebooting fixes it.  This has never occurred before on this computer.

How do I go about finding the problem?

---

### Post by houstonbofh on 2014-01-01
This sounds a lot like bad hardware.  Three installs and none of them work?  Try running memtest a few hours and see if at least the memory is stable.

---

### Post by Speedwagon on 2014-01-01
No, this has only happened on the latest install of 13.04.  As I said, it has never happened before.

 I'll try a memtest

*please note that the above username was an SSO issue, and I am the same person

Update:  twice now I have had my Roku stop playback, because it can't access the files on my computer via Plex media server.  When I go to the computer, I have no network access.  I rebooted, and after the shutdown process, the computer seems to just hang with a blank monitor(power saving mode on the monitor).  A hard boot off/on fixes it.

---

### Post by Speedwagon on 2014-01-03
I figured out the reason for the hang ups:  My wireless driver is screwing with things.  After the installation, it got enabled, though I don't use it.  Since I disabled the wireless driver, the wired side is working fine.

Any ideas on how to figure out why the wireless driver is making things hang?

---

