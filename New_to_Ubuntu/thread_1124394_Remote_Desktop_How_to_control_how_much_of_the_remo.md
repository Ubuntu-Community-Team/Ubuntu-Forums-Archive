---
title: "Remote Desktop: How to control how much of the remote desktop's screen is needed?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by swarup on 2009-04-13
Remote Desktop connection is working fine. But the host computer has a new screen, and for some reason the image which is sent to the remote computer no longer fits on the remote desktop screen. Only part of it fits. 

What determines how much screen is needed for the image when it gets to the remote desktop? Is it the screen resolution? If the remote desktop user wants to keep the image on just half his screen and wants the entire host screen to appear (rather than showing only half), then what are the tools to control this?

---

### Post by freak42 on 2009-04-13
yes, indeed the screen resolution, vncviewer will always display the full remote image at the same resolution as your local viewer, meaning if the remote machine has a higher screen resolution it won't fit on the client's screen. 
There is another vnc viewer in the ubuntu repos called vinaigre (or vinagre??), it can zoom/shrink the reomte deskotp's image, which is great. I'd say give this a try.

hth

---

### Post by swarup on 2009-04-13
Wow--that sounds great. When you open vinagre, where is the control for zooming/shrinking the remote destop image?

I'm pretty sure vinagre *is* the Remote Desktop Viewer (RDW) which we are using. And I think this is the default viewer in Ubuntu. And least that is the one that has always been in my machines. When I do "vinagre" in the terminal window, then the RDW which we always use, opens.

I have used the vncviewer before, but it doesn't seem to be the default software for Ubuntu--at least not for 8.04 or 8.10.

---

### Post by freak42 on 2009-04-13
in vinagre to get a remote desktop to resize to the vinagre window use either:

1. when opening a new connection (connect button), check the Scaling checkbox.

2. or when you are connected go to view and check "scaling"

3. or if you already have your connection bookmarekd.. right-click the bookmark -> choose edit bookmark and then check scaling.

hth

---

### Post by swarup on 2009-04-13
Whether I try to select "scaling" before or after the application opens, vinagre gives the same error:

> Scaling does not work properly on composited windows. Disable the visual effects and try again.

So, I cannot enable scaling. Does this vinagre work *with scaling* for you?

I searched on this subject, and found that others have been having the same problem. Some have suggested that there may be a bug with the remote desktop scaling available in vinagre that ships with Ubuntu. See thread: [http://ubuntuforums.org/showthread.php?t=1075269](http://ubuntuforums.org/showthread.php?t=1075269)

Please let me know some suggestion or tip as to how to get scaling enabled in vinagre.

---

### Post by freak42 on 2009-04-14
> **swarup said:**
> Whether I try to select "scaling" before or after the application opens, vinagre gives the same error:



So, I cannot enable scaling. Does this vinagre work *with scaling* for you?

I searched on this subject, and found that others have been having the same problem. Some have suggested that there may be a bug with the remote desktop scaling available in vinagre that ships with Ubuntu. See thread: [http://ubuntuforums.org/showthread.php?t=1075269](http://ubuntuforums.org/showthread.php?t=1075269)

Please let me know some suggestion or tip as to how to get scaling enabled in vinagre.

uh-oh.. I don't have this problem, here it works fine, however I do not have compiz enabled nor visual effects.

you can try turning off compiz and visual effects (system->preferences-> appearance preferences -> visual effects -> check none.

I don't know if this helps, obviously you will loose the fancy windows visual effects.

The thread you mention suggests 'krdc' as a vnc client that can do scaling in such situations, I however cannot help you with it if you try it (and it might install a lot of kde libraries if yo do install it)

hth

---

### Post by swarup on 2009-04-14
> **freak42 said:**
> uh-oh.. I don't have this problem, here it works fine, however I do not have compiz enabled nor visual effects.

you can try turning off compiz and visual effects (system->preferences-> appearance preferences -> visual effects -> check none.

I don't know if this helps, obviously you will loose the fancy windows visual effects.

I don't have compiz or visual effects enabled, nor have I ever used these things. And I don't have the impression that those on the other thread I mentioned had them enabled either. For that reason I am so surprised that your "scaling" is working. I haven't found anywhere else yet in Ubuntu where it was reported to be working. But it is very hopeful that at least yours does work. That means that somehow, in others' machines also, it *should* be able to be made to work. The question is, how. Any further suggestions in this regard will be helpful I think not only for me, but for so many others as well for whom scaling has until now not worked.

---

### Post by freak42 on 2009-04-15
Ok, if you don't have visualeffects enabled.. then uhm.. I don't know how to help you .. there are some bug reports:
[https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/294879](https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/294879)

another thread proposed to enter
  vinagre reset 
in a console to reset settings or you can try starting vinagre from a console with:
 vinagre --gtk-vnc-debug
and maybe find a more descriptive error message.

Otherwise I am at my wits end, maybe try the kde alternative from above?

hth

---

