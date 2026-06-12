---
title: "super noob cpu question"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by dan0804smith on 2011-07-26
so recently tried to under clock my 1.6ghz duel core dell mini 10v.  im not sure if i did it right but when i check the cpu clock rate it said that the cpus were running at 800mhz each.  has itr always been this way?  and if so how do i reverse it?

this is the site i used [http://ubuntudaily.blogspot.com/2011/07/extend-laptop-battery-life-with-cpu.html](http://ubuntudaily.blogspot.com/2011/07/extend-laptop-battery-life-with-cpu.html)

the reason why im concerned is that ia assumed that 1.6 ghz duel core ment that i had two cores each running at 1.6ghz.  is this wrong?

---

### Post by lkjoel on 2011-07-26
> **dan0804smith said:**
> so recently tried to under clock my 1.6ghz duel core dell mini 10v.  im not sure if i did it right but when i check the cpu clock rate it said that the cpus were running at 800mhz each.  has itr always been this way?  and if so how do i reverse it?

this is the site i used [http://ubuntudaily.blogspot.com/2011/07/extend-laptop-battery-life-with-cpu.html](http://ubuntudaily.blogspot.com/2011/07/extend-laptop-battery-life-with-cpu.html)

the reason why im concerned is that ia assumed that 1.6 ghz duel core ment that i had two cores each running at 1.6ghz.  is this wrong?
I think it has always been 800mhz.
I'm not an expert at under/overclocking, so I can't really help you with underclocking.

---

### Post by 3rdalbum on 2011-07-26
1.6GHz is the top speed of the processors. If they are virtually idle, they will drop back to (probably) 800MHz each to save power. If under load, they will shoot back to the full 1.6GHz each.

Run something CPU intensive such as audio or video encoding, and see what the reported CPU frequency is while this is running.

---

### Post by amjjawad on 2011-07-27
I would suggest to write down your CPU Model and then put that in Google and probably will give you Intel's Website as the first search result. Go there and read more about your CPU.

This is the BEST approach IMHO :)

Good luck ;)

---

### Post by CatKiller on 2011-07-27
> **dan0804smith said:**
>  tried to under clock my 1.6ghz duel core ... when i check the cpu clock rate it said that the cpus were running at 800mhz each.

the reason why im concerned is that ia assumed that 1.6 ghz duel core ment that i had two cores each running at 1.6ghz.

You've succeeded in what you were trying to achieve. What did you think would happen? Underclocking is running your processor at less-than-maximum speed for heat or power reasons. That is what you have done.

When you're running something that needs to have a faster processor it should come back up to speed automatically. The chances are it will spend almost all of its time in the underclocked state.

---

### Post by turtle153 on 2011-07-27
I did some tests, In the default state my CPUs spent most of their time at 800MHz and occasionally reaching 2.7GHz (the maximum). With the powersaving mode they spent practically all their time at 800MHz and never reached 2.7GHz.

---

