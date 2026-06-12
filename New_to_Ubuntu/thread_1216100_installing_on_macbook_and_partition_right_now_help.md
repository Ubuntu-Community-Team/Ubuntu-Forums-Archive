---
title: "installing on macbook and partition right now help"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by hollowtd on 2009-07-17
please help

I;m in the middle of installing 9.04 on my macbook 1.83 ghz computer. I have a 60 gig hd on the mac and about 24 gig free. I want to partition the hardrive so that each the tiger os and ubuntu os have 5-10 gig memory after installation. Can anyone tell me how to partition it? (Also, the screen is only taking up some of the screen. Will it extend to all the edges once installed or can I do it later?) Please help

---

### Post by hollowtd on 2009-07-17
I select advanced and don't know what to do afterward as there is a list of sizes and stuff.

---

### Post by earthpigg on 2009-07-17
> **hollowtd said:**
> (Also, the screen is only taking up some of the screen. Will it extend to all the edges once installed or can I do it later?)

i suggest figuring that out *before you* install! make a new thread with that specific problem in the thread title, so people who know about that stuff will come help you out.

your best bet is to select manually partition.

resize the OS X partition to 40 gigs.

that should give you a bunch of empty space.

make a new partition that is 2 gig partition as 'swap'.

make the rest an ext3 partition and set its 'mount point' to /.


that is a basic partition scheme that will achieve the desires you outlined in your post.


but, again, settle the touchscreen _*before*_ you install if that is important to you!

---

