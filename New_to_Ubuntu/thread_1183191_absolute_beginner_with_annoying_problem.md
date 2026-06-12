---
title: "absolute beginner with annoying problem"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Vyse_23 on 2009-06-09
So, I'm brand new to Linux. I got a more computer-savvy friend to partition my drive with Vista on one side and Ubuntu on the other. Now, however, on the Ubuntu side, I'm being told that my home folder is completely full. I haven't installed anything to the folder, so that should be impossible.

Help??

---

### Post by izizzle on 2009-06-09
Do you know how much space your friend allocated to the Ubuntu partition?

---

### Post by Vyse_23 on 2009-06-09
Yeah, it was 50 gigs for each OS and 100 for storage, accessible by both OSes.

---

### Post by wpshooter on 2009-06-09
> **Vyse_23 said:**
> Yeah, it was 50 gigs for each OS and 100 for storage, accessible by both OSes.

That was probably way too much to allocate to Ubuntu O/S.

Which O/S was installed first and which one was installed second ?

---

### Post by Vyse_23 on 2009-06-09
The computer came with Vista, Ubuntu was installed after the partitioning.

---

### Post by 123456789123456789123456 on 2009-06-09
Check the partition, see how much it is saying you have.  Ubuntu when it installs, if you tell it to install on a 50gb parititon, it will create two new partitions, use one for swap, and one for Ubuntu.  It should not have used a whole lot for swap partition though.  post the information about partitons that you get from the system, you can use the partition editor under system I believe to get this data.

---

### Post by llamabr on 2009-06-09
Post the output of:

```
 df -h && du -h | tail
```

and, before you come back, navigate to your home directory, and type ls -aL, and make sure there's not something huge in there.

---

### Post by wpshooter on 2009-06-09
> **LaughingDog said:**
> Well imagine my embarassment. Became an Ubuntu-er moments ago. Thought I was doing OK. Then this. Feel like I wondered into someone's living room during a "Son's Of Silence" meeting. Not sure I'm in the right place and have no idea where I stand on the Java scoreboard. As long as I'm here........I too have a problem before getting to the starting gate. How do I move everything in "C" drive to "F" drive so I can use "C" for Linux install....help?......don't shoot. Bye for now. I'll be annoying you soon again, I imagine. Speaking of "Imagine" wasn't that a great........................

What are C drive and F drive ?

Are these 2 physical drives or are they just logical drive "letterings" ?

---

### Post by dioltas on 2009-06-09
> **LaughingDog said:**
> Well imagine my embarassment. Became an Ubuntu-er moments ago. Thought I was doing OK. Then this. Feel like I wondered into someone's living room during a "Son's Of Silence" meeting. Not sure I'm in the right place and have no idea where I stand on the Java scoreboard. As long as I'm here........I too have a problem before getting to the starting gate. How do I move everything in "C" drive to "F" drive so I can use "C" for Linux install....help?......don't shoot. Bye for now. I'll be annoying you soon again, I imagine. Speaking of "Imagine" wasn't that a great........................

Surely trolling?

---

### Post by UbuntuNerd on 2009-06-09
> **LaughingDog said:**
> Well imagine my embarassment. Became an Ubuntu-er moments ago. Thought I was doing OK. Then this. Feel like I wondered into someone's living room during a "Son's Of Silence" meeting. Not sure I'm in the right place and have no idea where I stand on the Java scoreboard. As long as I'm here........I too have a problem before getting to the starting gate. How do I move everything in "C" drive to "F" drive so I can use "C" for Linux install....help?......don't shoot. Bye for now. I'll be annoying you soon again, I imagine. Speaking of "Imagine" wasn't that a great........................

?????

---

