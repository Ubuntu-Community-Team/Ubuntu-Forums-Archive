---
title: "Logical partition &amp; swap size Qs"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by snl on 2009-08-10
I am planning to make a clean install of ubuntu on a dual boot laptop with Windows Vista. In the past, I have always had / root on primary partition and swap and /home on logical partitions. If this time I have all /, /home and swap on logical partitions, will there be any performance difference or any other disadvantage by having Ubuntu running on logical partition?

I have 4GB RAM, how much should the swap space be? I know that the rule of thumb is twice the actual RAM so do I need 8GB swap space?

Thank you.

---

### Post by mapes12 on 2009-08-10
In my experience primary partitions (max 4 inc an Extended partition) compared to Extended then Logical partitions does not affect the speed of my system.

Swap - yes, 2x RAM used to be the norm but that was in the days when RAM was small. There is now a school of thought that 1x RAM is OK.

---

### Post by raymondh on 2009-08-10
> **snl said:**
> I am planning to make a clean install of ubuntu on a dual boot laptop with Windows Vista. In the past, I have always had / root on primary partition and swap and /home on logical partitions. If this time I have all /, /home and swap on logical partitions, will there be any performance difference or any other disadvantage by having Ubuntu running on logical partition?

I have 4GB RAM, how much should the swap space be? I know that the rule of thumb is twice the actual RAM so do I need 8GB swap space?

Thank you.

No difference for me (whether it be primary or logical).  I, as well have 4GB RAM.  My swap is 1.5GB and I rarely get to use it all ... even when running a video editing app.

---

### Post by snl on 2009-08-10
Thanks for a fast reply.

I read somewhere that in order for a laptop to go into hibernate mode, I need swap space more than the actual RAM. So if the swap space is the same size as RAM, i.e. 4GB in this case, will there be any problem with hibernate mode?

Thanks.

---

### Post by raymondh on 2009-08-10
> **snl said:**
> Thanks for a fast reply.

I read somewhere that in order for a laptop to go into hibernate mode, I need swap space more than the actual RAM. So if the swap space is the same size as RAM, i.e. 4GB in this case, will there be any problem with hibernate mode?

Thanks.

With the apps I run and at my RAM (4GB) and with 1.5GB swap, I have had no problems/difficulties hibernating.  Now, if I had say, 512mb RAM .... then I can foresee hibernating problems as I consider SWAP a spill-over-catch-basin for RAM.....again because of the apps I run (editing videos, music, pics).

Nevertheless, it is easy to create a swap file as well, should you realize you need more swap space.  See the [swap FAQ]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by Paddy Landau on 2009-08-10
How big is your hard drive? As you have Vista, I'm guessing that it's a new computer, and a 4Gb swap won't make any significant difference to you.

If you have a 4Gb swap, you're guaranteed to have enough swap space for hibernation. With 4Gb, though, it's extremely unlikely that your computer will use any swap at all except when hibernating.

---

