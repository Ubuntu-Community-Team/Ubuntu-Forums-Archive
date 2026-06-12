---
title: "title bar and bottom panel missing from firefox :-%"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-03
Hi there! I'm newby..I just installed ubuntu, everything was fine but dont know why, I suddendly miss my title bar and bottom panel from firefox so I cannot reduce to icon my page, neither navigate throw my desktops..
any hel please?

---

### Post by Het Irv on 2009-03-03
Try hitting F11 and see what happens.

---

### Post by webwiller on 2009-03-03
> **Het Irv said:**
> Try hitting F11 and see what happens.

GREAT! Fixed! I got both top/bottom panels back, the window was somehow not-aligned, but this way I could reach the minimize/maximize buttons & I got my original window back! txs!;)

---

### Post by redseventyseven on 2009-03-03
> **webwiller said:**
> GREAT! Fixed! I got both top/bottom panels back, the window was somehow not-aligned, but this way I could reach the minimize/maximize buttons & I got my original window back! txs!;)

Ummm... not quite. You were in Fullscreen mode. This is toggled either through the menu (View > Fullscreen) or by hitting F11.

Just so you know.

---

### Post by Het Irv on 2009-03-03
No problem, F11 toggles Full screen mode, and it usually scares the crap out of people that accidentally hit it and don't know what they did.  Its all so a pretty fun problem since IE has the same feature.  I have walked into plenty of offices, hit a button and fixed the problem, and had the user stare at me like I just used a magic spell, its great.

---

### Post by JoshuaRL on 2009-03-03
> **Het Irv said:**
> Its all so a pretty fun problem since IE has the same feature.

As does Opera, I just tried it.  :p

---

### Post by webwiller on 2009-03-03
but anyway...yes, f11 first goes full screen and when I press it twice it brings my bars back but...going around my desktops and back to firefox I find them away again!
Is it some feature I have to turn permanently off somewhere??

---

### Post by redseventyseven on 2009-03-03
Does it affect the title bars for your other applications?

If so, then it's probably a problem with "compiz" - the package which produces visual effects. Can you reproduce the problem with Advanced Visual Effects turned off (you can turn them off in your Appearance settings)?

---

### Post by suitedaces on 2009-03-03
The F11 "spell" got me serious brownie points from a few different worried teachers back at school!

---

### Post by cj1404 on 2009-03-11
FYI:

F11 is the shortcut key for FULL SCREEN in Firefox and some movie players.  Just so you know.:popcorn:

---

### Post by SentientFluid on 2009-03-11
> **webwiller said:**
> but anyway...yes, f11 first goes full screen and when I press it twice it brings my bars back but...going around my desktops and back to firefox I find them away again!
Is it some feature I have to turn permanently off somewhere??

Same thing happens to me on occassion.  Relaunching the Window Manager fixes it as well but only ever in Firefox. Not sure if Compiz isn't playing nicely with Firefox or vice versa.  It doesn't happen often enough for me to have been bothered enough to look into it, though.

Just to clarify what happens in my case:

I will have been switched from one workspace to a 2nd that has Firefox on it.  The Firefox viewport will be taking up the whole screen (ie Tab bar is at the top edge of my display and no status bar at the bottom).

It looks like it's in Fullscreen mode but I don't think it is because I'll hit F11 and the Firefox window will flicker a bit, but doesn't appear to change.  Pressing F11 a second time acts as if Fullscreen is being turned off (ie toolbars and status bar are back on screen) and the Firefox window was manually resized to take up the whole display.

Does that sound like what's happening with you Willer?

---

### Post by green69 on 2009-03-13
> **redseventyseven said:**
> Does it affect the title bars for your other applications?

If so, then it's probably a problem with "compiz" - the package which produces visual effects. Can you reproduce the problem with Advanced Visual Effects turned off (you can turn them off in your Appearance settings)?

Yes it happens the same to me but in everykind of windows (not only in firefox). I cant fix it with F11 and I don't know how to solve it.

Please, someone can help?

Thanks in advance!

---

### Post by VCoolio on 2009-03-13
I had these same problems, not sure how I repaired them though. Thing is: in my Appearance settings > Visual effects, now none of the three options is checked. So, first, set this to none or maybe the medium option. Then run Preferences > Compiz settings manager, reset to default settings and then make sure the window decorator plugin is on (in the effects section). Also, change the theme (the human theme screwed with my window borders). Get fancy themes from gnome-look.org: download the .tar.gz and drag and drop in Appearance preferences >theme. 

