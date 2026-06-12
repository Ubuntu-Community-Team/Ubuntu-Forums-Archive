---
title: "CUPS shutting down"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by seattle vic on 2010-09-16
Every couple of days CUPS will not respond and I have to restart it, after which it runs fine, for a couple of days.

I checked the log files in /var/log/cups but did not see any clues.  What I don't know is if it was still running at that time, but I'll check the next time it fails.

Any clues?

---

### Post by OhBooHooTu on 2010-11-03
Well, no clues at all, but exactly the same thing happens to me. I'm running 9.10 which I just upgraded to from 8.something. I'm on an Intel Dual E2200 with 3.2GB reported. No dual boot or any such thing. Printers worked fine before, and they still work fine if I type **sudo service cups start** in a terminal when they all go away. Specifically, the File -> Print menu show only Print to File and all the other printers are gone. Upon restarting CUPS I can immediately use my printers. It seems to last a few days, but I don't have a specific number.

Although the installation was very much vanilla, there was a warning message that prompted me to edit /etc/cups/cupsd.conf and change **Browsing Off** to **Browsing On**. The message had claimed that it was On in the previous version and I might want to change. Otherwise, no changes.

Thoughts?

---

### Post by jtarin on 2010-11-03
You might be missing the following from your /etc/network/interfaces file:


```
auto lo
iface lo inet loopback
```

Reboot and it should start working again.

---

