---
title: "What can I do with Powertop?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by lordjj on 2011-02-11
Hey guys, by the way, how do you use Powertop after installing it?
By typing "Powertop" in terminal, I get a sort of resource monitor. What can I do with the program?

---

### Post by Cracklepop on 2011-02-11
> **lordjj said:**
> Hey guys, by the way, how do you use Powertop after installing it?
By typing &quot;Powertop&quot; in terminal, I get a sort of resource monitor. What can I do with the program?

+1 for Powertop.  My netbook runs at 5.5 watts thanks to it.

I'd be interested to hear figures from peoples experience with Granola (NOT feelings or opinions).  It just seems a little odd to me: they give it away for free but won't let us see the algorithms at its heart, to protect their business...

---

### Post by uRock on 2011-02-11
Bump for moving to a new thread as the old one was, well, old.

---

### Post by 3rdalbum on 2011-02-11
> **lordjj said:**
> Hey guys, by the way, how do you use Powertop after installing it?
By typing "Powertop" in terminal, I get a sort of resource monitor. What can I do with the program?

Powertop displays the number of CPU wakeups-per-second for each program and kernel module.

You need to run it as root; "sudo powertop".

At the bottom of the window it will give you suggestions for options to enable that will reduce power use; it tells you "Enable SATA link management; press S" and stuff like that. Once you've done all those options, you can close Powertop.

Powertop is also useful for making informed program choices. If Openoffice (for example) shows up high on the list on Powertop, you could switch to another word processor that uses fewer wakeups-per-second.

You can also make a choice of kernel modules to disable, if these are causing the CPU to wake up.

---

### Post by unagimiyagi on 2011-05-14
I see what powertop aims to do, but is it possible to run powertop on reboot or when on battery power automatically?  I find that I'm having to hit U, P, W, A for all of those features each time I unplug.  Are there instructions on how to do that; I'm still new when it comes to shell scripting.

---

