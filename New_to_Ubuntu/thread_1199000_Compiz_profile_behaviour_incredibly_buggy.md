---
title: "Compiz profile behaviour incredibly buggy"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-28
I first used compiz on 8.10 with a Nvidia Go 7400 with the 173 and then 177 driver. It was buggy at first but then stabilised when I stopped trying to play with it or load profiles of any sort.

Now on 9.04, with the version 180 driver, I tried loading a saved profile and it simply will not reflect the settings. Sometimes it will forcefully change the settings of the loaded profile. Often it will mess up the desktop rendering. Sometimes, like 1 out of 6 times, it will load correctly and everything will be fine, but after 2-3 restarts, it will again mysteriously mess up and the cycle will repeat when I try to load the profile again.

Nothing is wrong with the profile btw, I've used the exact same file in more than a dozen computers and about half of them go crazy with it, 1 or 2 just don't work, the rest work fine.

Is compiz still experimental?

Thanks

---

### Post by Andy06 on 2009-07-01
Ok now its settled down a bit without me changing anything. It still is buggy but "predictably" so. Now when I shut down the computer, just before it leaves the GNOME desktop, the "compiz could not be enabled" (paraphrasing) warning flashes in a dialog box before shut down proceeds. Then when I log back in or restart, compiz is disabled. No amount of tinkering in the "Visual effects" tab of "Appearance" enables it. What I have to do it open Compiz fusion icon (which apparently tells me that compiz is indeed still the WM despite effects being off) and then select the "Reload Window Manager" option, this will then mess up the screen with artefacts, tearing, the works...then I have to reload it once more and everything comes to life and compiz works as expected without any bugs TILL the next shut down/restart.

So basically the WM needs to be reloaded twice. If I did not have Compiz Fusion Icon installed, I wouldn't even know this is the case. Anyone else have the same problem? Could this be due to the Nvidia 180 driver because I did not have this problem with the 173 or 177 (I had different problems :)).

Thanks a lot

---

### Post by drs305 on 2009-07-01
> **Andy06 said:**
> Then when I log back in or restart, compiz is disabled. No amount of tinkering in the "Visual effects" tab of "Appearance" enables it.

Andy06,

Is Metacity's compositing enabled? Barring hardware issues, compiz may not start if the 'compositing' option of metacity is enabled. On my machine, if I try to select "Normal" or "Extra" with metacity enabled Compiz won't start. Note: Metacity compositing only became available in Ubuntu with jaunty, which may explain why compiz presented you with fewer problems in hardy.

You can tell if compositing is enabled (when running metacity) by looking for 'shadowing' around window borders. If you see shadowing, metacity's compositing feature is on. Run the following command and see if it is enabled. If it is, turn it off and compiz should start when you select something other than 'None' on the Appearance page.
```

gconf-editor /apps/metacity/general/compositing_manager

```

Once in compiz, you might try experimenting with the Effects > Window Decoration settings. By default, compositing is set to "/usr/bin/compiz-decorator". The other option, which you can set either with the fusion-icon or manually entering it here, is:
gtk-window-decorator --replace

---

### Post by Andy06 on 2009-07-01
Hi drs305,

You were right, metacity compositing was indeed enabled. Unfortunately disabling it did not set things right. I disabled it and then logged out and just before logging out, it showed the compiz error again, then after logging in, it notified that it could not start AWN dock because no compositing was in place (earlier metacity compositing meant that this error would not show), I had to manually start compiz. 

Subsequent restarts confirmed the problem had not gone away. However like you said, now enabling effects from the Appearance tab works (so I don't have to use Compiz fusion icon anymore).

> Note: Metacity compositing only became available in Ubuntu with jaunty, which may explain why compiz presented you with fewer problems in hardy.

In hardy, I don't quite remember but I and a couple of friends enabled metacity compositing using Ubuntu Tweak instead of gconf editor and I remember having it enabled in Intrepid as well, are you sure there was no metacity compositing in Intrepid (if there wasn't and enabling it in Tweak did not actually do anything, then that would explain the fewer problems).

> Once in compiz, you might try experimenting with the Effects > Window Decoration settings. By default, compositing is set to "/usr/bin/compiz-decorator". The other option, which you can set either with the fusion-icon or manually entering it here, is:
gtk-window-decorator --replace 

The funny thing is, my profile had it on "gtk-window-decorator --replace", so I reset it to default "/usr/bin/compiz-decorator" but compiz fusion icon still showed it as being "gtk-window-decorator --replace". Couple of restarts later, CCSM auto reverted to the non default "gtk-window-decorator --replace". 

Is it just me or does compiz often do "out of control" :D. Also I have always experienced delayed effect of changes with it. If I configure something, it seems it only comes into effect (and stays that way) after a couple of reloads and restarts. Seen this on multiple computers, variety of hardware graphics cards etc. It always settles down after a while though until you change something again. :-k

---

### Post by Andy06 on 2009-07-05
Now Cairo refuses to work with compiz compositing, it works with metacity though. Hmm....

---

