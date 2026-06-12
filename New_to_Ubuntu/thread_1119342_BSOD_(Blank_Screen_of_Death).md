---
title: "BSOD (Blank Screen of Death)"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Strider11o7 on 2009-04-07
So my friend alex recently had his XP crash on him, the computer itself still seemed to be fine though. I convinced him to let him try Ubuntu 8.10, so i brought over my disk and popped it in to try the demo, it seemed to load up fine, but upon trying to log in, it went to a black screen with the loading cursor stuck in place.

I decided to forget it and just try installing it instead. After awhile of going through the process, including importing his old files and partitioning the hardrive, it finished and we try booting it up. Upon startup, it skips the initial Ubuntu-loading splash screen and goes straight to the default orange background with just a cursor that you can move around and nothing else. Anybody have any idea?

Please note i'm nowhere near qualified to understand what all i'm doing, i just enjoy Ubuntu's convenience.

---

### Post by juancarlospaco on 2009-04-07
Hardware problems, rams, conectors, or HD

---

### Post by jpoRS on 2009-04-07
Hello!

First thing first, check your disc for errors.  Should be an option when the live CD first comes to the menu.  9 times out of 10 that is what the problem is.

Good luck, and welcome to the community.

jim

p.s. don't sweat your inexperience.  We all knew nothing at some point.

---

### Post by robert shearer on 2009-04-07
What graphics card is used?  or onboard graphics?
 
 If it is older hardware and the card is less than 8Mb then the symptoms you describe I have encountered.

Can you try another graphics card and boot up with the live cd?

It would be useful if you could post back the specifications- make/ model/ cards/ Ram/ Processor etc. The more info the better able we are to troubleshoot.

---

### Post by Strider11o7 on 2009-04-08
Thanks I'll try to check the disk for errors next time I get the chance. I wish I could give more info on his hardware but I don't have it with me, and I'm quite sure alex doesn't know either (He's a music major, go figure =/). If it counts for anything, I noticed that he was using a pre-built dell desktop, not much more than a few years old i'm guessing.

I'll update with specs if it continues to not work.

---

### Post by mbadawi23 on 2009-04-09
> **Strider11o7 said:**
> it skips the initial Ubuntu-loading splash screen and goes straight to the default orange background with just a cursor that you can move around and nothing else.

I have the same problem and I have some experience installing ubuntu. Actually this is the first time I saw this problem on this computer. Here are my h/w specs:
- AMD Athlon 64 x2
- 2GB RAM
- GeForce 9600 GT display adapter
- MSI mainboard (I'm not sure of the model)

Note: I installed Hardy and Feisty before with no major problems like this. I only had to enable restricted drivers for the display adapter and some poking for the wifi adapter.

All help appreciated.

Thanks

---

### Post by cariboo on 2009-04-09
I would suggest you try starting in safe graphincs mode. Boot from the LiveCD and at the menu press F4 and select safe graphics mode. Press enter and continue booting.

I am running an MSI K9NGM2, and running the onboard graphics adapter I have to use safe graphics mode to start up. It didn't affect the installation as the adapter is detected right away and the proper restricted driver is recommended.

Jim

---

### Post by mbadawi23 on 2009-04-09
> **cariboo907 said:**
> I am running an MSI K9NGM2, and running the onboard graphics adapter I have to use safe graphics mode to start up. It didn't affect the installation as the adapter is detected right away and the proper restricted driver is recommended.

But the onboard adapter is disabled I'm using the GeForce one. Do you suggest that I use the onboard adapter? or should I try your approach with the GeForce adapter?

---

