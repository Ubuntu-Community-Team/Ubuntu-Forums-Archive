---
title: "Hello &amp; request help with menu/toolbars"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by location8 on 2009-06-17
Hello Ubuntu users
 

 Absolute beginner here and learning the hard way which to me is the best way to learn.
 

 Obviously here to ask about a problem that I have and have already googled my problem and searched here in the forum.  Lots of conflicting finds so I figured I'd better join here and ask before I start making things more difficult for myself.  ;o)  I will attempt to describe
 

 **_Problem_**: Lost all menubars/toolbars &#8211; top and bottom
 I cannot access any panels/icons etc.
 

 Once booted up, I only have the wallpaper on show, Unbuntu logo top  left of screen, battery level &#8211; wireless connection &#8211; date &#8211; time on the right.  I have right clicked anything between these two and nothing.  I have right clicked the logo and there is nothing there to access the addition of another toolbar.  Have done the same for the icons on the right too (batt-w/c-date & time).  Have also right clicked other areas but no joy.
 

 Every now and then, I get the update manager. I attempted to update but the request was bounced back stating not enough disk space (very puzzling indeed as theres 70gig free)  
 

 I can access the wireless but I always have to input my password to connect.  Cannot get on internet because theres no browser to connect to.
 

 **_History_**
 I purchased an NC10 via ebay some 5wks ago with partitioning for Ubuntu 9.04 and Windows XP.  Ubuntu has been working fine until tonight.
 

 First, I lost my tabs, then could not place new ones on.  Then Admittedly removed the bottom toolbar. Still had no joy, so I rebooted.  No difference. Currently running firefox as a browser.
 

 Phew! Sorry about long type up but figured all information is important.
 

 Hope you guys can help and please go easy on me
 

 I'll start reading the free beginners guide in my lunchbreak tomorrow
 

 :)
 

 regards
 manf

---

### Post by CatKiller on 2009-06-17
At each end of the panel there is a handle that will let you access the properties of the panel itself rather than the applets included on it. There is an option on the right-click menu for New Panel.

If you **have** run out of disk space, that would cause weirdness in applications. ```
df -h
``` should show you what you've used on each of your filesystems.

---

### Post by location8 on 2009-06-18
> **CatKiller said:**
> At each end of the panel there is a handle that will let you access the properties of the panel itself rather than the applets included on it. There is an option on the right-click menu for New Panel.

thanks catkiller
I can't see or access the panel itself.  Have tried right click menu  but nothing happens when I do this :sad:

> **CatKiller said:**
> If you **have** run out of disk space, that would cause weirdness in applications. ```
df -h
``` should show you what you've used on each of your filesystems.

How does one get into the codes?  Through DOS??

Anyone else have any ideas?

:confused:
thanks again

---

### Post by ZackM on 2009-06-18
> **location8 said:**
> thanks catkiller
I can't see or access the panel itself.  Have tried right click menu  but nothing happens when I do this :sad:



How does one get into the codes?  Through DOS??

Anyone else have any ideas?

:confused:
thanks again

It's not DOS... Careful saying that around here... Some people may burn you alive. Haha. Linux is based on Unix. The commands you need to run is in the terminal (Which is like using command prompt in Windows). 

So hit Alt-F2 and choose terminal (or gnome-terminal).

Then type this:

```
sudo debconf gnome-panel
```

Restart and your panels should return and be to their default settings.

If that doesn't work, you can also try this:

Open the terminal like I told you above, then type:

```
[B]gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```[/B]

---

### Post by elysianfields44 on 2009-06-18
> **location8 said:**
> thanks catkiller
I can't see or access the panel itself.  Have tried right click menu  but nothing happens when I do this :sad:



How does one get into the codes?  Through DOS??

Anyone else have any ideas?

:confused:
thanks again

EDIT: Zack beat me to the reply :P

You enter the code into Terminal - the Ubuntu command-line tool. To open a terminal, press Alt + F2, and you will get a "Run application" window. Type "gnome-terminal" (without the quotes) and click Run. This should get you a Terminal window, where you can type the code that was suggested. Hope that helps.

---

