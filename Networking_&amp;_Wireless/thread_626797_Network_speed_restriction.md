---
title: "Network speed restriction"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by expoiser on 2007-11-29
Hey

Me and a friend of mine just installed ubuntu on his laptop, however when we try to download some package files we are getting kicked by our network administrator on our dorm, as we use the full line. Is there a way that we can restrict the download speed total on the linux system, so we wont get kicked again?

Thanks in advance

---

### Post by dave37 on 2007-11-29
Absolutely, there are many ways, I have used wondershaper which IMHO was the easiest way to do it.  I used it for the opposite to ensure that ftp uploads weren't taking all the bandwidth in my SOHO but it will work the other way as well.

```

Package: wondershaper
New: yes
State: installed
Automatically installed: no
Version: 1.1a-4
Priority: extra
Section: universe/net
Maintainer: Vince Mulhollon <vlm@debian.org>
Uncompressed Size: 81.9k
Depends: iproute
Description: Easy to use traffic shaping script
 An easy to use traffic shaping script that provides these improvements:
 * Low latency for interactive traffic (and pings) at all times
 * Allow websurfing at reasonable speeds while uploading / downloading
 * Make sure uploads don't hurt downloads
 * Make sure downloads don't hurt uploads

 It does this by:
 * Limiting upload speed slightly, to eliminate queues
 * Limiting download speed, while allowing bursts, to eliminate queues
 * Interactive traffic skips the queue
 * ACKs and tiny packets skip the queue

 Configuring the wondershaper requires you to accurately and precisely determine your consistent upload and download speeds.

 The wondershaper is the simplest, easiest to use, entry level, traffic shaping
 script provided by Debian.

 After installing this package, read highly the detailed instructions:
 /usr/share/doc/wondershaper/README.Debian



```
I found the detailed instructions in the above noted path the easiest to understand and use.

---

