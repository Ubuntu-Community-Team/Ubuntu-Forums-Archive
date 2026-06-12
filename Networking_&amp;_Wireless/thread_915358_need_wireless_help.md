---
title: "need wireless help"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by johnny linux on 2008-09-09
Ok after installing ubuntu earlier today and it doesn't have my Belkin wireless drivers. so i went to their site to find that theirs only drivers for windows and mac So what should i do? and wine isn't on my computer O_o so i can't just get the drivers and run them.

unrelated but do i just burn wine as a data cd? 

edit:my wireless is belkin 802.11g-54mbs  f5d7050 raxwn450th

---

### Post by mrsteveman1 on 2008-09-09
That would be the dark grey, rounded-end USB stick, right?

Probably rev.4 i think (says on the back), because rev.3 was a zydas chip.

The drivers should be part of the kernel, and if they aren't you might find them in the ubuntu repo, but if not you'd have to compile them yourself (not too hard i can help if thats needed).

What does the output of lsusb say about the stick?

---

