---
title: "Long boot time"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Grill on 2009-12-18
i have been running ubuntu 9.1 kar on this computer for about a month:guitar:. about a week ago my system locked up, i had to do a hard shutdown:(. this happens the next day. hard shutdown again and i have had a really long boot time since then. I've been looking around for others that had a similarly long boot time. i found to use bootchart, installed it but the readout is nothing like the well spread out log i had seen in the other post:confused:. which lead me to believe it is not the same problem but i don't really know how to make heads-or-tails of the chart. so any help i can get figuring out what got messed up and how to fix it would be much appreciated :)

---

### Post by Sir Jasper on 2009-12-18
Hi,

Either exactly or approximately; how long is a long time (and how long did it take before the problem)? Personally, I cannot read even a single word of your images even with a high zoom level.

My regards

---

### Post by prshah on 2009-12-18
> **Grill said:**
> it but the readout is nothing like the well spread out log i had seen in the other post:confused:. 

> **Sir Jasper said:**
> Personally, I cannot read even a single word of your images even with a high zoom level.

As mentioned, your posted bootcharts are unreadable; please post them as attachments, not as an embedded image in the post.

---

### Post by guvnr on 2009-12-18
> **Grill said:**
> i have been running ubuntu .............

*fried* it?

sorry.

---

### Post by Grill on 2009-12-18
sorry about not being clear on the time but i expected the chart to be readable and that all would be explained. from what i can tell the system "starts" to boot then pauses for 125 seconds then resumes booting just fine.
what happens is it pauses on a blank screen with a cursor and just sits there. then when the splash comes up it boots like normal, runs fine. the really odd thing that threw me off with the boot chart is that all but a few processes wait till 125s to start. the other post that i had seen the boot chart on was a lot more spread out (ie. the whole time was actually trying to boot not just waiting). i have no clue what all the boot processes are but here are the ones that boot before the 125s,
 "init" "kthreadd" "pdflush" "async /4" "async /5"
could all of these be  damaged? of so how do i fix it or do i need to reinstall?

---

