---
title: "Random Loss of Internet Connection"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by shirt on 2006-09-29
I've been having a strange problem recently. I'll be looking up websites/using bittorrent/etc...and it will be working fine, then, at variable lengths of time (sometimes within 5 minutes, sometimes within 5 hours, etc..) my internet connection will just stop and I won't be able to load websites and such. Now, after trying many different ways of fixing it, I just decided to format and reinstall Ubuntu, however, even after a fresh install I am still having the same problem. Some info on my computer: I'm using a cable modem connected directly to my computer (no router, no LAN, etc..). My motherboard comes with its own ethernet interface, but I use a separate card instead (maybe that would cause issues?). I have my system set up for dual-boot (windows/linux) and my internet connection works flawlessly in Windows. Normally I try to solve issues myself, but I am simply lost as to what to do in this situation. Any ideas?

---

### Post by Old Pink on 2006-09-29
Check if the networking module of Ubuntu has been updated recently, and if it has see if you can downgrade. 

Unless you personally changed something, this is all I can suggest.

---

### Post by jmmcd on 2006-09-30
Some more information required, I think:

Is it wired or wireless? When the connection fails, what symptoms do you notice? Run 

```
$ ifconfig
$ host google.com
$ ping google.com

```

when the connection has gone down, to see whether *anything* is still working. When the networking goes down, what do you do to get it back up - does it work if you run

```
$ sudo ifdown eth0
$ sudo ifup eth0
```

(assuming eth0 is your network connection, as you'll see from ifconfig).

A hunch: try some internet usage where you *only* download - no uploading files or bittorrent or anything like that, and see if that makes it work for longer. Then, try uploading a large file - eg by emailing an attachment through webmail - to see if that makes things stop working. (I have symptoms a bit like this - see thread: [http://www.ubuntuforums.org/showthread.php?t=212964]("http://www.ubuntuforums.org/showthread.php?t=212964"))

---

### Post by Old Pink on 2006-09-30
> **jmmcd said:**
> Is it wired or wireless? 

Read the original post:

> **shirt said:**
> Some info on my computer: I'm using a cable modem connected directly to my computer (no router, no LAN, etc..). My motherboard comes with its own ethernet interface, but I use a separate card instead (maybe that would cause issues?).

---

