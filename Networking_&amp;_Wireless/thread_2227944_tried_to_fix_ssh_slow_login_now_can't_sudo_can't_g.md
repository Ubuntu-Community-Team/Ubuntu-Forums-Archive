---
title: "tried to fix ssh slow login now can't sudo can't get into Recovery Mode"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Bradley_Lathan on 2014-06-04
Hey all,

relatively new to Ubuntu server and I tried a post on the forum to speed up ssh login.  it said to edit /etc/network/interfaces and add my domain, which i did but now i can't sudo.  so I tried to login to single user mode to fix this using the instructions listed at [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) but it just boots as normal, using a known good keyboard.  is the single user recovery mode different in 14.04 LTS? is it different when a RAID is involved?

Thanks.

---

### Post by TheFu on 2014-06-05
RAID complicates boots and behaves differently under different run-levels, I believe.  What sort of RAID - FakeRAID, HW-Driver RAID or SW-RAID?

Similarly, encryption complicates things too.

I avoid RAID on / and /boot to keep things simple.  This way, booting off any live-CD/Flash drive lets us mount the settings and modify them easily. It also makes physical security critical for servers, since anyone with physical access can do this too - change the root password and own the machine.

Can you post the complete interfaces file?

---

### Post by Bradley_Lathan on 2014-06-05
RAID complicates indeed! I have learned the hard/fun way.  I bought the server on craigslist and learning so much.  Timing was the trick.  I ended up getting the server to boot up into recovery mode and made necessary changes to fix everything wrong.  I might start from scratch with a normal sata drive for / to make booting faster.  what are your thoughts on this idea?

---

### Post by TheFu on 2014-06-05
I cannot recommend anything without much more information - like the questions I already asked.

---

