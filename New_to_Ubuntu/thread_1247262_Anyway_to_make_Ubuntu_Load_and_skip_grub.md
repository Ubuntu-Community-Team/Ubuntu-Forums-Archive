---
title: "Anyway to make Ubuntu Load and skip grub?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Codix121 on 2009-08-22
I've completely turned over to the darkside,
and got rid of windows all together,
now I'm all ubuntu all the time!
uhm just curious, since the grub list, is a bit pointless,
now without windows,
anyway to just make Ubuntu load automatically without
having to go through the grub and select my operating system?

---

### Post by wizard10000 on 2009-08-22
> **Codix121 said:**
> I've completely turned over to the darkside,
and got rid of windows all together,
now I'm all ubuntu all the time!
uhm just curious, since the grub list, is a bit pointless,
now without windows,
anyway to just make Ubuntu load automatically without
having to go through the grub and select my operating system?

The grub list isn't pointless  :)

Someday you may want to boot the machine into single user mode to unbreak something that's been broken - also when your kernel is updated you want to be able to select the previous kernel until you're sure nothing broke.

You can remove the Windows entry from the grub menu by editing /boot/grub/menu.lst - you'll have to be root to edit it, though.

---

### Post by Liolikas on 2009-08-22
Add:
default=0
timeout=0
Lines into menu.lst top or edit them to 0 if already exists. 
Means select first option by default after 0 seconds. You still can enter menu by hitting esc many times as PC starts.

---

### Post by running_rabbit07 on 2009-08-22
Go to System>Administration>Synaptic Package Manager and install startupmanager. Once install it will let you select which kernel to install and the you can also select not to show the grub menu.

---

### Post by Codix121 on 2009-08-22
default=0
timeout=0

that sounds good, thanks!
and I know grub isn't POINTLESS, lol.
I wasn't planning on ERASING it,
just bypassing it, until I need it.

Thanks for the help!

---

### Post by wizard10000 on 2009-08-22
> **Codix121 said:**
> default=0
timeout=0

that sounds good, thanks!
and I know grub isn't POINTLESS, lol.
I wasn't planning on ERASING it,
just bypassing it, until I need it.

Thanks for the help!

So if you set the timeout to zero how do you use it when you need it?  You'd have to boot from a live CD and edit menu.lst  :)

---

### Post by gn2 on 2009-08-22
> **wizard10000 said:**
> So if you set the timeout to zero how do you use it when you need it?  

Press Esc repeatedly at boot.

---

### Post by mcduck on 2009-08-23
> **wizard10000 said:**
> So if you set the timeout to zero how do you use it when you need it?  You'd have to boot from a live CD and edit menu.lst  :)

It never actually sets it to zero, even if you try.

If I remember right the shortest you get is a hidden menu with a 3 seconds timeout to press ESC to show the menu.

---

### Post by Codix121 on 2009-08-23
I wouldn't have to boot from live CD?
I would just do sudo gedit, and set the timeout back to 10 seconds? lol...
and yeah it still has a 2-3 second screen,
but ill try the startup manager way,
Not fond of startup manager my splash screens dont even work :(

---

### Post by markbuntu on 2009-08-23
If you break your system bad enough you can break the kernel grub is trying to boot and you will not be able to change that unless you are quick. Autologin is also a very dangerous option.

---

### Post by mcduck on 2009-08-24
> **Codix121 said:**
> I wouldn't have to boot from live CD?
I would just do sudo gedit, and set the timeout back to 10 seconds? lol...
and yeah it still has a 2-3 second screen,
but ill try the startup manager way,
Not fond of startup manager my splash screens dont even work :(
uncomment the "hiddenmenu"-line if you want to hide the menu. It's just nder the timeout.

And, like  said, you'll always have 3 seconds of time to press esc to show the menu.

---

