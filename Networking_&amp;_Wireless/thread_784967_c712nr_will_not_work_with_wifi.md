---
title: "c712nr will not work with wifi"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by brianslater on 2008-05-07
alright so I am trying desperately to get heron to allow my wireless built in to work. I have a c712nr and I do not want to boot into windows ever again, however my wifi doesnt work, can someone help me please!

---

### Post by chili555 on 2008-05-07
Many laptops come with a choice of several wireless cards, my Lenovo T60 came with a choice of three. Same for my Thinkpad T40. In some cases, manufacturers change components in the middle of a model run; maybe they can get it cheaper or better. It is therefor very difficult to figure out what wireless chipset you have. Let's ask the computer. Open up a terminal (Applications -> Accessories -> Terminal) and type:```
sudo lshw -C network
```One of the entries will relate to your ethernet card and one to your wireless. When you know the manufacturer and model of your wireless card, you can search this forum and see the methods many others have used to get theirs going.

Please post back if you get stuck.

---

