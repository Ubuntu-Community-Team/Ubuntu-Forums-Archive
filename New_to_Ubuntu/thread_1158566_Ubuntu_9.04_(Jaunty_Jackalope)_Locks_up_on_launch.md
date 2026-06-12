---
title: "Ubuntu 9.04 (Jaunty Jackalope) Locks up on launch"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by DPMR on 2009-05-13
Hi All
I broke my Ubuntu 9.04 (Jaunty Jackalope). :(
Now when I launch from grub I get a screen of black bars and gray bars, it blinks a few times like it is trying to run but just locks up.

Before this I (after much taunting by package manager)allowed package manager to update system. I was looking at other apps for graphics and notice ATI CCC was available so I installed it. All seamed fine. I worked on some spreadsheets in OOo and played around with the cool graphics.

I also rebooted a few times to see if everything would load fine and had no problems. I believe that I installed the ATI app just before the trouble began, it was getting late and I was having so much fun I don't really remember.
Man I can believe how cool Ubuntu 9.04 (Jaunty Jackalope) is.

I am using an AMD2 mombo with a ATI Radeon X1650 graphics card.

---

### Post by coffeeaddict22 on 2009-05-13
Try booting into a recovery console (its' the option below the one you usually chose in the GRUB boot menu) and choosing "Fix my graphics problem" or whatever it's called.
If that doesn't work, can you get to a terminal? (try the "drop to a root terminal with networking" option) If so, what's the output of ```
lshw -C display
```

---

### Post by atisucks on 2009-05-13
i have exactly same problem after installing ati ccc from their site , now my pc won't load up any more , help me uninstall this ati ccc messed up driver please . i want no part of it , i have enough trouble as is when using window xp , their drivers are of very poor quality as usual .

---

### Post by DPMR on 2009-05-13
@coffeeaddict22

Thanks for your reply. I did try the recovery boot with no luck.

I was to impatient to wait for a reply, so I simply reinstalled.

So far the reinstall is working fine.

I see from atisucks reply that there must be an issue with ATI's CCC package.

I will keep this post in mind and try your suggestion if it happens again.
And thanks for your effort.

@atisucks
I don't know if you are aware of ATI's effort opening up drivers for Linux distros. 
They are one of the few video card makers that are willing to help. 
I don't want to start a flame in this post but I think you should walk before you leap.[-X

---

### Post by coffeeaddict22 on 2009-05-14
DPMR,
I didn't get lockup but was getting long delays on my ATI card; the open sourced driver is much better functionally (although I'm not playing games, so don't use that 3D stuff much).

---

### Post by atisucks on 2009-05-14
> **DPMR said:**
> @coffeeaddict22

Thanks for your reply. I did try the recovery boot with no luck.

I was to impatient to wait for a reply, so I simply reinstalled.

So far the reinstall is working fine.

I see from atisucks reply that there must be an issue with ATI's CCC package.

I will keep this post in mind and try your suggestion if it happens again.
And thanks for your effort.

@atisucks
I don't know if you are aware of ATI's effort opening up drivers for Linux distros. 
They are one of the few video card makers that are willing to help. 
I don't want to start a flame in this post but I think you should walk before you leap.[-X
yea ok  , point taken and lesson learned .
Yea well  . , after updating ubuntu 8.10 to  ubuntu Jaunty Jackalope   all went well and no glitches after restarting and confirming that all was running smoothly . Now no boot or should i say i got the boots  cause  i understand nothing about what to do when boot stall at this screen ( _ )   all it does is flash , on and off . I should re download again and stay with the propriety driver , but not today , i'm over my download limit this month and takes bout 2 hours easy to download , some other time maybe .

---

### Post by atisucks on 2009-05-14
Initramfs means that ubuntu was not happy having that ati ccc downloaded from ubuntu 9.04 how do i backtrack on this how to how to is the question

---

### Post by DPMR on 2009-05-14
@atisucks
 I would suggest that you follow coffeeaddict22 advice about the sudo command and report it back here,
 or start a new thread with that report, the report will appear with that command.

But with all due respect for your anger with ATI, 
I would get a new screen name, 
don't think your going to get anybodys attention if they think they have to put up with bad attitude right from the get-go.
I am not trying lecture just help.

I know Linux people can be a little fussy if they don't think your going to be forthright. 
For myself I don't really care to reply to atisucks.

Since I have corrected my problem by reinstalling I am going to consider this thread closed.

---

### Post by atisucks on 2009-05-14
yea ok DPMR no problem 
i will try other alternatives ,
Tks for the input .

---

