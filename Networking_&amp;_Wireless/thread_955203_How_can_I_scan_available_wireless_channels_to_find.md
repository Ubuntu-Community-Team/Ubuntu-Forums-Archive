---
title: "How can I scan available wireless channels to find the best one?"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by joe56 on 2008-10-22
There are quite a few wireless networks in range. Is there a simple way to find the 'quietest' channel?

---

### Post by lisati on 2008-10-22
I currently have two wireless access points at home (partly due to putting a redundant router to work to help avoid buying extra cabling) - the one nearest to my Ubuntu machine shows a stronger signal, which is the one I use for it. 

I would suggest (a) choosing from the networks you have permission to use first, and (b) go for the strongest signal

---

### Post by joe56 on 2008-10-22
I should have been more specific. I want to know what channel I should use for my own network. I live in close proximity to ~6-7 other networks and I would like to know which channel has the least interference.

---

### Post by tgalati4 on 2008-10-22
Install wifi radar.  Search radar in synaptic.

---

### Post by bionnaki on 2008-10-22
iwlist x scan 

x being your interface (i.e. ath0)

---

### Post by topbayder on 2012-03-15
> **tgalati4 said:**
> Install wifi radar.  Search radar in synaptic.

Im hitch hiking on this thread but Wifi Radar worked perfectly to see what channels all the wifi netwroks in range of my house/lap top are using.

Thanks tgalati4

---

### Post by nevalain on 2012-10-20
> **topbayder said:**
> Im hitch hiking on this thread but Wifi Radar worked perfectly to see what channels all the wifi netwroks in range of my house/lap top are using.

Thanks tgalati4

This helped me also. Thanks!

I stubled to this problem after trying to fix my slow connection. It seems that 90% of my area wlans (about 10 of those) are on channels 1-7. I don't know how changing to channel 13 helps, but at least it is nice to know. If this really has effect I think "finding optimal channel" should be easily available in every Linux user's toolbox.

---

