---
title: "Xorg won't work for my non root user"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by keiichidono on 2009-10-22
I installed Arch Linux 2009.08 x86_64 Core inside Sun VirtualBox 3.0.8 and got up to the part of the Beginners' Guide that tells me to test X and it can never work for my non root user. Funny thing is, I tried running it as root and it worked even though my root user has no ~/.xinitrc file. Running startx or xinitrc as my non root user I get a small (maybe 400x600) white terminal but can't use my mouse or keyboard. 

After looking over the guide and doing a step I forgot and adding in all of the extra stuff the guide says might help I can use my mouse and keyboard in my non root users' small white terminal but X still won't start properly with xterm even though I put 'exec exterm' in my non root users' ~/.xinitrc file. Please help. Thanks for any help guys.

---

### Post by tarps87 on 2009-10-22
I believe that is all an xterm session should show, xterm is a terminal emulator.

What happens when you run startx as root?

For Arch related questions I would try looking here as well:
[http://bbs.archlinux.org/](http://bbs.archlinux.org/)

---

