---
title: "Why is Ubuntu overwhelmed with wireless problems?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by pokipoki08 on 2008-06-24
Everyday, this forum is filled with problematic wireless connectivity threads.

Is this a distro-specific issue?

Are the updates tackling this issue at all?

Maurice

---

### Post by dmizer on 2008-06-24
there's probably several reasons for this, but it's been my observation that the vast majority of wireless issues are user based rather than system based.  or in other words, the most common problem is simply lack of experience with linux.  the poster either doesn't know how (or has not taken the time) to find the information necessary to get their card working, or doesn't understand the howto's that do exist for their card.

this is obviously not always the case, but i think it's the largest contributor to the volume of wireless connectivity threads.

---

### Post by pokipoki08 on 2008-06-24
Perhaps something can be done to the Live CD?

My wifi card work fine in the Live CD but not after I installed Hardy. 

In addition, Firefox homepage should add Ubuntu forums, especially the Wifi Howtos.

Maybe we should have include a poll to specify which wifi adaptor works out of the box. I remember seeing such a list somewhere.

---

### Post by dmizer on 2008-06-25
> **pokipoki08 said:**
> Perhaps something can be done to the Live CD?

My wifi card work fine in the Live CD but not after I installed Hardy. 
you should run the live cd again, and take a look at how the card is configured under the live cd with this command:
```
lshw -C network
```
and compare it to the same command when you're booted into your hardy install.

> **pokipoki08 said:**
> In addition, Firefox homepage should add Ubuntu forums, especially the Wifi Howtos.
actually ... i believe this is already the case, but it's been a while since i've installed so i'm not positive.  i believe it appears as an option when you open firefox the first time.  it's also in the firefox bookmarks by default.

> **pokipoki08 said:**
> Maybe we should have include a poll to specify which wifi adaptor works out of the box. I remember seeing such a list somewhere.

if you look at the sticky threads posted at the top of the "[Networking & Wireless](http://ubuntuforums.org/forumdisplay.php?f=336)" forum, you will find the "[Supported wireless cards list](http://ubuntuforums.org/showthread.php?t=370108)".

---

### Post by kevdog on 2008-06-25
Once you've been around the block for a while, wireless isn't so hard with Linux. Of course this took me months to get to this point.  It is more difficult in Windows, however part of the difficulty was learning a new OS and having to use very foreign commands at once which I totally didn't understand.  Atheros (some) and many Intel chipsets work directly without a lot of fuss.

---

### Post by xXOtherPeoplesWasteXx on 2008-06-25
I agree with ***Kevdog***, other than the fact that this is my first trip around with anything Linux. I was hell-bent on Windows, until I realized that I just wanted something different.


Now I almost feel like I'm in a boat but with no water around.
                     (**safe**)

---

