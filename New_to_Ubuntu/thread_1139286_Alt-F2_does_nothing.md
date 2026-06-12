---
title: "Alt-F2 does nothing"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by ebeckhusen on 2009-04-26
I just noticed today that Alt-F2 is not bringing up a run box for me anymore.  I don't know when this happened, since I don't have to use it that often, but was wondering if anyone had any ideas what might have caused it to disappear and how to get it back?

Running Jaunty, upgraded from Intrepid

---

### Post by steve101101 on 2009-04-26
have you tried to restart.

---

### Post by ebeckhusen on 2009-04-26
System is fully up to date, and the other Alt+F combinations are working, just Alt+F2 doesn't work.  Not a huge deal, just more curious than anything.

---

### Post by fdrake on 2009-04-26
did u check your keyboard-shortcuts? system>preference>keyboard-shortcuts

---

### Post by ebeckhusen on 2009-04-26
Checked Keyboard Shortcuts and it's listed.  Cleared it and reset, still doesn't work.  Restarting machine made no difference.

---

### Post by fdrake on 2009-04-26
change the command to something else like firefox, to find out if the problem is the keyboard-shortcut or the command launcher.

---

### Post by ebeckhusen on 2009-04-26
Changed Alt+F2 to open Firefox, doesn't work.  Don't think it's the keys, or otherwise  Alt+Ctrl+F2 wouldn't work either, but it does.

---

### Post by kirk ammon on 2009-04-27
I have the same problem.

It started after I was messing around with Conky, AWN, and disabled gnome-panel through gconf editor. I don't know if that has anything to do with alt+f2 not working, but I thought some more info might help? 

It is still listed under keyboard shortcuts and the keys still work.

---

### Post by ebeckhusen on 2009-04-27
> **kirk ammon said:**
> I have the same problem.

It started after I was messing around with Conky, AWN, and disabled gnome-panel through gconf editor. I don't know if that has anything to do with alt+f2 not working, but I thought some more info might help? 

It is still listed under keyboard shortcuts and the keys still work.

Do you have Compiz running?  I don't know what prompted me, but I was checking out the Compiz settings in CompizConfig Settings Manager and noticed there was a setting for Gnome Compatibility.  I checked to turn it on, and Alt-F2 works.

---

### Post by mcduck on 2009-04-27
> **kirk ammon said:**
> I have the same problem.

It started after I was messing around with Conky, AWN, and disabled gnome-panel through gconf editor. I don't know if that has anything to do with alt+f2 not working, but I thought some more info might help? 

It is still listed under keyboard shortcuts and the keys still work.

The run dialog is actually feature of the gnome-panel, so when you disabled the panel you also lost this feature.

(I must admit that I have absolutely no idea why this feature is implemented in the panel, but that's just the way it is.)

If you want the feature without running gnome-panel you need to use some other tool to provide similar dialog and then set the Alt-F2 shortcut to start that program. You could give Gmrun a try, it seems like a good substitute for the panel's run dialog.

---

### Post by Roadbloc on 2009-04-27
i know this may sound a bit dumb, but can you check it is actually alt you're pressing. i had a proble where i kept on pressing Fn all the time

---

### Post by kirk ammon on 2009-04-27
I guess I'll just have to use gmrun. I reset Alt+f2 to gmrun and it is working fine. thanks!

---

### Post by Shwan.c on 2010-03-21
> **kirk ammon said:**
> I guess I'll just have to use gmrun. I reset Alt+f2 to gmrun and it is working fine. thanks!

works for me too

---

### Post by ricardisimo on 2010-09-30
Same problem here, but gmrun is not installed. Is gmrun what ALT+F2 is supposed to be calling, or just a similar program?

P.S. - I added "Run Application" to my bottom panel, and it works, but for the life of me I cannot determine just what app is being called by this. No process is added when I do this, at least as per the System Monitor.

---

### Post by mcduck on 2010-09-30
> **ricardisimo said:**
> Same problem here, but gmrun is not installed. Is gmrun what ALT+F2 is supposed to be calling, or just a similar program?

P.S. - I added "Run Application" to my bottom panel, and it works, but for the life of me I cannot determine just what app is being called by this. No process is added when I do this, at least as per the System Monitor.

Like I said on the first page of this thread, it's not any individual application. The default Run dialog in Gnome is a feature of gnome-panel.

If you have the panel running without problems and pressing Alt-F2 doesn't open the dialog you should check your keyboard shortcuts (in both System/Preferences/Keyboard *and* Compiz options if you use visual effects). Make sure that Alt-F2 isn't defined as shortcut for anything else.

---

### Post by ricardisimo on 2010-10-03
Well, this is interesting... My ALT key is not an ALT key after all. It is Mod5, whatever that means. And the right ALT key is "ISO 3rd Level..." somethingsomething. I should mention that my keyboard layout is not US Standard, but rather USA International (AltGr dead keys). That's probably the first issue here. The second is selecting both ALT keys as 3rd Level choosers in System > Preferences > Keyboard > Layouts > Options...

Just a guess. Seems like a bug to me, though. I would think there would be a simple workaround for it. I'm going to have to go through and change every ALT key to Mod5 on whatever shortcut where it appears. But what happens in the future if I decide to change layouts? Definitely a bug as far as I can tell.

---

### Post by ricardisimo on 2010-10-04
Exceedingly odd. On my other computer, or maybe even the same computer on a different account (it's been a few days and I forget if I was toying with this here or at home) ALT+F2 - in fact all of the ALT combinations - works just fine. All of the same layout, locale and language settings apply to both computers, so I'm at a loss.

---

### Post by WestCoastSuccess on 2010-11-07
One of the things, as somewhat mentioned above, which can cause this is Compiz. The solution is to go to Preferences > CompizConfig Settings Manager > Gnome Compatibility (you'll find this at the top in the "General" section). Once inside the Gnome Compatibility settings screen, you'll see, under the "General" tab, "Run Dialog". Make sure it shows Alt+F2 (or, really, whatever you want to use as your shortcut keys), then make sure you check the box at the left which says, "Enable Gnome Compatibility". You should immediately get your Alt+F2 = Run Dialog back.

PS: If you don't have the Compiz Settings Manager installed, just go to Synaptic and search for, "compizconfig-settings-manager" (you'll need to have the "universe" repository enabled) and install it. It will appear in your Preferences menu.

---

### Post by I'mGeorge on 2010-11-07
well you can always define it again as a keyboard shortcut

---

### Post by robsc on 2010-11-07
try alt + fn + capslock +f2

---

### Post by philak on 2011-02-16
This works for me. Why this combo works I don't know.

---

### Post by Monotoko on 2011-02-16
Why bring a 2 year old thread back to life?

---

