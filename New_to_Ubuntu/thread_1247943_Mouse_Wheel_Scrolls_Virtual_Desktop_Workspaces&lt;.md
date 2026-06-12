---
title: "Mouse Wheel Scrolls Virtual Desktop Workspaces&lt;?&gt;"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by athowell on 2009-08-23
Hello,

I searched the forums but I am not sure if I have the right wording to yield criteria results.

When I scroll the mouse wheel it changes virtual desktop workplaces. The small law office I admin is complaining to me about this feature and wish for me to disable it.

Does anyone know how to disable this? I tried 'keyboard short cuts' and 'display' to no luck.

Please/help/thanks/advance

ps so far they all love ubuntu over xp and I saved them like 5k at least!

---

### Post by FreewheelinFrank on 2009-08-23
Seems to be a bug in Compiz (visual effects).

I've noticed it using Evince (PDF viewer) and other programs.

Here's one bug report. Might be worth a read for work-arounds.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/277195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/277195)

Try disabling visual effects (System>Preference>Appearance>Visual Effects).

---

### Post by athowell on 2009-08-23
> **FreewheelinFrank said:**
> Seems to be a bug in Compiz (visual effects).

I've noticed it using Evince (PDF viewer) and other programs.

Here's one bug report. Might be worth a read for work-arounds.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/277195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/277195)

Try disabling visual effects (System>Preference>Appearance>Visual Effects).

You fixed it. I love you man. I freaking love you so much it's almost gay!.


Joking aside...
Thank you very much for your help though. If I can ever do anything to repay the favour please let me know.

Thanks again.

---

### Post by zkriesse on 2009-08-23
In the taskbar you should little boxes at the bottom right hand corner. The amount of boxes equals the amount of virtual desktops. Right or opposite click on those and choose preferences. Make sure the amount of rows and boxes both equal one. That will make it so there is one desktop, the one you see.

---

### Post by CatKiller on 2009-08-23
For reference, you don't need to disable Compiz entirely, just change the Viewport Switcher behaviour. Install compizconfig-settings-manager and change (or disable) the mouse-based shortcuts for Desktop-based Viewport Switching in the Viewport Switcher plugin.

---

### Post by athowell on 2009-08-23
> **Zachk18 said:**
> In the taskbar you should little boxes at the bottom right hand corner. The amount of boxes equals the amount of virtual desktops. Right or opposite click on those and choose preferences. Make sure the amount of rows and boxes both equal one. That will make it so there is one desktop, the one you see.

My users don't want to lose their 6 desktops sir. I just wanted it not to start freaking out (read as scrolling desktops really fast & crazy) if they accidentally scrolled the mouse wheel while over desktop area or over a window that is not scrollable. 

The first guy fixed the issue but we did lose some 'eye candy' when it comes to some visual features but at least my users are happy -- for now at least.

Thanks again,
Avery Howell

---

### Post by athowell on 2009-08-23
> **Zachk18 said:**
> In the taskbar you should little boxes at the bottom right hand corner. The amount of boxes equals the amount of virtual desktops. Right or opposite click on those and choose preferences. Make sure the amount of rows and boxes both equal one. That will make it so there is one desktop, the one you see.

Ok. I just seen your post after I was off typing mine. I am going to try to just do that then. I'll let you know how it works out for me. Thank you very much.

-Avery

---

### Post by FreewheelinFrank on 2009-08-23
> **CatKiller said:**
> For reference, you don't need to disable Compiz entirely, just change the Viewport Switcher behaviour. Install compizconfig-settings-manager and change (or disable) the mouse-based shortcuts for Desktop-based Viewport Switching in the Viewport Switcher plugin.

Thanks.

I was going to suggest that after seeing it suggested as a work-around in one of the bug reports- I'll try it myself too.

---

