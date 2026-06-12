---
title: "Very slow Internet with BCM5751M and tg3"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by pjenazabrijanje on 2008-01-02
Hi all!
I switched to Suse a few months ago and three weeks ago to Ubuntu 7.10 on my work laptop (a very bold move) and I have a few problems...

Internet connection from my company's network is VERY slow: I get 170 kbps at most while everybody else can easily get 6000 kpbs. 

I have ThinkPad T43 which has BCM5751M ethernet card which uses tg3 driver.

The problem is present only with Internet connections from my company's network: local LAN connections are fast enough (to and from samba shares etc).
Also, I get 6000 kbps on ADSL line from another company.'s network...
And also, I get 6000 kbps on our network when I boot to Windows....
(I used [www.speedtest.net](www.speedtest.net) to measure this)

So, I can conclude that the problem:
- is not in the Ethernet card itself because the speed is OK locally
- could be the tg3 driver problem because it works on Windows
- is not in the Linux driver per se because it works on another network

So, it must be the combination of our switch and this driver. We have Planet switch GSW-2401. I normally connect through a hub, but I've tried connecting directly to the switch and it's the same...

I've tried using ethtool to disable autonegotiation, and I've tried setting different speeds and (I think) every possible combination of speed, TX and RX - to no avail..

Also, there are no dropped packages and no error messages in the log files...

I also tried sniffing the traffic on my machine with Wireshark but didn't see anything suspicious...

Does anyone have any suggestions or experience with something similar? What else can I try (besides switching back to Windows)?


I don't want to switch back but small things like this are really driving me nuts...


Thanks in advance..

---

### Post by pjenazabrijanje on 2008-01-03
Already on 6th page??

---

### Post by pjenazabrijanje on 2008-01-03
Anyone?

---

### Post by pjenazabrijanje on 2008-01-04
Going once!

---

### Post by pjenazabrijanje on 2008-01-14
I have new info regarding this problem...

I tried to boot Ubuntu 7.10 on my colleague's laptop T61, which has another card (I forgot the name of the card - intel and some numbers) that uses e1000 driver. And guess what? The same problem!

That could only mean that the Linux kernel's got issues with this Planet switch...

Any ideas? (my hopes aren't too high that I'll get an answer but have to try...)

---

