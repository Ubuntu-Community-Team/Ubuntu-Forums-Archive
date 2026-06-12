---
title: "Flash Video choppy?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by mlthmp on 2009-08-18
Is there anything I can do to improve the way Flash video loads on my system?

For example, I sometimes watch TV on Fox.com etc, and its been choppy since I moved to Ubuntu. Granted its better when viewed in Seamonkey as compared to Firefox.. but its still mighty choppy.

Also Im not able to load any megavideo shows on fullscreen. Same issue very choppy and slow. Any suggestions?

Thanks!

---

### Post by zephyrcat on 2009-08-18
Unfortunately, Ubuntu 9.04 has some very serious issues with Intel-based graphics hardware. This is surprising, since Intel hardware had historically had some of the best support for Linux.

If you don't know if you have Intel graphics, open Synaptic Package Manager (System > Administration > Synaptic Package Manager) and install "hardinfo". Then go to System > Preferences > System Profiler and Benchmark. Click on Display under Computer and scroll down to OpenGL. The Vendor should tell you if you are using Intel graphics.

If you are, you can try this tutorial: It is quite advanced, but it might help.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Sorry I don't have a better answer. I really wish I did.

---

### Post by mlthmp on 2009-08-19
> **zephyrcat said:**
> Unfortunately, Ubuntu 9.04 has some very serious issues with Intel-based graphics hardware. This is surprising, since Intel hardware had historically had some of the best support for Linux.

If you don't know if you have Intel graphics, open Synaptic Package Manager (System > Administration > Synaptic Package Manager) and install "hardinfo". Then go to System > Preferences > System Profiler and Benchmark. Click on Display under Computer and scroll down to OpenGL. The Vendor should tell you if you are using Intel graphics.

If you are, you can try this tutorial: It is quite advanced, but it might help.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Sorry I don't have a better answer. I really wish I did.

Thank you for the response!

When I install, and scroll down it has

OpenGL 
Vendor "Tungsten Graphics, Inc" 
Renderer Mesa DRI Intel(R) 915G 20090326 RC2 x86/MMX/SSE2
Version 104 MESA 7.4
Direct Rendering YES

So, am I screwed? lol

---

### Post by zephyrcat on 2009-08-19
Ooops. I guess Renderer would be the better place to check, but I guess you figured that out. Yes, you do seem to have Intel graphics. That doesn't necessarily mean you're screwed, though. :-)

I haven't dealt with the Intel graphics issues personally, since I have an Nvidia chip.

Look at the guide I mentioned before and decide if you want to give it a shot. It is rather complicated, but you should be able to get through it without too much trouble.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

If that doesn't work or you decide to skip it, you could install a previous version of Ubuntu. You can get Ubuntu 8.10, for example:

[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

Hope that helps.

---

### Post by mlthmp on 2009-08-19
Thanks for all the help =)

After giving it some thought.. I've decided to "downgrade" to 8.10 instead of messing with stuff im not ready to do yet (im a linux newb, lol)

I figure my PC may likely handle a slightly older release better anyhow lol. Thanks!

---

### Post by zephyrcat on 2009-08-19
I hope that works out for you.

If you have any more issues, please post again.

---

### Post by nunovi on 2009-11-21
Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

---

### Post by NoaHall on 2009-11-21
> **nunovi said:**
> Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

Could you please stop posting in old threads? You are causing people with problems to lose support. If you want to post your words, do so in the cafe - [http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

---

### Post by ibuclaw on 2009-11-21
Old Thread - Closing.

If you are having this issue, raise a new support question.

Regards
Iain

---

