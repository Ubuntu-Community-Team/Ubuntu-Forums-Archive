---
title: "Restore Unity Defaults from GDE?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by mlnease on 2011-08-07
Hello,

I've been trying to familiarize myself with the Unity desktop in Natty.  Some setting I've changed either in CCSM or gconf-editor has resulted in Dash failing to respond to the super key and the dock failing to appear when I move the cursor to the left side of the screen.

GDE still works as usual, is there any way I can restore the Unity defaults from a GDE session and start over from scratch?

Thanks in advance.

mike

---

### Post by x-D on 2011-08-07
> **mlnease said:**
> Hello,

I've been trying to familiarize myself with the Unity desktop in Natty.  Some setting I've changed either in CCSM or gconf-editor has resulted in Dash failing to respond to the super key and the dock failing to appear when I move the cursor to the left side of the screen.

GDE still works as usual, is there any way I can restore the Unity defaults from a GDE session and start over from scratch?

Thanks in advance.

mike

Go into Gnome2/ Classic Mode, and then copy a shortcut to Compiz Settings Manager to the Desktop. Then go back into Unity. Go to the Profiles Tab (ALL IN COMPIZ SETTINGS MANAGER). Do reset to defaults (making sure the profile is set to Unity).

Then go back and search for Unity Plugin. Disable this. Then re-enable it. Tell me what happens now. It may be due to other plugins, but this should fix it. If it tells you it must disable other plugins, let it disable the other plugins, keep telling it you want Unity, it can disable the other plugins.

Hope this is of help to you....

x-D :guitar:

---

### Post by mlnease on 2011-08-07
Thanks for the quick response, x-D.  I'm not yet familiar with the Unity desktop but I don't think there were any tabs last time I tried opening a session.  However, I've copied the CCSM shortcut to the desktop; will restart in Unity and get back to you with the results.

---

### Post by x-D on 2011-08-07
> **mlnease said:**
> Thanks for the quick response, x-D.  I'm not yet familiar with the Unity desktop but I don't think there were any tabs last time I tried opening a session.  However, I've copied the CCSM shortcut to the desktop; will restart in Unity and get back to you with the results.

I mean the profiles tab in CCSM.

---

### Post by mlnease on 2011-08-07
OK:  I went back to Unity; the desktop appeared with the CCSM shortcut; but the shortcut (and Unity in general) was* completely* unresponsive to any input.

Thanks again for your time and attention--any other ideas?

---

### Post by x-D on 2011-08-07
> **mlnease said:**
> OK:  I went back to Unity; the desktop appeared with the CCSM shortcut; but the shortcut (and Unity in general) was* completely* unresponsive to any input.

Thanks again for your time and attention--any other ideas?

Right, go into Gnome 2 / Classic Mode. 

Open up CCSM. Go to the Profiles tab of CCSM Click Unity. Press reset to defaults (it may take a while to respond). 

Then try it again. Post back if it doesn't work. If it still persists to not work, I will give you help to reinstall Unity.

---

### Post by mlnease on 2011-08-07
Well, actually the CCSM shortcut* was *responsive when I tried it again.  And when I clicked on Unity in Profiles, the dock reappeared (and the top panel, or whatever it's called now) and all seemed normal--for a moment--then the dock and panel vanished again and Unity became unresponsive to input again.

I'd much appreciate your help in reinstalling Unity.  Thanks again for your patience.

---

### Post by x-D on 2011-08-07
> **mlnease said:**
> Well, actually the CCSM shortcut* was *responsive when I tried it again.  And when I clicked on Unity in Profiles, the dock reappeared (and the top panel, or whatever it's called now) and all seemed normal--for a moment--then the dock and panel vanished again and Unity became unresponsive to input again.

I'd much appreciate your help in reinstalling Unity.  Thanks again for your patience.

It's fine, I'll just be a moment remembering the commands, and thinking of any complications.

:guitar:

---

### Post by x-D on 2011-08-07
```

sudo apt-get install --reinstall unity

```

Just test-drove this on my machine, and it worked perfectly, tell me if there's any problems when you did it. :)

x-D :guitar:

---

### Post by mlnease on 2011-08-07
Nope.  I should've thought of that but didn't.  Anyway, after three Unity reinstalls and four restarts, still zero response in Unity.

Thanks again for all your efforts, though.

---

### Post by x-D on 2011-08-07
> **mlnease said:**
> Nope.  I should've thought of that but didn't.  Anyway, after three Unity reinstalls and four restarts, still zero response in Unity.

Thanks again for all your efforts, though.

hmmmhhh, try disabling the unity plugin and then re-enabling it again, AFTER you have disabled OpenGL and then re-enabled it again.

I'm sorry I'm not really helping at all, I'm trying my best, but without actually using your computer, there's only so much I can do. I don't really know what else could be wrong?

---

### Post by mlnease on 2011-08-07
I'll give it a try, though up till now I've had no way to disable, enable or re-enable anything.  I'll try it one more time though and get back to you.

And by the way, no apologies are in order--I really appreciate your efforts.

---

### Post by mlnease on 2011-08-07
Well, I did try this from the GDE session--still no luck.  Maybe I should just reinstall Natty.  I could restore from a recent backup but I hate all the clutter from duplicate files...

Well, just thinking aloud.  You've really gone above and beyond--thanks a million, again.

---

### Post by wildmanne39 on 2011-08-07
Hi, this should fix your problem:

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
```
Unity --reset
```
Let it run for about three minutes then restart your computer.

You have tried so many things you may have to do this also.

These commands well reset all the settings in compiz. 
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1

```
Thank you

---

### Post by mlnease on 2011-08-08
Thanks!  Actually, I've already managed to get Unity working again.  I would've posted my solution but I'm afraid I don't know what it was--I tried so many different tricks I really have no idea which one worked.

However, since your code directly addresses (and presumably solves) the thread title, I'm going to go ahead and mark it 'solved'.

Thanks again--all--for your help.

---

### Post by wildmanne39 on 2011-08-08
Hi, I am glad you got it working and yes for future reference it will fix that problem most of the time.

---

### Post by popper668 on 2011-10-06
**Re: Restore Unity Defaults from GDE?** 			
 			 			 		   		 		 		Hi, this should fix your problem:

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key  combination does not open the terminal try ctrl+alt+f1 thru f6. Then  type this command in terminal to reset unity. 
 	Code:
 	Unity --reset 
Let it run for about three minutes then restart your computer.




thank you so much, this was very helpful

---

### Post by wildmanne39 on 2011-10-06
Hi, your welcome!

---

