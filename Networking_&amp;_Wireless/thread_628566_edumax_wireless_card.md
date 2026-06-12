---
title: "edumax wireless card"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by hollowhead on 2007-12-01
I've installed gutsy on a clean install wiping out windblows.  I bought a edumax 7128 wireless card since I was assured it "worked out of the box" to connect to our broadband router.  It works  but keeps disconnecting, the workaround is to disable wireless then re-enable it, there must be a more elegant solution.  It is not seen as ra0 but wlan0 the driver is given as rt61pci.  I don't want to to install the serialmonkey driver unless I have to, is there another way?

---

### Post by Lambert on 2007-12-02
> **hollowhead said:**
> I've installed gutsy on a clean install wiping out windblows.  I bought a edumax 7128 wireless card since I was assured it "worked out of the box" to connect to our broadband router.  It works  but keeps disconnecting, the workaround is to disable wireless then re-enable it, there must be a more elegant solution.  It is not seen as ra0 but wlan0 the driver is given as rt61pci.  I don't want to to install the serialmonkey driver unless I have to, is there another way?

wireless works in the 2.4 ghz spectrum. It is possible you're getting interference that's causing the disconnects. Try a different channel on your router to see if that works.

Also check out your syslog file to see if there are any errors related to the disconnects. System->administration->system log. Then make sure you're looking at the syslog file.

Did you also search this forum using the term rt61pci? you might find someone else who has had this problem and found a solution.

---

### Post by hollowhead on 2007-12-02
Cheers I will look into these things, how you change the frequency on the router could be an issue....

---

