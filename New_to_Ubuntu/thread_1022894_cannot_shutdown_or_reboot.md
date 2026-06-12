---
title: "cannot shutdown or reboot"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-12-27
yesterday i had a very strange situation
if i clicked on the 'shutdown' button at the top of my screen, it gave me the usual dialog where i can choose between 'log-out', 'hibernate', 'other user', ... but 'restart' and 'shutdown' weren't there...
then i canceled and tried to open firefox to post this problem but nothing worked
i couldn't open a thing, not even the terminal
then i logged out and logged immediately back on and then everything worked again...
my question: how come it didn't work 5 minutes earlier?
and i believe this will just be a temporary solution, so how can i solve this problem if i have it again?

---

### Post by bumanie on 2008-12-27
On my 64 bit desktop shutdown/restart is under the System tab. On my 32 bit laptop they are located under the button at the top right of screen. I have no idea why they are different - afaik, I set them up the same way. Have a look in the drop down menu under the System tab. You can always do > sudo shutdown -h nowto shutdown or > sudo shutdown -r now to reboot

---

### Post by cmnorton on 2008-12-27
Did the button that would not let you shutdown/reboot let you log out? I am not clear after reading your post how you were able to log out but not shut down.

I'd look in your logs (/var/log), probably messages and syslog, and the output of dmesg. 

How much RAM is in this system?

---

### Post by bumanie on 2008-12-27
> **cmnorton said:**
> Did the button that would not let you shutdown/reboot let you log out? I am not clear after reading your post how you were able to log out but not shut down.

I'd look in your logs (/var/log), probably messages and syslog, and the output of dmesg. 

How much RAM is in this system?

Log out takes you back to the username/password screen without shutting down :).

---

### Post by kerry_s on 2008-12-27
sounds like a update that didn't finish.
or
you know what they say "linux can run for years with out rebooting or shutting down", maybe someone decided those options weren't needed. :lolflag:

---

### Post by Dadsgé on 2008-12-27
i'm using an eeepc, so i don't have that much RAM

i meant i didn't get the shutdown or reboot buttons, they weren't in the 'message box' (don't now how to call it) when i clicked on the shutdown button on my panel.
i also thought about shutting down trough terminal, but it didn't open, as all of my applications...

---

### Post by Dadsgé on 2008-12-27
> **kerry_s said:**
> sounds like a update that didn't finish.
or
you know what they say "linux can run for years with out rebooting or shutting down", maybe someone decided those options weren't needed. :lolflag:

lol indeed :P

---

