---
title: "how can i change the run level (aka what i see at boot)"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-27
can anyone tell me cuz i forgot and now i feel like a complete lamer. i want to watch the process at boot.  if anyone could tell me how i change it i do remember there were different numbers like 2 3 5 etc.
However, I still want to go into a GUI and NOT a shell!  So I guess this is a two part question how do i change the run level and what number do i use.   I only want to see the process at boot and then go into a GUI w/o having to do a "startx" command.
i don't think there is a innit file that i can modify w/ VI in ubuntu. 
Anyone have any ideas?

---

### Post by Gixxy on 2010-03-27
This might help... :) 

[http://ubuntuforums.org/showthread.php?t=542082]("http://ubuntuforums.org/showthread.php?t=542082")

---

### Post by PocketDog on 2010-03-27
> **Gixxy said:**
> This might help... :) 

[Link]("http://ubuntuforums.org/showthread.php?t=542082")

That won't work; he's on 9.10

Brad,
*Graphical method*: install startup-manager (It's in Synaptic, or **sudo apt-get install startup-manager** in a terminal).
Run it, and you'll have the options at the bottom:

[img]http://gerardmcgarry.com/files/images/startup-manager.jpg[/img]

*Text method:*
For a temporary verbose boot fix, at the Grub screen press 'E' when the Ubuntu boot entry is highlighted. You can remove 'quiet' for scrolling text under the Ububtu logo, and 'splash' to display just text.
 To make permanent changes, edit your grub options with ```
gksudo gedit /etc/default/grub
``` and remove the quiet/splash options there. 
Make sure you run ```
sudo update-grub
``` afterwards.

-----

[color=gray][size=1]You know what? I mis-read the OP's post *twice*; he didn't want a graphical solution, he just wanted his desktop to run after boot. Anyway, I'll leave everything as it is and move swiftly on...[/size][/color]

---

