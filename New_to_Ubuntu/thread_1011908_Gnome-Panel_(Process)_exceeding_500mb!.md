---
title: "Gnome-Panel (Process) exceeding 500mb!"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-12-15
I have a lot of applets added to my gnome panel, however, after leaving my computer on for most of the day it shows 500mb RAM being used.
[B]
List of applets:[/B]
Fast user switching
Main Menu
Sticky Notes
Music Applet
Disk mounter
volume
force quit
notification area
clock
deskbar-applet
keyboard switcher
window list

I know this is a lot (its spread over 2 panels) BUT I use almost everything quit frequently. So, I would like to know if one of these applets is known to be giving problems.

Thanks,

---

### Post by Michael.Godawski on 2008-12-15
hi abhiroopb,

how many RAM do you have at all. 
```
free
```I would not be concerned with the usage of ram. It is the function of ram to be used.
Are your machine acting slower? If not, why being concerned?

---

### Post by abhiroopb on 2008-12-17
Thanks for responding. I have a lot of free RAM left, that isn't the problem. I was just wondering whether this was normal or not.

---

### Post by drs305 on 2008-12-17
> **abhiroopb said:**
> Thanks for responding. I have a lot of free RAM left, that isn't the problem. I was just wondering whether this was normal or not.

When I open System Monitor and display Processes, my gnome-panel says it is using 15 MiB.

---

### Post by Sukarn on 2008-12-17
mine is using 23.6 MiB, and I've got more applets than you.

---

### Post by abhiroopb on 2008-12-17
It appears that an applet is leaking memory. Am I using any that you're not?

---

### Post by drs305 on 2008-12-17
> **abhiroopb said:**
> It appears that an applet is leaking memory. Am I using any that you're not?

I have lots more too. I don't have Sticky Notes or Music Applet.

**Added:** After seeing the next post, I noticed I don't have desk-bar either.

---

### Post by Sukarn on 2008-12-17
I think it might be deskbar-applet, although I'm making a guess here. If I had to say that one of those applets was using up a lot of memory, I would say it was deskbar-applet. I'm not using the sticky notes or music applet either.

---

