---
title: "How do I clear iwlist scan &quot;cache?&quot;"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-08-24
iwlist scan seems to cache its results. I scanned, and saw my original ssid. Then, I changed my ssid on the AP and scanned again, but saw my original ssid reported. I couldn't jog it with an ifconfig down/up.

What's the scoop?

Edit: Oh, and the annoying part is that all the encryption info, and everything else was cached. (Along with the name, I had removed wireless security.)

---

### Post by kevdog on 2007-08-25
Im not finding a physical file, but there are a bunch files with similar info in /proc/net

Check out the /proc/net/ndiswrapper/<interface_name> directory.  Wonder what happens if you delete one of those files???

See if there are some old file creation times.

---

### Post by croto on 2007-08-25
make sure you run iwlist as root. If you run it as normal user it *doesn't* scan but shows you the result of the last scan.

---

### Post by Jamie Jackson on 2007-08-31
> **kevdog said:**
> Im not finding a physical file, but there are a bunch files with similar info in /proc/net

Check out the /proc/net/ndiswrapper/<interface_name> directory.  Wonder what happens if you delete one of those files???

See if there are some old file creation times.

It doesn't *seem* to be relevant. Those files are updated each time I scan, even when the "caching problem" is occurring.

---

### Post by Jamie Jackson on 2007-08-31
> **croto said:**
> make sure you run iwlist as root. If you run it as normal user it *doesn't* scan but shows you the result of the last scan.

It *does* take longer to run under sudo, so it seems that it's doing something more, but I'm still seeing the problem. I'm going to reboot as a sanity check, to see if it finally picks up the changes.

Edit: Yes, it correctly reports my AP changes in an iwlist scan *after* rebooting.

So, I'm still at square one with this little issue.

---

