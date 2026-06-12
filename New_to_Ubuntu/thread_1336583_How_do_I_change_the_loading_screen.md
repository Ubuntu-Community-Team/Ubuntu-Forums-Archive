---
title: "How do I change the loading screen?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Madel on 2009-11-24
How do i change the loading screen?

Actually, I don't want that graphical loading screen. I just want to see those text running, services loading with [OK] txt in the right side of the screen. Not the GUI.

In older GRUB, I just have to enter something to disable the GUI loading screen. I forgot how. And don't know how to disable that with Grub2. Don't even know if it's possible.

I need tips on how to disable the gui loading screen and just display those starting services txt at startup.

---

### Post by gorgon on 2009-11-24
not having tried grub2, in grub(1) you can enter your boot item (after entering grub, if necessary, by 'esc') by pushing 'e' and then 'e' again at the item that says 'kernel ....' remove the text that says 'splash' and add a '-v' for verbose.

if you'd like to have it like that permanently you can edit /boot/grub/menu.lst

although, i dont know if this is the same in grub2, someone else might know better :)

ciao,
g

---

### Post by Madel on 2009-11-24
Thanks for the reply.

I have just found a solution.
Removed "quiet splash" from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", from the file /etc/default/grub then do sudo update-grub

So, that makes my request solved.

---

