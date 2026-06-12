---
title: "Ubuntu dual boot with USB hard disk?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by rimshot4 on 2010-01-04
I installed Karmic Koala on my laptop last week and I'm very impressed. Blazing fast, stable, powerful. I love it. 

So now I'd like to move my WinXP desktop to a dual boot, but my HD is close to full. I have an old HD, but the IBM system I have was a corporate small box I got used and doesn't have a second HD slot. 

I do have an old HD, and I found a box kit online to convert it to a USB HD. Questions:

1. Is it possible to set up a dual-boot, having nothing but Windows XP on the internal HD and nothing but Ubuntu on the USB? I am picturing Ubuntu being our default OS; I only have to convince my wife :P
2. What would be he best way of going about this?

Thanks!

---

### Post by J V on 2010-01-04
Yes its possible, and better yet you can allocate more space on the internal to ubuntu too to give it more breathing space...

Could you say your harddrive sizes and how much space you need for windows?

---

### Post by rimshot4 on 2010-01-04
40 GB. My internal is also 40GB, and XP takes up some 34GB.

Older HDs both.

---

### Post by J V on 2010-01-04
hmm... It might be possible to get your / alone into that last 6 gigs, but probably best not to :)

Ok then, heres what you do...

Install ubuntu as normal, but when it asks for formatting, go to advanced...

Format the entire external drive as an extended partition...

Inside that there should be:
1: Swap partition of twice your ram size (2 gigs should be fine)
2: Ext4 partition of 8 gigs mounted to /
3: Ext4 partition of all the rest of the space mounted to /home

This means even when you upgrade or switch linux your data and settings will be saved on that third partition :)

Enjoy!

---

