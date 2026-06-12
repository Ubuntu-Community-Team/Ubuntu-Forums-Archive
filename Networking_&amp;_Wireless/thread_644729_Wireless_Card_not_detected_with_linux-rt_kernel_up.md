---
title: "Wireless Card not detected with linux-rt kernel update"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by angelsguitar on 2007-12-19
Hi.  I installed the updated linux-rt kernel and, after a restart, my Atheros AR2413 is gone from the network manager applet.  It works perfectly on the regular kernel, but is not detected when running the Realtime kernel.  Any suggestions?

---

### Post by angelsguitar on 2007-12-20
Has anyone had a similar problem?

---

### Post by radiobuzzer on 2007-12-20
Yes, I have this problem on an ACER 5102. We should report that as a bug

---

### Post by angelsguitar on 2007-12-21
Ok, how and where do we report it as a bug? (Sorry, my first time)

---

### Post by angelsguitar on 2007-12-21
Nevermind my last post; I did a search on how to report bugs and reported it on launchpad.  Here's the link to it: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/177859]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/177859")
it's bug #177859. It would help if you or anyone else that has the same problem can confirm it. Thanks.

---

### Post by jakoblund on 2007-12-28
I'm not using an RT kernel, but I had the same problem after upgrading to Gutsy. It turned out I had two versions of the newest kernel installed, but only one of them had the `restricted modules' package to support the ath card.

All I had to do was choose ``2.6.22-14-generic'' instead of ``2.6.22-14-386'' from the boot menu (the one that comes up if you press `esc' right after turning the power on)

To check you could try to open a terminal and type 

```
ls /lib/linux-restricted-modules/`uname -r`
```

and if you dont see ``ath_hal'' you should

```
sudo aptitude install linux-restricted-modules-`uname -r`
```

---

