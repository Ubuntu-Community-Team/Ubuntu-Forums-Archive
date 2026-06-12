---
title: "64bit or 42bit? Worried about compatibility"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Dyegov on 2009-04-27
Well I recently installed Ubuntu 9.04 64-bit on my computer (Intel Core 2 Duo 2.4 Ghz processor, 4GB DDR2 ram, 512MB DDR2 Video). I installed 64-bit because I wanted to use my 4Gb of Ram (32bit only shows 3GB). However, I found problems with 64bit when installing things like Flash for Firefox, and that made me wonder.

Will I have several compatibility problems with my codecs/programs/devices? If so, how can I do to install 32-bit instead, without having problems with my Vista partition? (I'm dual booting). I don't want to make a mess with it. Thanks in advance.

---

### Post by AndyCooll on 2009-04-27
I use 64-bit with a similar configuration as yours and haven't noted any problems.

If you wanted to use 32-bit instead you'd need to download the 32-bit version of Ubuntu then simply do a re-install re-using the partitions you've already created for your 64-bit install. To do this, at the partitioning stage you'd select "Manual".

:cool:

---

### Post by Didius Falco on 2009-04-27
If you rather keep the 64 bit, there are lots of folks here that will help you iron out any mulimedia problems.

---

### Post by Dyegov on 2009-04-27
So are you using sites like Youtube and Facebook with those alpha and beta releases and had no problems at all? I'm only worried about compatibility. If I won't have those problems I can easily stay with 64 bit.

---

### Post by LowSky on 2009-04-27
i have no issue with flash using 64bit

as for codecs, use medibuntu and use the w64codecs, and not the w32codecs.

---

### Post by stchman on 2009-04-27
> **Dyegov said:**
> Well I recently installed Ubuntu 9.04 64-bit on my computer (Intel Core 2 Duo 2.4 Ghz processor, 4GB DDR2 ram, 512MB DDR2 Video). I installed 64-bit because I wanted to use my 4Gb of Ram (32bit only shows 3GB). However, I found problems with 64bit when installing things like Flash for Firefox, and that made me wonder.

Will I have several compatibility problems with my codecs/programs/devices? If so, how can I do to install 32-bit instead, without having problems with my Vista partition? (I'm dual booting). I don't want to make a mess with it. Thanks in advance.

Flash 10 is easy in 64 bit.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Multimedia in 64 bit is also easy.

```
sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Hospadar on 2009-04-27
Amen,
I was holding back on 64 bit for a while because I had had some unfortunate XP 64 bit issues, but on ubuntu I didn't even notice the switch (in a good way).

In reality, you'll probably never notice the difference unless you crunch big numbers, but if everything is just as compatible (which it is) you'll probably save yourself a few cpu cycles, and in doing so save a little power and maybe speed things up, all of which are good things.

---

