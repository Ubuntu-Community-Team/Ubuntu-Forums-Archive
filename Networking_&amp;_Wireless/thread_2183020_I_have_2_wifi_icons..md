---
title: "I have 2 wifi icons."
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by QNEPFmr on 2013-10-23
I just installed Ubuntu 13.10 en noticed that I have two indicators for WIFI in my upper panel. Is this normal or a bug?

[IMG]http://i.imgur.com/LSEvZVx.png[/IMG]

---

### Post by grahammechanical on 2013-10-23
What do you see when you click on each icon? Is there a difference. I notice that one icon is indicating a secure WiFi connection. I do not get that icon when I connect by WiFi. I get the left hand icon.

Regards.

---

### Post by QNEPFmr on 2013-10-23
Hi, 

This is the left one...

[IMG]http://i.imgur.com/WzUX7yC.png[/IMG]

and this the right one with the lock...

[IMG]http://i.imgur.com/H62tRuQ.png[/IMG]

When I switch to the gnome-fallback mode the wifi icon with the lock is gone.

---

### Post by I.Bun.Tu on 2013-10-23
I am also having this issue and I'm pretty sure it's a bug. I've done a bunch of reinstalls of Ubuntu 13.10 32-bit on both desktop and laptop machines and I've noticed this just one time on my latest install on my desktop machine. I'm sure reinstalling will fix the issue but I'm watching something on it right now and it would be nice to find a solution without reinstall... I will still likely reinstall in a few hours if I don't find a solution online.

My issue is exactly as described by OP including screenshots.

---

### Post by QNEPFmr on 2013-10-24
Hi, 

Have you tried the gnome session?
Btw, I have the 64 bit version installed.

---

### Post by I.Bun.Tu on 2013-10-24
I've actually reinstalled both machines and updated and both are showing two indicators. I am going to assume this is actually not a bug. 

It is unwanted behaviour however. It would be good to remove this second indicator with the lock. It is unecessary and the original indicator provides the same functionality plus more.

---

### Post by jacobcat on 2013-12-12
I also had the same problem. But I was able to remove the 2nd wifi icon by uninstalling indicator-network in Synaptic or via commandline:

```
sudo dpkg --remove indicator-network
```

Then restart Ubuntu. After that, I was able to successfully remove the 2nd wifi icon.

Hope this helps.

---

