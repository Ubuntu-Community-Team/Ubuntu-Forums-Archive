---
title: "I need some help on a Vostro 1000?"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by BioBlazer on 2008-10-06
Well.. I have this problem, I can't get my Wireless working. I'm using the Intrepid Ibex. On a Vostro 1000, I think the Wireless card is a BCM4311. I can't install ndiswrapper, when I run sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common, it tells me that ndiswrapper is already installed. It isn't installed, and I know this, because when I run any command related to it, the message that comes out says that ndiswrapper isn't installed.

I'm kinda new to this whole Linux thing, and I'm not really sure what I should do in this situation. Any help would be welcome. Thanks!

---

### Post by nixscripter on 2008-10-06
Try adding the --reinstall flag to make apt-get do it anyway. In other words: ```
sudo apt-get --reinstall install ndiswrapper-utils-1.9 ndiswrapper-common
```

---

