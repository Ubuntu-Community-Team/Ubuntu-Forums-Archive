---
title: "USB WiFi &quot;dongle&quot;/Card"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by devsen on 2008-04-23
hello,

I know there is a long list of usb wifi cards / "dongles" for Ubuntu but I would be interested in getting some advice on which is the best in terms of working out of the box. I am on 7.10.

Thanks - Dev

---

### Post by dstew on 2008-04-23
It seems the My Essentials Wireless G USB dongle works in Gutsy. See [_this thread_]("http://ubuntuforums.org/showthread.php?t=604245"). It uses the Linux native driver which comes with Gutsy.

---

### Post by kutjara on 2008-04-23
> **devsen said:**
> hello,

I know there is a long list of usb wifi cards / "dongles" for Ubuntu but I would be interested in getting some advice on which is the best in terms of working out of the box. I am on 7.10.

Thanks - Dev

I'm using 64 bit Hardy and have been able to find very little information on how well/poorly the different cards work in this environment. The built-in Broadcom card in my laptop had a major problem so I ended up buying a Belkin F5D7050 USB dongle, largely because it uses the Ralink rt73 chipset, for which Serialmonkey provides drivers. I had to download and compile the driver myself, but this only took a couple of minutes and the card was working perfectly within five.

For each chipset (Broadcom, Ralink, Atheros, etc) you'll see a thousand posts claiming it's the work of Satan, and a thousand posts claiming it works perfectly with minimal setup. The reality is it depends very sensitively on your specific setup. Wireless on Linux is still, I'm afraid, a bit of a black art.

The only consensus I've seen is that, when buying a laptop, you should only consider models using Intel integrated wireless. Apparently, that works "out of the box" with Ubuntu. Not much help to you now, I know, but food for thought for the future.

---

