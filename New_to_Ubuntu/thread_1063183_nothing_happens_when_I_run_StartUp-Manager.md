---
title: "nothing happens when I run StartUp-Manager"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by deleyd on 2009-02-07
I installed StartUp-Manager via System > Administration > Synaptic Package Manager. When I run it, System -> Administration -> Startup-Manager, I get a brief message that it's doing "perform pre-configuration tasks", that message goes away, and nothing else happens. Shouldn't a window pop-up? I'm not sure how to use it if no window comes up.

OK hold on, now there is a window "StartUp-Manager", but it's not responding. I select "force quit", try starting it again, same thing. Something ain't right. Tried rebooting but that didn't help.

OK it seems to take several minutes for "StartUp-Manager" window to come up. That don't seem right. And it's frozen when it does come up.

---

### Post by diablo75 on 2009-02-07
Since you're having weird issues with it, you should probably check to make sure you've killed all instances of it via your System Monitor.  Either that or just log off and log back in.

I'm pretty sure you have to run the program as sudo, meaning you can't just click on that icon in your menu.  You should run it from terminal with the word sudo in front of the command

I think it's:

sudo startup-manager

I'm sure it's lowercase, but I don't know if it's exactly spelled like that (with the hyphen).  You could type sudo startup(tab key three times) to reveal a list of possible commands that begin with the word startup.

---

### Post by deleyd on 2009-02-07
OK I'm going to start a new post as I'm guessing the problem is I can't edit the menu.lst file. I try to manually edit it via gksu /boot/grub/menu.lst, and nothing happens. I suppose that could be why StartUp-Manager is hanging the system. This is more of an advanced problem, even though I'm a newbie. (Oh I see the editor finally came up after a few minutes, but it's hung.)

---

### Post by presence1960 on 2009-02-07
open a terminal and type > sudo startupmanager

---

