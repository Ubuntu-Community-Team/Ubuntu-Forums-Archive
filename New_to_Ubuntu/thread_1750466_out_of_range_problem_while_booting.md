---
title: "out of range problem while booting"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by miz0ooo0 on 2011-05-05
[SIZE=3][B]hi 
i have a problem in setting up ubuntu 10.10 with nividia 5200 vga card because out of range problem 
i installed it before with old ATI 64 mb vga card but this card is not available now 
so i asked for a solution for this problem 
(plz check attached video [/B][/SIZE][http://www.youtube.com/watch?v=z4vbnrbaqBk](http://www.youtube.com/watch?v=z4vbnrbaqBk)[SIZE=3]**)**[/SIZE]
[SIZE=3][B]thnxxxx for advance

[/B][/SIZE]

---

### Post by miz0ooo0 on 2011-05-06
[SIZE=3][B]any one can solve this problem ?
the attached  link shows the problem plz check 
[/B][/SIZE]

---

### Post by Redblade20XX on 2011-05-06
so you installed the ati drivers for the ati card but decided to replace the ati card with a nvidia card?

---

### Post by miz0ooo0 on 2011-05-07
[SIZE=2][B]no , the ATI card has a problem in preview ,i ignored this problem when installing ubuntu but after installing it , it was so hard to continue using this card with this problem so i decided to switch this card by the nivida one ,so i searched for any method to use the nividia card without out of range problem and finally i got a solution by typing a code in terminal which adjust the resolution to work with this card (nividia), but in this case i installed ubuntu before
but now it's really bad problem i cant start installation because of out of range problem 
[/B][/SIZE]

---

### Post by Wim Sturkenboom on 2011-05-07
One solution I see (there might be others) is to use the alternate CD to do the install. It willallowyou toinstal in text mode.

---

### Post by miz0ooo0 on 2011-05-07
can you explain this ; what is the alternative cd ,and how to use it ?

---

### Post by Wim Sturkenboom on 2011-05-08
It's the non-live version of the install CD. Boot from it and install; it uses text-based graphics instead of real graphics.

---

### Post by Hedgehog1 on 2011-05-08
Just watched the video.

The issue is the default video size used by the LiveCD/LiveUSB is larger than your monitor is capable of showing.

The 'OUT OF RANGE' error is from your monitor, letting you know it is getting an input that is outside of what it can display.

This happens when the video card go can go much larger then the monitor can.

Do you have access to another monitor that has a higher resolution?

***The Hedge***

:KS

---

### Post by miz0ooo0 on 2011-05-08
[SIZE=3][B]unfortunately this is only monitor available for me  ,so there is no way to do this installation except by  changing either monitor or video card ?
[/B][/SIZE]

---

