---
title: "[SOLVED] system-tools-backends last update  breaking my connection?"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by jdackle on 2007-12-15
I'm not sure of this but...

Since I updated system-tools-backends (in Gutsy) about a month ago I started having problems with my connection (using the crapy Speedtouch 330 USB modem but that's what I've got...). It may be a coincidence but...

Anyways a few details:
Said modem setup since Dapper following [this howto]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") and working in Gutsy too til I did the said update.

Problem:
1. It DOES connect on startup! But that connection only lasts for some five minutes. After that it is impossible to redial (which I could whenever the connection got down for whatever reason before this update).
2. IF I use the Startup Manager and change the setup in a way that will make it display the progress-window "Apllying changes...", the connection on next bootup lasts for from half an hour to several hours straight!!! (I was trying to see somemessages on bootup and that's why I accidentaly found this out...). But once the connection is down I have to reboot to get some more Internet time...


Am I making any sense?

Can anyone help me (NOT in the psychological/psychiatric sense, whether I need that or not...)?


Thanks in advance! :)


EDIT: I've made a mistake here! The concerned package is **NOT system-tools-backends** but **gnome-system-tools** instead! See my post three posts below this one. Thank you.

---

### Post by jdackle on 2007-12-17
Bumping this up after the weekend...

And adding I have seen some people on the Web having problems with this modem and getting the following message on attempted dial-out:
> Timeout waiting for PAD0 packets
Unable to complete pppoe discovery

Can anyone help?

---

### Post by jdackle on 2007-12-18
rebump!

---

### Post by jdackle on 2007-12-18
Sorry folks...

I made a mistake... Where I wrote "**system-tools-backends**" you should read "**gnome-system-tools**".
This is tje package I updated (system-tools-backends hasn't been updated so far since Gutsy's release) and after which I started having weird problems.
The most annoying was this one I've mentioned here but I had other "unexplainable" problems: audio apps not playing m3u playlists where they did before, sound being mutted and alsamixer showing everything ok, and just a couple reboots ago (I'd been doing them frequently...), the kernel logger failed to start at bootup...
These the ones I remember now.

I have no idea how a package for Gnome can break the system at such a core-level (my modem dialout has nothing to do with Gnome and neither does my kernel logger and I suspect the mute-sound problem didn't either). But that's when the troubles started and I'm connected for a longer period of time I had been allowed the last 3 or 4 sessions...
Also something that may support my opinion that the gnome-system-tools package is the responsible here is the fact that when I did the changes to Grub's confi from the graphical, gnome, utility, I did get more than a few minutes online, but when I manually edited /boot/grub/menu.lst and then issued sudo update-grub (which is what I assume the gnome-frontend does) I did NOT get that result...

So, I have now **downgraded** **gnome-system-tools-2.20.0-0ubuntu2** to gnome-system-tools-2.20.0-0ubuntu**1**.

If this turns out to solve the problem, I'll post it here (and if it doesn't too!), mark this as solved and file a bug with launchpad.
In the meanwhile, I'll edit the first post's name ...


To MOD's: Maybe this thread would fit better in the "Installation and Upgrade" board?

---

### Post by jdackle on 2007-12-19
So... erm... no... The said downgrade did not fix the problem.

Thoughts continuously appreciated.

---

### Post by jdackle on 2007-12-25
bump-bump-lump-bump-bump!

No, I'm not happy with this.

Let's jsut say it's Christmas or somethin' (course, I'm listening more like to Leonarc Cohen at the moment)

But PROBLEM STILL TO BE SOLVED!

Apologies for shouting and thank you for listening. :)

---

### Post by jdackle on 2008-01-01
My connection seems stable now, after the last kernel update!

Hence I'll mark this as solved. :)

---

