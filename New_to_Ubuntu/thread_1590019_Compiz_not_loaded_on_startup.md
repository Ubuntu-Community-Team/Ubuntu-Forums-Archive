---
title: "Compiz not loaded on startup"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by robfuller on 2010-10-07
Hello,

How can I set up my system so that it defaults to using Compiz after startup? Every time I restart Ubuntu it goes back to using Metacity (i.e. "none" in Visual Effects), and I have to go to System > Preferences > Appearance to switch to Compiz.

In gconf-editor, the key /desktop/gnome/session/required_components/windowmanager is already set to "compiz".

There's this old thread on the same subject [http://ubuntuforums.org/showthread.php?t=1201888](http://ubuntuforums.org/showthread.php?t=1201888) , but I'm not clear what the solution was. Do I have to add Compiz to the startup applications? Shouldn't there be a better way to make Compiz the default?

I'm using the Maverick 10.10 beta, and have CompizConfig (CCSM) installed, if that's relevant.

Thanks in advance,
Rob

---

### Post by NightwishFan on 2010-10-07
What is your grapics card? Did this happen before on this release? Or on a previous release of Ubuntu? Did you fresh install Maverick or upgrade from Lucid?

First, try resetting compiz. Go into CCSM, click "Preferences" in the bottom left corner. Below "Profile" click "reset to defaults". Under "Backend" does it say "Gconf Configuration Backend?" Also ensure "Enable Integration into the desktop environment" is checked. Close CCSM, open System -> Preferences -> Appearance, and choose "Normal". Log out and back in, does it work?

If not, try running (copy-paste) this command in a terminal.
```
sudo apt-get --reinstall install compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf compizconfig-settings-manager libcompizconfig0 python-compizconfig
```

Log out and back in. If it still does not work, answer the questions at the top of this post for me.

---

### Post by robfuller on 2010-10-07
Thanks for your help, NightwishFan. I have followed all your steps, but unfortunately no progress. When I logout and log in again, it has always reverted to using Megacity.

My graphics card is an ATI RS780M/RS780MN [Radeon HD 3200 Graphics]. I upgraded to Maverick from Lucid. But I didn't try to use Compiz until after I did the upgrade, so I don't know if there would have been the same problem in Lucid.

Any other ideas?
Rob

---

### Post by NightwishFan on 2010-10-07
Run these two commands, then log out and log back in.
```
rm -r .compiz
```
Then:
```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by NightwishFan on 2010-10-07
I am going to get some sleep, so I will be off. Last thing I can say, is if the above does not work, go to the power icon in the top right corner and start a guest session. In this session, does compiz start automatically? If so, this might be possible for me to fix. If not, I am stumped for now, and will get back to you.

---

### Post by robfuller on 2010-10-07
Running those two commands you mentioned still didn't make a difference. But when I start a guest session, Compiz *is* enabled automatically.

Thanks for all your suggestions. Let me know if you have an idea of what else I should try.
Rob

---

### Post by NightwishFan on 2010-10-07
It has to be a configuration issue then. If you do not mind losing some gnome settings, you can try running:
```
gconftool-2 --recursive-unset /desktop
```

If that does not work try resetting ALL settings with:
```
gconftool-2 --recursive-unset /
```

Log out after trying each once. Be sure to back up evolution email if you use it.

---

### Post by robfuller on 2010-10-07
Well, I've trying resetting everything as you suggested, and believe it or not, the situation is still the same. Logging out and back in always deactivates Compiz. But if I open a guest session, it starts with Compiz activated.

Maybe we'll just have to leave this be? Obviously it's not a big issue, it just seems weird to me.

Thanks for trying! Any other ideas, let me know...
Rob

---

### Post by NightwishFan on 2010-10-07
I know for a fact wiping all the configuration will fix it, but I would rather not have you do that.

---

### Post by robfuller on 2010-10-07
Yes, I think I'd like to avoid that too. Never mind. Thanks for your help anyway.

---

### Post by NightwishFan on 2010-10-07
Good luck. I will tell you if I find an easier way.

---

### Post by algoban on 2011-04-09
I know its an old post, but if someone also have this problem, the first thing you must do is check in 

/desktop/gnome/applications/window_manager/

with gconf-editor. If you see metacity, just change to compiz.

---

