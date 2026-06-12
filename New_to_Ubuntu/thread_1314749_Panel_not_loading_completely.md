---
title: "Panel not loading completely"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by smitty96 on 2009-11-04
After I updated to 9.10, everything was working great. The next time I turned on the computer, though, the panel doesn't load everything. The Thunderbird and the Help icon (I think that's there by default... Right?) And the icons for things like wireless/pidgin/sound aren't there. Any possible reason for this?

---

### Post by SunnyRabbiera on 2009-11-04
how many icons did you have in your panel?
The Gnome panel has issues loading one too many icons

---

### Post by smitty96 on 2009-11-04
There weren't any more than there are by default. Just the three launchers, the menu, clock, logout menu, audio, wireless, and taskbar. The only thing that was different from a default panel is that I replaced Evolution with Thunderbird. But that worked fine in 9.04..

---

### Post by douglas_slac on 2009-11-04
I have the same problem.  And I can't control my sound right now, and I'm worried that when I change wireless, I'll lose the ability to connect to the internet.  Is there another way to connect to wireless without the panel wireless app?  I try to add these to the panel, and I can't see these listed in the "add to panel" apps list.  I also can't see any wireless control in the system prefs either.  How do I control wireless?

Also when I start skype (after updating to 2.1 to work at all), there is no skype panel icon.

How do I try to fix this?

---

### Post by douglas_slac on 2009-11-05
Argghh... finally found this.  I was looking for the NetworkManager app or some such.  Which does exist, but not as a specific panel app.  Or Sound control, or some such.  So, I seemed to have no way to control wireless or sound...

It turns out these things show up in the "Notification Area".  My Notification Area had disappeared as part of the upgrade.  I had to right click on the panel, and then "Add to panel", and add the "Notification Area".  Then my wireless control and sound came back.

There should be a note that this is more than just a notifications, this is the only place in Gnome/Ubuntu where you can control wireless, there isn't any other place it seems.  Just calling an info area just seem to do it justice in its central control.  This was quite annoying, and I couldn't find any help on this, or docs that this is where the control show up.

---

### Post by smitty96 on 2009-11-05
Thanks! Also, I think I figured out why they disappeared in the first place. I don't know why, but I think it was because they weren't locked on my panel. I'm not sure why that would cause this, but I know I unlocked them so I could move them around, and they're the only ones that disappeared.

---

