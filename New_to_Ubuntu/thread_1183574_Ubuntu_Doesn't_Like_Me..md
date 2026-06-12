---
title: "Ubuntu Doesn't Like Me."
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Frombie on 2009-06-10
I have now installed Ubuntu (9.04) twice on my laptop from two different downloads as well as trying to boot from a third download of a live CD.

The problems is the same with all, Ubuntu loads and then freezes. I get horizontal lines across my screen and I am unable to move the cursor with either the mouse or touch pad.

I've run the Live CD on my desktop without problems, so I think I can eliminate a corrupted download.

1. What suggestions do you have for installing Ubuntu on my laptop?

2. How can I delete the Ubuntu install, without having to re-install Windows?

3. What do you recommend for manual partitions for Ubuntu?

Cheers
Frombie

---

### Post by arochester on 2009-06-10
What is the make and model of your laptop? It might have specific requirements.

---

### Post by lisati on 2009-06-10
How much RAM does your laptop have? You might find that the "alternate" installation disk might work better if you have a lower amount of RAM.

---

### Post by Frombie on 2009-06-10
The laptop is an Averatec 6700 (upgraded) with 1 GB RAM.

When the laptop freezes, all I can do is power off and reboot. Sometimes if freezes as soon as I log in, other times as soon as I try to load a program or open a file.

---

### Post by Celauran on 2009-06-10
What's the video card like? What are Jaunty's default compiz settings?

Can you use the keyboard? If so, try alt-F2 and run top to see what (if anything) is eating your CPU and causing the slowdown.

---

### Post by Frombie on 2009-06-10
The video card is an onboard ATI Radeon Xpress 1100.

The computer doesn't slowdown. It freezes totally, there is no response from the keyboard at all.

When I've installed Ubuntu I have let Ubuntu automatically partition free space alloted for the OS (20 GB). It makes the swap partition around about 600 MB. From what I have read it should be about 2 GB, this is why I've queried manually partioning the drive.

Cheers

---

### Post by Tholley on 2009-06-10
I have had the same problem (hopefully all in the past now), I had to re-install 3 times and now it seems like the third has stuck. It seems like it could be something to do with ATI Radeon cards.
My Ubuntu would work for a week or so, until I would possibly install some media apts (not sure which) and the next day it wouldnt boot properly. Here are the instructions I used to manually re-install that worked for me.
 
when you get to the partitoning section:

1. select manual editing of partitions
2. you will see two partitions that are Ubuntu
3. select the ext3 or ext4 partition (whichever format was used)
4. click "edit partition"
5. select "Ext3" from where it says "do not use this partition" (its a drop down menu) and select the format option
6. select "/" from the mounting drop down menu.
7. click ok.
make sure that the box is checked for formatting on the Ext3 partition.
dont worry about the "Swap area" because it doesnt change.

then continue installing from there. 

that should work.

then you'll have Ubuntu back and working hopefully
 
Good Luck!

---

### Post by Frombie on 2009-06-10
I'll try again this afternoon when I have a little more time to focus on what I'm doing.

I do worry about the "Swap" partition though, as it is only 690 MB (I just checked the partition size). My gut tells me that I should be a little more generous in this area, so would like to take it up to the 2 GB that is recommended.

---

### Post by SunnyRabbiera on 2009-06-10
Also try other distros, where ubuntu might fail another might succeed.

---

### Post by Sir Jasper on 2009-06-10
Hi,

If you don't use hibernation it is unlikely you will need a large Swap partition.

You can resize it at any time using Gparted from your live CD. 

My regards

---

### Post by shae on 2009-06-10
I believe that is a problem with that card, open source drivers, and compiz.  My suggestion is to disable compiz.  That will reduce the frequency of that problem, but you may still encounter it from time to time.

---

### Post by xavierp94 on 2009-06-10
> **Frombie said:**
> I have now installed Ubuntu (9.04) twice on my laptop from two different downloads as well as trying to boot from a third download of a live CD.

The problems is the same with all, Ubuntu loads and then freezes. I get horizontal lines across my screen and I am unable to move the cursor with either the mouse or touch pad.

I've run the Live CD on my desktop without problems, so I think I can eliminate a corrupted download.

1. What suggestions do you have for installing Ubuntu on my laptop?

2. How can I delete the Ubuntu install, without having to re-install Windows?

3. What do you recommend for manual partitions for Ubuntu?

Cheers
Frombie
I gave my friend a copy of Ubuntu Hardy Heron and he got the same problems too! His computer after a minute or two would get frozen so the only choice he had was to shut it down. I told him to update because sometimes that may fix problems like those and next day he came to me a told me that it worked. Try updating before you try uninstalling it.

---

### Post by Frombie on 2009-06-13
I re-installed Ubuntu again. After logging in all I get now is a blank screen. I do have a curser though.

---