The firefox problem was a bug, should be gone when you install updates. Also, check here: [http://ubuntuforums.org/showthread.php?t=981306](http://ubuntuforums.org/showthread.php?t=981306) .

---

### Post by green69 on 2009-03-14
> **VCoolio said:**
> I had these same problems, not sure how I repaired them though. Thing is: in my Appearance settings > Visual effects, now none of the three options is checked. So, first, set this to none or maybe the medium option. Then run Preferences > Compiz settings manager, reset to default settings and then make sure the window decorator plugin is on (in the effects section). Also, change the theme (the human theme screwed with my window borders). Get fancy themes from gnome-look.org: download the .tar.gz and drag and drop in Appearance preferences >theme. 

The firefox problem was a bug, should be gone when you install updates. Also, check here: [http://ubuntuforums.org/showthread.php?t=981306](http://ubuntuforums.org/showthread.php?t=981306) .

I tried what you proposed but unfortunaly no solution is reached in my case. Thank you anyway for you help.

If anybody else has another solution to propose it will be welcomed!

Thanks

---

### Post by broecher on 2009-03-15
Hey I have suddenly had this problem as well for a couple days now. I have  been using Hardy with gnome and compiz for several months without this problem. I am not sure what brought it on.

Firefox (only) is opening in a strange state - it is not the same as full screen. It is not stable, it jitters and freezes for short periods. If I click on view, I can see that full screen is not selected during this problem.

Pressing F11 twice fixes it. I would rather not have to press extra keys when I open my browser so I went turned my visual effects off and the problem is gone altogether.

I will attach screen shots of what normal full screen looks like, and what this particular problem looks like.

---

### Post by chubble10 on 2009-03-15
> **suitedaces said:**
> The F11 "spell" got me serious brownie points from a few different worried teachers back at school!

That's not the worst thing I've had to help teachers with! One asked me how to delete data from some cells in Excel! I just leaned over and hit the 'delete' button on the keyboard and they stared at me as though I had just found life on another planet!

---

### Post by fooman on 2009-03-15
> **broecher said:**
> Hey I have suddenly had this problem as well for a couple days now. I have  been using Hardy with gnome and compiz for several months without this problem. I am not sure what brought it on.

Firefox (only) is opening in a strange state - it is not the same as full screen. It is not stable, it jitters and freezes for short periods. If I click on view, I can see that full screen is not selected during this problem.

Pressing F11 twice fixes it. I would rather not have to press extra keys when I open my browser so I went turned my visual effects off and the problem is gone altogether.

I will attach screen shots of what normal full screen looks like, and what this particular problem looks like.

should be easy to fix *with* visual effects enabled...

open firefox and press f11 twice to get to a normal size screen.

click on the unmaximize button.

close firefox....then open firefox.

click the maximize button.

problem should be fixed....for good.

---

### Post by Het Irv on 2009-03-17
> **chubble10 said:**
> That's not the worst thing I've had to help teachers with! One asked me how to delete data from some cells in Excel! I just leaned over and hit the 'delete' button on the keyboard and they stared at me as though I had just found life on another planet!

Please tell me you made that one up! Please!

---

### Post by union two levers on 2009-03-26
thanks for that as well, it was doing my head in...cheers

---

### Post by union two levers on 2009-03-26
hi, i too found that if i switched visual effects off firefox was returned to its more usable state

---

### Post by green69 on 2009-03-27
> **union two levers said:**
> hi, i too found that if i switched visual effects off firefox was returned to its more usable state

My window title bar disappear, but not only with firefox, in every types of windows. It's a such annoying thing, because every time a want to minimize a window I have to alt and drug that window, and to close I have to do it from the bottom pannel.

PLEASE can anybody help me?!?

---

### Post by JoshuaRL on 2009-03-29
> **green69 said:**
> My window title bar disappear, but not only with firefox, in every types of windows. It's a such annoying thing, because every time a want to minimize a window I have to alt and drug that window, and to close I have to do it from the bottom pannel.

PLEASE can anybody help me?!?

It might be a good idea to start your own thread.  Your problem, although annoying and seemingly connected, isn't related to this one.  If you'd like you can PM me the address of the new thread and I'll try to help you.

---

### Post by VastOne on 2009-04-08
> **VCoolio said:**
> I had these same problems, not sure how I repaired them though. Thing is: in my Appearance settings > Visual effects, now none of the three options is checked. So, first, set this to none or maybe the medium option. Then run Preferences > Compiz settings manager, reset to default settings and then make sure the window decorator plugin is on (in the effects section). Also, change the theme (the human theme screwed with my window borders). Get fancy themes from gnome-look.org: download the .tar.gz and drag and drop in Appearance preferences >theme. 
.

It seems as if every time there is a kernel update this very thing happens to many of us.  Under visual effects, none were selected for me and as soon as I selected the maximum (choice 3) (one I always use) my issues with no minimize maximize buttons went away...

Kernel upgrades are great but not infallible...

VastOne

---

### Post by Therion on 2009-04-08
A common solution for this is to install the Compizconfig-settings-manager package via Synaptic then going to the settings manager in System/Preferences.  

From there scroll down to the "Utilites" section and open the "Workarounds" plugin.  

Clear the check-box for **Legacy Fullscreen Support** and see if the issue is resolved.

---

