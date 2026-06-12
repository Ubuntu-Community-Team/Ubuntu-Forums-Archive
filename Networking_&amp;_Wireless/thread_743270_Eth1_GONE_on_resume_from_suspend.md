---
title: "Eth1 GONE on resume from suspend"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by blazercist on 2008-04-02
hi guys, pretty simple and yet weird problem.

I have a Asus C90s lappy with a Intel 3495ABG wireless card.  Everything pretty much works out of the box and wireless is fine and connects everywhere.

The problem is that I can be surfing and using wireless and whatnot, I then suspend and that works fine.  I resume and that works fine.  But eth1 is now gone upon resuming.  no its not down its just gone.

sudo /etc/init.d/networking restart doesnt' help. any ideas why this happens and how to fix it?

EDIT SOLVED (sorta) : apparently its a bug in udev thats already being worked on.

---

### Post by gkiller on 2008-06-07
Care to post the bug number? I have the same problem and would like to follow the progress.

Thanks,
GKiller

---

### Post by ddumanis on 2008-06-09
Booting from Hardy kernel 2.6.24-16 is a good temporary fix. This still needs to be fixed permanently, though.
[INDENT]
sudo gedit /boot/grub/menu.lst[/INDENT]

and change the default boot number from 0 to whichever number in the list 2.6.24-16 falls.

---

### Post by gkiller on 2008-06-10
Because of a graver bug with frequency scaling, I have to use the 2.6.24-19 kernel, with which this is still happening.

In any case, I would not really recommend to anybody to use the 2.6.24-16 kernel because it has known security issues (newest security release is 2.6.24-18).

---

