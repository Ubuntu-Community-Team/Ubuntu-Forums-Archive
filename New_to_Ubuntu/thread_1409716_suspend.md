---
title: "suspend"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by degarb on 2010-02-17
Neither suspend or hybernates works on this laptop.

Well, they work but waking up doesn't.    Looks like if I suspend.  return wakes up computer but monitor doesn't come on.

---

### Post by switch10 on 2010-02-17
Some hardware isn't supported.

How big is your swap partition?  Make sure it is twice as much as your installed RAM.

---

### Post by degarb on 2010-02-17
> **switch10 said:**
> Some hardware isn't supported.

How big is your swap partition?  Make sure it is twice as much as your installed RAM.

nah about 3/5 size of ram.  But Small hd.

---

### Post by walt.smith1960 on 2010-02-18
> **switch10 said:**
> Some hardware isn't supported.

How big is your swap partition?  Make sure it is twice as much as your installed RAM.

I don't believe swap matters with suspend. I can suspend without any swap space at all. Hibernate is another matter-no swap partition no hibernate option. The "it appears to wake up but the screen is blank" may be an issue with video. I was fighting this problem with an Nvidia AGP graphics card. I think the card may have been faulty, it's replacement should be here in the next few days. The problem I was having is that the machine would suspend and resume IF it was in suspend only a few minutes. If it was in suspend for a few hours, the P/S fan, keyboard and USB devices would come alive, the video would not.

---

### Post by degarb on 2010-02-18
> **walt.smith1960 said:**
> I don't believe swap matters with suspend. I can suspend without any swap space at all. Hibernate is another matter-no swap partition no hibernate option. The "it appears to wake up but the screen is blank" may be an issue with video. I was fighting this problem with an Nvidia AGP graphics card. I think the card may have been faulty, it's replacement should be here in the next few days. The problem I was having is that the machine would suspend and resume IF it was in suspend only a few minutes. If it was in suspend for a few hours, the P/S fan, keyboard and USB devices would come alive, the video would not.

Only difference here is it doesn't matter how long.   I don't think I will buy a new video card for my laptop.   Though I bet the new ones are much more powerful than an old one. 

Sounds like the driver may not be perfect, so might work with next release.

---

