---
title: "Wine Slowness"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Pikzilla on 2009-11-01
Hiya. I switched to Linux a few days back, and have been adjusting to using the Linux equivalents of Windows applications. However, as an aspiring game Dev, there are certain applications which, while not having Ubuntu equivalents, are still needed by me. My solution, of course, was WINE. I've heard that WINE runs .exes faster than XP, but I have been experiencing the opposite. WINE opens and runs the application okay, but when I want to run a test play of the game I'm building, I get monstrous amounts of lag. So, what's my best bet for optimizing speed? Is there anything I can do to get WINE to run faster, or will a virtual machine be more quick?

---

### Post by Pikzilla on 2009-11-01
Sorry, but bump

---

### Post by Soulcage on 2009-11-01
Give this a read. [http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by Pikzilla on 2009-11-02
I looked at it; The only useful info there was was an incomplete report, staing that Multimedia Fusion 2 (the program I'm trying to use) runs flawlessly, although much was not WINE-tested.

---

### Post by Pikzilla on 2009-11-05
Okay, I just checked, and the build runs smoothly when I don't move the character, but not when I start shooting like crap.

---

### Post by Mark Phelps on 2009-11-06
>  ... but when I want to run a test play of the game I'm building, I get monstrous amounts of lag. 
Games are a special case because the video driver comes into play and you have entirely different video drivers in Linux than in MS Windows. 

If you have one of the "legacy" ATI video cards/chips, you're running the open source drivers, and in that case, gaming will be a major disappointment.

If you're running an Nvidia card, check for restricted drivers for your card.  Installing them will dramatically improve game play.
>  ...will a virtual machine be more quick?
Definitely -- NO.  A VM introduces another layer of SW and the video performance will be worse, not better, than you're experiencing now.

---

### Post by Pikzilla on 2009-11-07
How do I find my video card? I ran "su -c "lspci | grep VGA"" but it gave me "su: Authentication failure"
Lil' help?

---

### Post by Pikzilla on 2009-11-07
Oh, here it is:
VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by fhmanas on 2009-11-07
My experience with Wine is great, I did do some modifications to my program to make it work in Wine but this was pre-1.0 version of Wine.  Performance was comparable, sometimes better than on native windows.  Although, I do have to point out that my program was an database/office application and not a game.  

If you do have issues with Wine, it would be better to post it in the official Wine site ([http://www.winehq.org](http://www.winehq.org)) site, they were able to help solve some of my problems when I was trying my program on Wine.

Keep at it, you won't regret it.

---

