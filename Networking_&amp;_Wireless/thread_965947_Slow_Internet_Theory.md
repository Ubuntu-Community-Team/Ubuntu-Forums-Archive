---
title: "Slow Internet Theory"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Sakura88 on 2008-10-31
Well, since the release of ubuntu 8.10, people all over the forum have been reporting slow internet connection in synaptic package manager. So I started to look for a fix for this too, but then I opened my laptop (hasn't been opened in a week) and noticed that this is also happening. I don't think it has to do with the actual distro version but a effect of the new release time. Am I crazy or something? comment? 


P.S. My laptop connection has been working awesome prior to this.

---

### Post by adamdoyle on 2008-11-02
Ive been getting the same thing with both of my wireless laptop. Browsing seems fine but downloading files from synaptic is very slow.  Anyone have any ideas?

---

### Post by priegog on 2008-11-02
Yes I do. I would think it is due to the release and the million sof people that surely were/are downloading stuff from ubuntu. 
In intrepid you can use the package apt-p2p. It's not exactly super quick, but when the servers are overloaded, you can get the packages you need no problem.

---

### Post by priegog on 2008-11-02
Dang it, this forum seems to be misbehaving. sorry for the double post.

---

### Post by jflaker on 2008-11-02
Yep

Solved it by having the system find the best server...

ADMINISTRATION>SOFTWARE SOURCES

on the UBUNTU SOFTWARE tab, click on the DOWNLOAD FROM button

Then click OTHER

Then select your country, then click BEST SERVER.

It will ping the servers to find the best return which is theoretically less busy.

Good luck

---

### Post by adamdoyle on 2008-11-02
Still having the same issue. Any files i try to download are slow, even though browsing seems fine .  I have the correct server selected in software sources, even opened up dmz in my router with static ips. Everything was fine until i download 8.10 , what is going on here?..Happening on 2 laptops , even tryed a different network .

---

