---
title: "Linksys WUSB54G V4 in Hardy"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by herschen on 2008-07-20
I followed the instructions in this post: [http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045"). I've disabled  roaming mode and put in all the information, Network name-linksys with no password protection. I'm running into the same problem every time. I open System-Administration-Network and click Unlock. I check the box next to Wireless Network and I click close. I'm not able to connect to the Internet and when I reopen the Network window, wireless is unchecked. I'm using Hardy Heron. Thanks.

---

### Post by sazaliwahid on 2008-08-20
> **herschen said:**
> I followed the instructions in this post: [http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045"). I've disabled  roaming mode and put in all the information, Network name-linksys with no password protection. I'm running into the same problem every time. I open System-Administration-Network and click Unlock. I check the box next to Wireless Network and I click close. I'm not able to connect to the Internet and when I reopen the Network window, wireless is unchecked. I'm using Hardy Heron. Thanks.

You still have the problem? I faced the same problem too. I stumbled on a forum that asked me to use ndiswrapper to install the windows driver supplied by linksys. It worked like a charm. The following link gave me a step x step instruction to install the adapter using ndiswrapper.

[http://www.lugmanipal.org/2008/04/27/installing-ndiswrapper-on-ubuntu-804/#comment-162](http://www.lugmanipal.org/2008/04/27/installing-ndiswrapper-on-ubuntu-804/#comment-162)

good luck!

---

### Post by sazaliwahid on 2008-08-20
One more thing, I installed the ndiswrapper and driver on a freshly installed Hardy.

Best!

---

### Post by brockangelo on 2009-08-15
This worked for me in 8.04 on 8.15.09. Awesome!

---

