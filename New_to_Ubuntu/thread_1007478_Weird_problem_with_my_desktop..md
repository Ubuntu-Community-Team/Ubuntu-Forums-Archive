---
title: "Weird problem with my desktop."
date: 2008-12-10
forum: New to Ubuntu
---

### Post by TenaciousT44 on 2008-12-10
I just got xubuntu 8.10 installed on my computer two days ago and was showing off some of the finer points to one of my friends. I was demonstrating how pressing cntrl-alt-esc turns the mouse into a force-quit X of death, but didn't want to close any of the programs I had open, so I clicked it on the desktop, thinking it would be harmless. Now I can't put any icons on my desktop, nor can I change the background. I feel like this is just a ridiculously random problem, but I'm really at a loss for how to fix it.

---

### Post by Peter09 on 2008-12-10
Did you kill nautilus? Have you rebooted?

---

### Post by halitech on 2008-12-10
don't feel bad, I did this myself last week but with my dock :O

open a terminal and type```
start xfce4 &&
```or you can reboot, just make sure to UNcheck the option to save settings

---

### Post by Michael.Godawski on 2008-12-10
Try this:

[LIST]
[*]press alt+f2
[*]type in 
```
xfce4-panel &
```
[*]run it
[*]login again (ctrl+alt+backspace)
[*]report back :p
[/LIST]
edit: I guess try out [halitech]("http://ubuntuforums.org/member.php?u=69393") solution first...

---

### Post by halitech on 2008-12-10
> **Peter09 said:**
> Did you kill nautilus? Have you rebooted?

Xfce doesnt use nautilus, it would be thunar he killed by clicking on the desktop

Michael, wouldn't that just be the bars at the top and the bottom?

---

### Post by Michael.Godawski on 2008-12-10
> 
Michael, wouldn't that just be the bars at the top and the bottom? 	

Touché. :p

---

### Post by halitech on 2008-12-10
was just checking ;)

---

### Post by TenaciousT44 on 2008-12-10
So, I tried the xfce4-panel & command and for some reason that made it so that I couldn't do anything at all. My desktop was black and I couldn't access anything, not files not programs, nothing. So, I restarted the computer in recovery mode and voila, everything is all better now. But seriously, thanks for the suggestions. As a new ubuntu user, I was genuinely shocked and impressed by how quickly you guys addressed my problem. Thanks for being awesome.

---

### Post by cardinals_fan on 2008-12-10
> **halitech said:**
> Xfce doesnt use nautilus, it would be thunar he killed by clicking on the desktop

Michael, wouldn't that just be the bars at the top and the bottom?
Actually, it would be xfdesktop4.  Xfce doesn't follow the moronic tradition of handling the desktop with a file manager.

---

