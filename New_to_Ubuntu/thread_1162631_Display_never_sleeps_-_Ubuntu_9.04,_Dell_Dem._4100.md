---
title: "Display never sleeps - Ubuntu 9.04, Dell Dem. 4100 w/Rage 128, Viewsonic VX910"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by beowulfshaeffer on 2009-05-17
As old as it is, this Dell Dimension 4100 chugs along as good as ever. It's a simple file server here in my home office, sharing files and music. I have a monitor on it for the occasional local session and such, although I usually VNC into it when needed.

However, while after the allotted time the screen goes black, the display never goes into sleep mode on this machine. When attached to another machine it does, so I know it's not the display.

So I assume one of two things:
[LIST=1]
[*]I don't have something set up right
[*]The video card isn't capable of sending the proper sleep signal to the monitor.
[/LIST]
I tend to think it's the former, as when I pull up Display Preferences, it shows me "Monitor: Unknown". I had a different, older CRT monitor on it when Ubuntu was installed several years ago, although this new monitor has been on this box for a few weeks. Clicking the "Detect Monitors" button does nothing.

Ideas?

---

### Post by mprince on 2009-05-17
Have you set a sleep time under *System>Preferences>Power Management*?

---

### Post by beowulfshaeffer on 2009-05-17
Actions: Put computer to sleep when inactive for: Never

That's good, as it's not handy to have a server asleep.

Display: Put Display to sleep when inactive for: 15 Minutes

Looks ok, and it turns the display black, but that's all.

---

