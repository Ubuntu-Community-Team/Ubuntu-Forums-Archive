---
title: "blinking caps lock!?!?!?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by moose12 on 2009-01-27
i recently did a full install of 8.10, and it was working great. untill it began its freezing up. nothing works, not even the power button and the caps lock light begins blinking. i had to do a hard shutdown. this is happening mainly on firefox but has happened at other times too. is there any thing i can do to stop this?

---

### Post by ModelM on 2009-01-27
This is a kernel panic. When the kernel is paralyzed & can do nothing, it flashes the keyboard lights.

You might glean a clue or two by going over the log files.

---

### Post by moose12 on 2009-01-27
and i would go about doing so how?

---

### Post by moose12 on 2009-01-27
i did have the visual effects on normal and i dont have that great a video card, i changed it to none and its been better but it still happened

---

### Post by ModelM on 2009-01-27
System > administration > System Log

Check out "messages", "syslog", & "kern log". The most recent events are at the bottom of the file, so it's usually faster to read from the bottom up.

The entries are time-stamped so sometimes it makes things easier if you wait a couple of minutes after a kernel panic before you reboot. That way you can tell by the times the division between when your last session froze & the reboot began.

---

### Post by jtsc on 2009-01-28
Someone helping me with my kernel panics astutely suggested that the problem might be a Intel 4965 wireless chipset conflicting with a certain sort of wireless network... if [this]("https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless") could be your problem, try 

sudo apt-get install linux-backports-modules-intrepid

Good luck.

---

### Post by moose12 on 2009-01-28
i didnt think about the fact that it was happening while i was on a wireless  network, and i do have an intel i will try that command and get back to you, thanks a bunch.

---

