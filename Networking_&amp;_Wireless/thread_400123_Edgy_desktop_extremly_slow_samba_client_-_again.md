---
title: "Edgy desktop: extremly slow samba client - again"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by lovas on 2007-04-03
Hi Everyone,

We have windows environment at the company. Since we are mostly Java developers I've decided to migrate to Linux, also I needed the experience. Most of the things went quite fine but reaching network share was/is the hell.

Just telling you: I'm a really rookie in Linux
That's all: having Edgy (Kubuntu) on my machine (Asus P5PE-VM all-in-one) I can hardly access shared folders on remote Windows machines. All transfers are extremely slow, while booting up w/XP the transfer rate is beyond 3MB/s. Other network related services are definitely ok -- only samba is the problematic.

I've tried many things suggested on many sites including modding the config several ways, mounting. None of them helped. The symptom was the same: reading some kbytes... waiting for few secs... and so on. Copying 1MB takes minutes.

So the big questions are:
-- Can somebody help me???
-- How can anyone take the idea of migrating workstations to linux seriously while there are problems like this?

Thanks

---

### Post by lovas on 2007-04-04
*bump*

Isn't that important? IMHO the real "enemy" of the desktop linux systems is the poor quality or the problematic behavior of some components. Edgy was a really positive surprise for me, but I can't recommend it to others until I resolve this very MS network related issue

---

### Post by lovas on 2007-04-21
Finally I solved it using the doc [here]("http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html")

None of the browsing applications helped but mounting with the options decribed in the section about the correct packet size

---

