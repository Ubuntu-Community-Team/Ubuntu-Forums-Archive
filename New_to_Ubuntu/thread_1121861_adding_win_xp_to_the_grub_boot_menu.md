---
title: "adding win xp to the grub boot menu"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-04-10
:confused:I have two hard drives. one is my 60gb slave with windows xp installed, the other is my 80gb master with ubuntu 8.04 installed. I have two questions. 1.how do I put win xp on the grub boot menu? 2.how do I get the grub boot menu to show automaticly every startup? please note that I am new to linux and just installed it 2 days ago.

---

### Post by Elfy on 2009-04-10
Hi you can edit your menu list to add the xp and also to make the list show on boot.

Please run this from a terminal it will list your partitions

```
sudo fdisk -l
```

---

### Post by djbushido on 2009-04-10
To edit the grub menu do:"sudo nano /boot/grub/menu.lst"
To add XP, add ```
title Windows XP
root (hd1,0)
makeactive
chainloader +1
```
then do "sudo cp /boot/grub/menu.lst /boot/grub/grub.conf" to update the grub configuration.
That should be it.

---

### Post by carrierpilot1357 on 2009-04-10
ok I tried that, and win xp appears on the grub menu, I selected it, and I got the "starting up..." message and nothing happened. It did not boot up the operating system.

---

### Post by Elfy on 2009-04-10
Try adding map to the stanza 


> title Windows XP
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

---

### Post by carrierpilot1357 on 2009-04-10
it works now!:)! but how do I get the grub boot menu to show automaticly at every startup?:?:

---

### Post by unutbu on 2009-04-10
Near the top of /boot/grub/menu.lst, make sure there is a # mark in front of the word "hiddenmenu"
```

#hiddenmenu
```

and 

edit 
```

timeout		10
```

to give yourself time to see the menu. With "timeout 10" the GRUB menu will be visible for 10 seconds before automatically booting the default entry.

---

### Post by carrierpilot1357 on 2009-04-10
yay finally resolved!:p

---

