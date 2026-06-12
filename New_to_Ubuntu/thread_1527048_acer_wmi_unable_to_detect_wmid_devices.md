---
title: "acer wmi unable to detect wmid devices"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by dude213 on 2010-07-08
i just downloaded ubuntu 10.04 desktop edition today and installed it on my AAO D250 and whenever i boot i get this error i did try ubuntu 9.10 about 4-5 months ago using wubi and never had this error anyway to fix it? also when i shut down a bunch of words come up but there gone to fast to read is that normal? im new to ubuntu/linux so i dont know much about it i tryed it before but only for a few days

---

### Post by dude213 on 2010-07-08
please help

---

### Post by mike555 on 2010-07-09
Well, here is a quick fix. in terminal type ; gksu gedit  , 
 
    then in gedit open  /etc/modprobe.d/blacklist.conf

    at the bottom type "blacklist acer-wmi" without the quotes.

---

### Post by egx2 on 2010-07-15
works for me on acer one (kav10)

just type on terminal:

```
echo blacklist acer-wmi | sudo tee -a /etc/modprobe.d/blacklist-acer-wmi.conf
```then enter

---

### Post by Objekt on 2010-12-14
I realize I'm reviving a somewhat old thread, but I didn't see the point in creating a new one when this one is 100% on-topic.

I was seeing the "unable to detect WMID devices" message when starting up Ubuntu 10.04 (plain old desktop distro) on my Acer Aspire One D150.  However, in my case, it didn't seem to cause any real problems.  Everything worked, except the internal microphone (fodder for another thread, perhaps), so I didn't worry about it.

What does the message actually mean?  While I've made it go away by applying the suggested line to /etc/modprobe.d/blacklist.conf, is that a placebo, or does it actually solve the problem?

Is the microphone problem I've noted related to this one?

---

### Post by Stigmata13 on 2010-12-14
I have an Acer Aspire 5515 and I have had this problem also. Using Ubuntu versions 8.04-10.04 the message was displayed, it would hang for 10-20 seconds, and then continue and do a normal boot.
Although I don't see this message in 10.10, I do suspect the problem is still there, as boot takes much longer than it should, because it still hangs on a screen (just a plain black one though, no message is displayed)

---

### Post by Objekt on 2010-12-14
I got the microphone issue cleared up.  It was totally unrelated, being as easy as installing a couple of PulseAudio utilities (padevchooser was one).

Sorry to hear you're having hangs.  I fixed it, but even when it was happening, the "WMID" message didn't cause a hang.  It just seemed like something that should not be happening, and possibly an indication of trouble ahead.

---

