---
title: "Anyone solved slow scroll problem?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by TBABill on 2009-12-28
I have reloaded java and flash, selected smooth scrolling, etc., all to no avail with both Firefox and Chrome browsers. The jerky scrolling seems to be a big issue across several Linux variants. Has anyone found a complete solution that enables smooth, or at least steady, scrolling on pages with heavy graphics, java or flash (not sure which is the major cause) applications?
 
As a side note, Mandriva 2010 KDE does not have this problem and I scroll very smoothly, but I really like my Ubuntu 9.10 install and want to keep it, at least to dual boot. It's definitely not a hardware issue because Windows (gone now, but had it till last week) and Mandriva work fine. I have downloaded all updates, made sure my nVidia driver is up to date and freshly installed, and even downloaded some extensions to help smooth it out (they didn't).
 
It acts like back in the day when if you didn't have enough RAM (remember going from 512K to 1MB?? haha) the machine had to constantly access the hard drive, causing sluggish performance.

---

### Post by Bachstelze on 2009-12-28
Are you sure your nvidia drivers are working correctly?

```
glxinfo | head
```

---

### Post by Ben Wright on 2009-12-28
This issue comes up on almost all systems when you are running heavy java and flash pages, but certain configurations can help. Here is an old bug about the issue: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/74116](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/74116) another idea might be to change to the swiftfox browser it may provide some significant improvements in performance. Thanks

---

### Post by warfacegod on 2009-12-28
I find that having smooth scrolling enabled makes firefox more jittery.

---

### Post by warfacegod on 2009-12-28
Here's a thread that I have found to be very useful.
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by ibuclaw on 2009-12-28
Since both distributions use the same versions of NViDIA and Firefox, it is may be likely that the differing versions of Xorg-Xserver may be the reason (Ubuntu uses 1.6.4, Mandriva uses 1.6.5).

Although, what would be more interesting is what sites are you going on? I've never really had any slow issues in Firefox. (Then again, that could be because of NoScript blocking everything I don't ask for ;)).

Regards
Iain

---

### Post by TBABill on 2009-12-28
Pretty much any site that has a great deal of flash on the page, such as a site like YouTube where you can do a search and have the results come back on a grid that gives you the option of 20-40 videos to choose from. That really just causes scrolling to jitter badly. Normal sites, such as news, automobiles, etc., do not have this problem on my machine, just the ones heavy with java or flash.
 
Is there an app that plays flash videos instead of Adobe's? I could switch the default player and see if that helped.

---

### Post by ffi on 2009-12-29
> **TBABill said:**
> I have reloaded java and flash, selected smooth scrolling, etc., all to no avail with both Firefox and Chrome browsers. The jerky scrolling seems to be a big issue across several Linux variants. Has anyone found a complete solution that enables smooth, or at least steady, scrolling on pages with heavy graphics, java or flash (not sure which is the major cause) applications?
 
As a side note, Mandriva 2010 KDE does not have this problem and I scroll very smoothly, but I really like my Ubuntu 9.10 install and want to keep it, at least to dual boot. It's definitely not a hardware issue because Windows (gone now, but had it till last week) and Mandriva work fine. I have downloaded all updates, made sure my nVidia driver is up to date and freshly installed, and even downloaded some extensions to help smooth it out (they didn't).
 
It acts like back in the day when if you didn't have enough RAM (remember going from 512K to 1MB?? haha) the machine had to constantly access the hard drive, causing sluggish performance.
I am not noticing it now but was noticing this last year on several ubuntu installs, very sluggish scrolling compared to mandriva, tried all sorts of settings, my guess is that it is a patch ubuntu is using or not using or some compiler option. For fglrx there is a famous patch which can boost performance considerably, see

[http://blog.jasondonenfeld.com/190](http://blog.jasondonenfeld.com/190)


but it might be something different. Ubuntu has always been on the sluggish side for me compared to mandriva

---

