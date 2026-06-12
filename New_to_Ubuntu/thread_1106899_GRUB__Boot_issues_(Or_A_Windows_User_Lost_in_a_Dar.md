---
title: "GRUB / Boot issues (Or: A Windows User Lost in a Dark Forest....)"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by sugarpill on 2009-03-26
Please, please help me.
I've read so many guides, 
and I've come to so many road blocks, 
please just help me get out of this fog that I'm wandering.

Here's my issue: I am a poor defenseless Windows user (I know, I apologize in advance).  I installed Ubuntu onto a partition of my HDD a few months back in a misguided search for enlightenment.  As you can probably guess, I ended up fully neglecting my Ubuntu installation, and it sat dormant, until a few days ago.  Not thinking, and on a mindless quest to free up some much needed HDD real estate, I ended up deleting the partition that housed Ubuntu, marking it in my mind as something I just wasn't ready to experience yet.  Now, little did I realize, apparently GRUB was controlling my startup, so now when I turn on my computer, I end up getting a GRUB error 22.  Now, all i ask is that someone please help guide me back into a normal working Vista partition.  I've tried following so many guides, but most seem outdated, and I'm not sure they'll work on my Vista 64bit installation.  And then, other times, I keep getting continuously hung up on small issues.  As noted above, I am a complete uneducated newbie when it comes to doing things on a linux box (yes, even if that linux is ubuntu =\ ) so even simple things such as installing a program to try and get me out of this hole I'm stuck in have failed miserably.
  
So far, I found some posts on this forum, so I tried following the instructions that they had. I tried to install FixMBR while working under an 8.04 LiveCD, but I struggled with every step of the unpacking and compiling process, and then when I finally got everything to do what it should, I get make errors saying that it couldn't find the C Includes that the program needed :(:confused::(.  

Please, if someone could be so kind as to guide me back to a working Vista without a Vista installation CD, I would give you a million long distance internet hugs <3.

Thanks in advance.

tl;dr - File under: Stupid Windows User, Problem Exists Between Chair and Keyboard, Sadness and Confusion in the Land of Ubuntu.

---

### Post by SuperSonic4 on 2009-03-26
The easiest method would be to use the original vista disc if you have it and restore the bootloader on there

---

### Post by steve-shinn on 2009-03-26
No Vista disc, then download it from here :-

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

follow the instructions on how to create the disc from the iso image.

And then follow these instructions on how to repair the Vista mbr :- 

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Hope this helps

---

