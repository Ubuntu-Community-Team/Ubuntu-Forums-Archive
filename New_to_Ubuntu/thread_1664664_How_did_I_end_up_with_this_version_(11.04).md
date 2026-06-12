---
title: "How did I end up with this version (11.04)?"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by itsols on 2011-01-11
Up until my hard disk crashed, I was on 9.04.

Then with the new install I THOUGHT (and I'm pretty sure about it) that I had installed 10.04 or 10.10.

But suddenly I have found myself having Ubuntu 11.04 - the Natty Narwhal - and I can't even pronounce that last word - lol!

Is this something I did nor is this a mistake that I downloaded the wrong installation. It's funny that it says I INSTALLED it in the FUTURE (April 2011)!

Regardless of this mishap, it seems to be a pretty stable installation. But this is my work machine and I'm a little worried about the safety/security of my work.

---

### Post by Quackers on 2011-01-11
Please post the output for ```
uname -a
``` in the terminal.

---

### Post by Paqman on 2011-01-11
Where did you get the ISO you used to install? Can you post the output of:
```
uname -r
```

---

### Post by itsols on 2011-01-11
output of uname -a
Linux khalid-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

I've always taken the ISOs from the Ubuntu website.

---

### Post by Quackers on 2011-01-11
Please try ```
uname -r
``` as Paqman suggested.
I believe, though, that 2.6.35 kernels are for 10.10. There is a known bug which causes 10.10 to be called 11.04, temporarily.
I may be wrong there, 2.6.35 kernels were for 10.04 methinks.

---

### Post by Bucky Ball on 2011-01-11
> **Quackers said:**
> Please try ```
uname -r
``` as Paqman suggested.
I believe, though, that 2.6.35 kernels are for 10.10. There is a known bug which causes 10.10 to be called 11.04, temporarily.

Hi Quackers and yes, that is correct on both counts. Itsols, is everything working as it should? The 2.6.35-24 kernel is extremely problematic on some machines at the moment and your issue is a known bug. See here for more info and you might like to add your thoughts:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

---

### Post by itsols on 2011-01-11
uname -r gives this:

2.6.35-24-generic

I can understand the error that 10.10 is recognised as 11.04. But how come the release date is different?

Anyway, that's a good thought - thanks for the tip. I really did not come across any such bug report - not that I searched :)

---

### Post by wojox on 2011-01-11
See here [You may have a bug]("http://ubuntuforums.org/showpost.php?p=10329476&postcount=6")

---

### Post by Bucky Ball on 2011-01-11
That is the problem kernel. Please reread my post #6 and report back any issues you are having, if any, or add to relevant bug reports ...

I'm interested to know if everything is working - despite the fact it is giving the totally wrong version number (it is 10.10)  - and I'm sure the developers would be too ...

---

### Post by kaldor on 2011-01-11
I know of a bug with 10.10 that shows your version as 11.04 for some reason. Don't worry, you're using 10.10 :)

---

### Post by wojox on 2011-01-11
[It's a bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248")

---

### Post by itsols on 2011-01-11
Yes, Bucky Ball, everything outwardly seems to be just fine. In fact the terrible screen flicker (when the mouse was moved) is no more. So that's a GREAT improvement. And I can plug in a second screen as well without flickering.

But there's a new issue and I've addressed this in another thread. That is, that every once in a while, the screen takes a 'dip' like a sleepy cat blinking its eyes. It's lasts for about a second and things are back. Actually, apart from this, there's no other issue.

I also used to have issues with Brasero but now all's good :)

But as usual, my intel graphics can't show any animation effects and as a developer, I hardly need those fancy stuff (although it'd be nice to have them).

---

### Post by itsols on 2011-01-11
Yes, it's a bug!!!

Thanks everyone for your support. So in conclusion, I DO have 10.10 LTS right? I'm pretty sure this is what I got. But many have told me that 10.10 LTS is not on the site.

Anyway, it's a relief to know that I haven't messed up anything (yet) - cheers!

---

### Post by Bucky Ball on 2011-01-11
In that case, no panic. The bug squad would surely like to know your thoughts, machine and model, and kernel. 

The fact that it is calling itself 11.04 will be sorted in an update soon no doubt.

Have you tried System >Admin >Additional Drivers? Is there a graphics driver in there?

Also, get updates and search in Synaptics for 'ubuntu-restricted-extras' then install. That will give you Java and other things. Third party so if you want to use open-source only, omit that! ;)

> In the past I built solutions looking through a Window. But now I see how big the world is.             Nice. As a long time MS user and a Linux convert since 2007; my sentiments exactly.

---

### Post by itsols on 2011-01-11
Thank you once again... And I'm always more than willing to report bugs and put things right where possible.

It's been a while since I bid farewell to Windows. Now it's Ubuntu all the way... The path is not smooth but once we have all pieces of the puzzle in place, it's pretty neat.

---

### Post by Ekeluo on 2011-01-11
You don't have effects? I'm running 10.10 on a Compaq a935 with Pentium T2370 and X3100 graphics and i have effects. Try x-updates ppa. The intel igp drivers from there are quite a bit more recent than the main repo ones.

Then again i did have effects when i tried the live cd...

---

### Post by Bucky Ball on 2011-01-11
> **itsols said:**
> The path is not smooth but once we have all pieces of the puzzle in place, it's pretty neat.

+1. Once you've got the machine the way you want it it stays that way until *you* break something (generally, although updates for 10.10 are unpredictable which is why I stick with the LTS releases).

At the mo, I have a number of machines, so LTS on the others as they are 'production' machines and can't screw up and 10.10 on my laptop which I can screw with until uni starts again in a month or so! As long as I put it all back together by then I'm tryin' anything! lol

Good luck and enjoy the ride. ;)

---

### Post by hansolo4949 on 2011-01-11
You may have accidentaly downloaded the beta version of Natty. It's a pretty cool OS, but not stable enough for me at this point. You will need to download 10.10 Maverick Meercat from the Ubuntu website. I hope that helps!

hansolo4949

---

### Post by Bucky Ball on 2011-01-11
> **hansolo4949 said:**
> You may have accidentaly downloaded the beta version of Natty. It's a pretty cool OS, but not stable enough for me at this point. You will need to download 10.10 Maverick Meercat from the Ubuntu website. I hope that helps!

hansolo4949

When posting please read all previous posts *first*. This has been well and truly covered in this thread. It is a known issue with 10.10 and there are bug reports. OP *is* using 10.10. There is no 'accidentally' downloading 11.04.

Take no offence as none meant. ;)

---

