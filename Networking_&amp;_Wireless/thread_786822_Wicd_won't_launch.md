---
title: "Wicd won't launch"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2008-05-08
Wicd won't launch. I have ndiswrapper working and there's power to my Dell wireless 1350, so now all I need is to get the network manager up and running. What should I do?

---

### Post by imdano on 2008-05-08
You need to be a little bit more specific about what the problem is.  Is the daemon not launching, or the tray/gui?  What error message are you getting when you run them from a terminal?  What version of wicd are you using?  Has it launched correctly before and suddenly stopped?

That said, you could try doing this and see if it works
```

sudo rm /opt/wicd/data/wired-settings.conf
sudo /etc/init.d/wicd start

```Then try launching the tray or gui and see if it works.

---

### Post by lakelovers on 2008-05-08
That did it. . . worked like a charm. Thank you

---

