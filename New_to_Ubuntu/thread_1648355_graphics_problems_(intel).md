---
title: "graphics problems (intel?)"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-12-18
I've been having a lot of graphics problems lately.  Not sure what is causing them.

I've attached a couple of screenshots.  One from the compiz "fire" effect, the other from the game Urban Terror.

Both of these things worked for me before I reinstalled Ubuntu 10.04 (I had upgraded to 10.10 and it didn't go well).

This is my graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

```

I'm using this driver:
[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/~glasen/+archive/intel-driver")

It's a 64-bit install.  Any ideas?  It's driving me mad.

---

### Post by jtarin on 2010-12-18
Let me get this straight....you had 10.04 originally then you upgraded to 10.10, then reinstalled 10.04. Now which one worked for you the first install of 10.04?

---

### Post by stoogiebuncho on 2010-12-18
Yeah, my first install of 10.04 was working.  I upgraded to 10.10 - it had some problems.  I reinstalled 10.04 and now I'm having these issues.

---

### Post by jtarin on 2010-12-19
The launchpad driver that you mention in your first post is that the same one you used in your first install?

---

### Post by stoogiebuncho on 2010-12-19
> **jtarin said:**
> The launchpad driver that you mention in your first post is that the same one you used in your first install?

No, it's not.  But I started with the same driver, and it wasn't working, so I tried the one from that ppa instead.

I think I actually just fixed this by following the instructions on this site:
[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

My desktop effects are working now, and textures in *most* games are working.  So far so good.

Still don't know why it didn't work from the beginning, but oh well.

---

