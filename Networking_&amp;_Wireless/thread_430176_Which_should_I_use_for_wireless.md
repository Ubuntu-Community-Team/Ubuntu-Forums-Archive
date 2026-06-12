---
title: "Which should I use for wireless?"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by LochNess on 2007-05-01
Hi everyone,

I'm setting up my HP laptop with Ubuntu, and I've got wired network working, and now I'm trying to get my wireless to work.

My wireless chip is this:

```
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC
I Card (rev 01)

```

It looked kinda weird that the word Dell is in there, but whatever.

What procedure should I use to get the wireless working?  I have WPA security on my access point.

Thanks!

---

### Post by chili555 on 2007-05-02
Under its Dell skin, this is a Broadcom bcm43xx chipset. There are several posts that describe how to get the firmware installed and fire up this card without ndiswrapper. The downside, apparently is you will be limited to 11 Mb/s speeds. If you want to surf the web and email, that will be plenty. If you want to stream video from your media server, it will not be fast enough. 54 Mb/s speeds are evidently achievable with ndiswrapper.

Search this forum for bcm43xx and you will find both methods outlined.

---

### Post by LochNess on 2007-05-02
Thanks, I'll check them out.    My DSL is slower than 11Mb/s, and I'm not planning on streaming any video, so I'll have a go at the no ndiswrapper method.

---

### Post by stchman on 2007-05-02
> **LochNess said:**
> Hi everyone,

I'm setting up my HP laptop with Ubuntu, and I've got wired network working, and now I'm trying to get my wireless to work.

My wireless chip is this:

```
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC
I Card (rev 01)

```

It looked kinda weird that the word Dell is in there, but whatever.

What procedure should I use to get the wireless working?  I have WPA security on my access point.

Thanks!


What is a Dell card doing in an HP laptop?

I have a procedure to get Broadcom 43xx wireless cards working.  It will not work for these cards since I dont have the Broadcom Dell Wireless .inf files.  If you could get your hands on those files the procedure could be modified.  Since Dell is making a big switch to Ubuntu they might be sympathetic if you email them they might direct you to a place you can download the .inf files.

If that card is indeed a 43xx Broadcom card you can use the procedure as is.

Here is a link to my procedure:

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

I hope it helps you.

---

