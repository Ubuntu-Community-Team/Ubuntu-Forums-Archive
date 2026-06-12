---
title: "Are they working on the problem?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by bronner on 2009-02-22
Okay, I've been using Ubuntu for awhile now without any problems.
But recently I updated my Acer Aspire One laptop and everything went to hell. 
My wireless, wired and sound all stopped working, among other things.
So I figured, "I'll just downgrade from 8.10 to 8.04." 
Bad idea. It crashed my computer after restarting after the 8.04 update with something called "Kernel Panic!"
What I wanna know is, are these problems going to be fixed by Ubuntu 9? 
Because I love this operating system, but I don't love the way it's treating me right now. 
Sometimes love hurts...

Seriously though, is 9.04 going to correct these issues?

---

### Post by Rolcol on 2009-02-22
The issues are most likely coming from unsupported hardware.  As the hardware has been available to the consumer for a longer period of time, drivers will start appearing in the linux kernel.  9.04 will be using the latest kernel so newer hardware will be supported.  There's no guarantee that it will fix your problems 100%.

---

### Post by llamakc on 2009-02-22
> **bronner said:**
> Okay, I've been using Ubuntu for awhile now without any problems.
But recently I updated my Acer Aspire One laptop and everything went to hell. 
My wireless, wired and sound all stopped working, among other things.
So I figured, "I'll just downgrade from 8.10 to 8.04." 
Bad idea. It crashed my computer after restarting after the 8.04 update with something called "Kernel Panic!"
What I wanna know is, are these problems going to be fixed by Ubuntu 9? 
Because I love this operating system, but I don't love the way it's treating me right now. 
Sometimes love hurts...

Seriously though, is 9.04 going to correct these issues?

You had the option to boot into the previous kernel version (prior to the attempt to downgrade), and that very well may have solved your problem.

Have you tried the other kernel versions yet?

---

### Post by cwsnyder on 2009-02-22
Check out this YouTube video: [http://www.youtube.com/watch?v=8LY9iQo7sGk](http://www.youtube.com/watch?v=8LY9iQo7sGk)

It sounds like your drivers got updated during a kernel update.  You will probably NOT want to use the standard update sources for 8.04 or 8.10, rather the Netbook Remix sources, because you have a custom kernel to support your networking, sound, and camera hardware.

---

### Post by bronner on 2009-02-22
> **llamakc said:**
> You had the option to boot into the previous kernel version (prior to the attempt to downgrade), and that very well may have solved your problem.

Have you tried the other kernel versions yet?

Yes, it let me do everything normally, but the computer slowed to a crawl.

---

