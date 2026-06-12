---
title: "ubuntu freezes on boot, can i see why?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by adobrakic on 2010-09-18
Once I reboot my computer, this happens twice and then stops, next time I reboot, freezes for two or so reboots and starts up fine, etc. etc.: it freezes just as the desktop begins coming up, the only thing you see is the mouse on a black background. alt+ctrl+bckspce or whatever the combo is (dont wanna test it out now) doesnt work, the mouse doesnt move; i end up having to do a hard reboot (holding power button -- something i dont like doing) to restart the pc.

is there a log saved somewhere for me to see what happens just before it freezes? its getting quite aggravating. 

thanks

p.s - ubuntu 10.04 64bit

---

### Post by Ocxic on 2010-09-18
check "/var/log"  all the system logs are there. older ones are numbered 0,1,2,3 etc...

look at dmesg

---

### Post by renkinjutsu on 2010-09-18
When you press capslock, does the LED light up as usual? If it's not a kernel panic, you'll be able to recover using [REISUB]("http://en.wikipedia.org/wiki/Reisub").

Also, you don't have to use ALL of REISUB, maybe you only need to use the REI part, just to kill X and stuff that's hanging your computer, and after REI, or just R, you are able to press ALT+F1 to get to a console

---

### Post by adobrakic on 2010-09-19
> **Ocxic said:**
> check "/var/log"  all the system logs are there. older ones are numbered 0,1,2,3 etc...

look at dmesg

i just did that, anddd... idk wtf any of it means. theres also so much in the log, i dont even know where to begin. and yes, i looked at the correct time and not the entire log.

@renkinjutsu just got the chance to test that.. three times :|. all three times, the caps button didnt work and i tried the REISUB combo and nothing happened, had to hard reboot.

---

### Post by renkinjutsu on 2010-09-20
A good rule is to look at the end of the logs. Maybe you can post a snippet of your log on here for people to look at it.

---

