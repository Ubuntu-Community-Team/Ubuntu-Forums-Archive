---
title: "Ubuntu 9.04: LG DVD-RAM GH22NP20 burning DVD extremely slow"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-04-29
Hi!

Today, I wanted to burn my first DVD (data) in Ubuntu. This morning, I still had 8.10 installed, and it didn't recognize the empty DVD I put into my LG DVD-RAM GH22NP20 drive at all, now I have 9.04 and it recognizes the DVD, but butning is PAINFULLY slow, it varies between 0.2x and 1.1x (max about 1.3 MB/s). What's going on here? Any ideas?

Thanks!
Matthias.

---

### Post by ohzopants on 2009-05-01
What program(s) are you using to burn the disk?
Is it just a straightforward data DVD?
This is a PATA drive, right? (At least I think that's what the P in the model number means, mine is the same but it's an S for SATA)
Is DMA enabled in your BIOS?

---

### Post by The Bright Side on 2009-05-02
I'm using Brasero, and yeah, it was a no-frills data DVD. My drive is PATA, and in my BIOS, DMA mode is set to "Auto".

---

### Post by interceptorV8 on 2009-05-02
i'm having the same problem with my HP dvd writer.  it writes at ridiculously slow speeds anywhere from 0.2x-1x.

---

### Post by The Bright Side on 2009-05-02
Hey interceptor, did you try different DVD types? As in, different brands, DVD-R and DVD+R? I only have Intenso (German brand) DVD-R 1x-8x here.

Nobody else has any ideas?

---

### Post by DenysT on 2009-05-02
I'm seeing the same thing writing data DVD's. But when I burned an ISO CD it worked just fine. It also worked real well in 8.10. Wonder what happened?

---

### Post by interceptorV8 on 2009-05-03
> **The Bright Side said:**
> Hey interceptor, did you try different DVD types? As in, different brands, DVD-R and DVD+R? I only have Intenso (German brand) DVD-R 1x-8x here.

Nobody else has any ideas?

well...  the thing is... i'm almost finished using the last of this cheap dynex brand from best buy.  they must have been a bad batch since  i've never had the problem before, BUT these bad discs ONLY work with the HP drive so i'm trying to finish them off so i can get to the better sony discs.  i only have a few more to go and if in fact IT IS the particular brand of discs causing the slow write speed, i'll find out after TWO more write sessions!

---

### Post by The Bright Side on 2009-05-04
Keep us posted! :-)

---

### Post by clownschoolphd on 2009-05-12
I have generic DVD burner (pulled from an old Dell i think).  I also *thought* it was burning slow as well.  Write speed was 700ish or .05x.

I let it sit for a bit and while it said 0% done and indicated the slow write speed, it finished in an appropriate amount of time and the disc was readable afterwards.

Something is screwy here.  I got the data I need and will revisit the issue later this week when I have more time.  But just as a heads-up, the issue may be with the GUI and not the behind the scenes action.

---

### Post by joey-elijah on 2009-05-13
If you're using breasero this isn't likely an issue with your hardware, but Brasero itself. I'm getting awfulyl slow speeds of 0.3x regardless of what i'm burning, as are lots of other people. 

Thread here [http://ubuntuforums.org/showthread.php?t=1150554&highlight=brasero+slow](http://ubuntuforums.org/showthread.php?t=1150554&highlight=brasero+slow)

---

