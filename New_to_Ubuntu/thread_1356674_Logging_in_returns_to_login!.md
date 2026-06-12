---
title: "Logging in returns to login!"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by pipedreambomb on 2009-12-16
Hi,

I installed Xubuntu with Wubi last night, was working fine for a few hours. Think the last thing I did on it was install WINE, but didn't get a chance to try it out. Actually I think Firefox then started shutting as soon as it opened. I went to bed at that point :)

I'm trying to log in again today, and it accepts my password (rejects wrong ones just fine) but then after doing the 'swirly dots' xubuntu screen for about 3 seconds just loads the login page again.

Any ideas? I'd be very grateful.


Thanks, George

---

### Post by pipedreambomb on 2009-12-16
Bump! Please could I get some help, I'm stuck using XP and it's extremely slow on this old computer. Xubuntu was much faster when it was working - it's my mum's computer and I was going get her using it permanently.

---

### Post by Paul T. on 2009-12-16
If you've only just installed Xubuntu I assume you've nothing important that needs saving, so why not just uninstall it and then re-install it again?

---

### Post by philinux on 2009-12-16
> **pipedreambomb said:**
> Bump! Please could I get some help, I'm stuck using XP and it's extremely slow on this old computer. Xubuntu was much faster when it was working - it's my mum's computer and I was going get her using it permanently.

At the login screen look for the session or options tab and choose failsafe or xterm.

---

### Post by pipedreambomb on 2009-12-16
Phil, choosing xterm gives exactly the same result.

Paul, I take your point but I spent a few hours installing stuff, getting Firefox just how I like it, finding a desktop etc. Perhaps it's common to wipe over your settings frequently with Linux, but I was hoping not to have to do that over again. Besides, won't this problem just crop up again?

Thanks for the replies. I think I've found a thread detailing a similar issue to mine now, so I'm trying to work through it. Looks complicated though I must admit! 

[http://ubuntuforums.org/showthread.php?t=1317265&page=2](http://ubuntuforums.org/showthread.php?t=1317265&page=2)

---

### Post by joes7 on 2009-12-16
Log in as "root". There shouldn't be password or what so ever if you didn't specify it during installation process.

---

### Post by llawwehttam on 2009-12-16
Hmm sounds like a bit of a wierd glitch. Try ctrl-alt-backspace maybe to kill 'x'.  Otherwise press ctrl-alt-F1 to get to a command line before you log in, login as yourself and see if it works. If so ```
su -
```  to root and try ```
killall X

```
To re-load the X server (the linux GUI). Did you install graphics drivers? They can cause a problem if you got the wrong ones.
I've been using Linux for years now and have never seen a problem like this.

---

### Post by pipedreambomb on 2009-12-16
I suspect it's a graphic card issue as after I posted the link to the thread with the same problem as me, I noticed someone had exactly the same old card as me (nVidia GeForce2 MX/MX400). Sounds like if I just do a system update enabling pre-release updates, it'll probably fix it. However now I've logged temporarily by using 'startx' from the recovery console (I'm just trying stuff I read about, not always knowing what it does :) ) and am posting this in a different looking version of Linux.

So a little problem to overcome in order to do the update - how can I clear some space? It's an old computer and I only had 3 gig to spare for the pseudo-partition with Wubi. I'd rather not uninstall some of the media players etc I downloaded if there are other options.

Really grateful for the replies btw, thanks.

---

### Post by philinux on 2009-12-17
> **pipedreambomb said:**
> I suspect it's a graphic card issue as after I posted the link to the thread with the same problem as me, I noticed someone had exactly the same old card as me (nVidia GeForce2 MX/MX400). Sounds like if I just do a system update enabling pre-release updates, it'll probably fix it. However now I've logged temporarily by using 'startx' from the recovery console (I'm just trying stuff I read about, not always knowing what it does :) ) and am posting this in a different looking version of Linux.

So a little problem to overcome in order to do the update - how can I clear some space? It's an old computer and I only had 3 gig to spare for the pseudo-partition with Wubi. I'd rather not uninstall some of the media players etc I downloaded if there are other options.

Really grateful for the replies btw, thanks.

Open synaptic and click Status then installed. Scroll through the list and mark for complete removal anything you dont need. e.g games, bluetooth etc. Just read the package details and dont remove anything the system needs.

---

### Post by pipedreambomb on 2009-12-17
No idea why, but it started working again just fine the next time I rebooted. All I really did was:

1) Start in the recovery mode
2) Use the command 'startx'

Startx seemed to load a different window manager than usual, or it certainly looked different, and my Firefox customizations were gone. Then by the next time I restarted it, log in was working again and Firefox had my settings too!

My best guess is that once I actually managed to get it to boot with startx, it was then in a position to fix itself automatically. Either that or I did something else to it, but I certainly don't remember doing anything of much significance! Hope that helps someone somewhere.

---

