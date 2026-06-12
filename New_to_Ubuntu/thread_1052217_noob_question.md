---
title: "noob question"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by thebozenator on 2009-01-27
sorry for the noob question but i haven't had to do this in a while... what is the terminal command to edit GRUB's menu.lst from from the install disk?

---

### Post by ChildOfMana on 2009-01-27
```
sudo gedit /boot/grub/menu.lst
```

It also helps if you have a more descriptive thread title :)

---

### Post by thebozenator on 2009-01-27
sorry :o 

i actually thought that was what it was but when i do that it sends me to a blank file. I think it is because it is sending me to at temp file used by the cd.I probably should have mentioned this before but i have a dual boot setup.

---

### Post by bobbob1016 on 2009-01-27
Actually, if you want to edit your menu.lst that is on your HD from a LiveCD, you have to mount your drive in the LiveCD.  Open "Partition Editor" from System, that'll tell you what drive to use.  Then in a terminal window on the LiveCD, type "sudo mkdir /media/root" then press enter then type "sudo mount /dev/sda1 (or whatever your / drive is) /media/root" then enter, then lastly type "gksu gedit /media/root/boot/grub/menu.lst".  Typing this from my Blackjack phone, so I can't check that the directions are 100% accurate, but the ideas are, you want to mount your internal drive, and modify it's menu.lst.

---

### Post by ChildOfMana on 2009-01-27
S'okay, just a heads up :)

Generally, if you try to edit a file that doesn't exist it will create one... so if you get a blank file you may not have a menu.lst in the specified location.

When you say you're using a Live CD, I assume you already have Ubuntu installed but had a problem with GRUB so have booted the Live CD to try to fix it?

Or have you not yet installed Ubuntu?

---

### Post by jerome1232 on 2009-01-27
If your wanting to edit the one that's one your filesystem you will need to mount that first.

So if your root partition is at /dev/sda1 then you would do this

```
sudo -i
mount /dev/sda1 /mnt
nano /mnt/boot/grub/menu.lst
```

---

### Post by ChildOfMana on 2009-01-27
[quote="bobbob1016"]Actually, if you want to edit your menu.lst that is on your HD from a LiveCD, you have to mount your drive in the LiveCD. Open "Partition Editor" from System, that'll tell you what drive to use. Then in a terminal window on the LiveCD, type "sudo mkdir /media/root" then press enter then type "sudo mount /dev/sda1 (or whatever your / drive is) /media/root" then enter, then lastly type "gksu gedit /media/root/boot/grub/menu.lst". Typing this from my Blackjack phone, so I can't check that the directions are 100% accurate, but the ideas are, you want to mount your internal drive, and modify it's menu.lst.[/quote]

Can't believe I didn't think of that :eek:. My apologies!!

---

### Post by thebozenator on 2009-01-27
Thats what i was missing!!! 
Thanks Bob.
I should have known that... XP

---

