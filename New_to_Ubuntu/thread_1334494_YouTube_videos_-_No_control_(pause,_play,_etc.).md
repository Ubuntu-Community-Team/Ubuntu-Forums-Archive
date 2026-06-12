---
title: "YouTube videos - No control (pause, play, etc.)"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-11-22
Before anyone says "install restricted-extras" I already did it :)

I can watch YouTube videos fine, however, I can't actually play/pause, use the volume, or skip forward using the progress bar at all. I click on a button and it goes to the hand to "grab" it for a split second, than goes back to the mouse picture. Any one have any idea on what to do? I have tried re-installing the Flash plug-in and it didn't work.

---

### Post by RaZoR-x11 on 2009-11-22
Hey there Sound's like to me that you haven't downloaded flash player or its not working, If not google flash for ubuntu. Hope this helps.

---

### Post by UnknownFear on 2009-11-22
> **RaZoR-x11 said:**
> Hey there Sound's like to me that you haven't downloaded flash player or its not working, If not google flash for ubuntu. Hope this helps.

I re-installed it and still nothing.

---

### Post by RaZoR-x11 on 2009-11-22
I did a google search and found this. [http://ubuntulinuxhelp.com/adobe-flash-on-firefox-3-beta/](http://ubuntulinuxhelp.com/adobe-flash-on-firefox-3-beta/)
Hope this helps.

---

### Post by spongypants23 on 2009-11-22
Are you using 64-bit or 32-bit Ubuntu?

---

### Post by UnknownFear on 2009-11-22
> **spongypants23 said:**
> Are you using 64-bit or 32-bit Ubuntu?

64-bit.

> **RaZoR-x11 said:**
> I did a google search and found this. [http://ubuntulinuxhelp.com/adobe-flash-on-firefox-3-beta/](http://ubuntulinuxhelp.com/adobe-flash-on-firefox-3-beta/)
Hope this helps.

Did not work at all. This sucks :(

---

### Post by spongypants23 on 2009-11-22
> **UnknownFear said:**
> 64-bit.


Known bug! Install the 64-bit version of Adobe Flash Player.

Simple guide here: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by UnknownFear on 2009-11-22
> **spongypants23 said:**
> Known bug! Install the 64-bit version of Adobe Flash Player.

Simple guide here: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Worked beautifully, thank you :)

Another thing I definitely will be installing after a fresh install of Ubuntu 9.10, along side restricted drivers :D

---

### Post by Breetai on 2009-11-22
> **UnknownFear said:**
> Worked beautifully, thank you :)

Another thing I definitely will be installing after a fresh install of Ubuntu 9.10, along side restricted drivers :D

I thought it worked at first too, you'll still notice a lot of bugs in 64bit flash as time goes on.  I just swapped back down to 32bit it's a world of difference considering how often I use flash in the browser.

---

### Post by UnknownFear on 2009-11-22
> **Breetai said:**
> I thought it worked at first too, you'll still notice a lot of bugs in 64bit flash as time goes on.  I just swapped back down to 32bit it's a world of difference considering how often I use flash in the browser.

I see what you mean. I cleared FireFox's history and cookies and everything, and now it's acting up again. I'll just follow the link again and hope it works. Frustrating, but whatever.

---

### Post by asuastrophysics on 2009-11-22
> **UnknownFear said:**
> Before anyone says "install restricted-extras" I already did it :)

I can watch YouTube videos fine, however, I can't actually play/pause, use the volume, or skip forward using the progress bar at all. I click on a button and it goes to the hand to "grab" it for a split second, than goes back to the mouse picture. Any one have any idea on what to do? I have tried re-installing the Flash plug-in and it didn't work.

If you happen to be running Ubuntu Karmic 9.10 with 64-bit Adobe Flash already installed, then: 

**This is a bug. You can get around the problem you are describing by middle-clicking and left-clicking at the same time.** (Try it, it works!)
You can also get around this problem by completely disabling compiz with:
```
metacity --replace
```
and clicking should return to normal.

Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444757](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444757)

The bug report seems to be going nowhere though, :sad: despite the fact that this is a huge problem. As of yet, it seems they can't decide how important this is and can't find someone to assign this to. This bug has been open for the last month with no real patches as of yet.

---

