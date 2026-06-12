---
title: "Triple Boot Ubuntu/Vista/XP with seperate HardDrives"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by mobflip on 2009-01-08
i'm sure someone can answer this quickly....
i am dual booting ubuntu(hardy)/xp-sp3 with grub.  recently picked up a new HDD and copy of vista. i was planning on just unplugging my dual boot drive, installing vista on the new drive (thus hiding xp from vista which i read about) and thend just plugging all back in. will grub just recognize vista, do i need to take other measures? whats my best way about going about this??

---

### Post by Tim Sharitt on 2009-01-08
You will need to add you vista install to the /boot/grub/menu.lst.

```
gksu gedit /boot/grub/menu.lst
```

Scroll down to where the other OS entries are and add

```

title       Windows Vista
root        (hd#,#)
makeactive
chainloader +1

```

Where (hd#,#) is, substitute, the drive and partition number of your Vista installation. For example, the fist partition of the second drive would be (hd1,0).

---

### Post by kansasnoob on 2009-01-08
> **mobflip said:**
> i'm sure someone can answer this quickly....
i am dual booting ubuntu(hardy)/xp-sp3 with grub.  recently picked up a new HDD and copy of vista. i was planning on just unplugging my dual boot drive, installing vista on the new drive (thus hiding xp from vista which i read about) and thend just plugging all back in. will grub just recognize vista, do i need to take other measures? whats my best way about going about this??

No! It's going to be difficult!

[http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm](http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by wolfen69 on 2009-01-08
or you could leave well enough alone and just hit F12 or whatever your quick boot menu is, and select the drive you want to boot.

---

### Post by mobflip on 2009-01-09
cool, never had a reply anywere so quickly, you guys are awesome
first reply .... would i have to unable the vista bootloader? 

to the second reply .... i don't want xp and vista on the same drive.

and the third ... i would rather not have to enter the bios everytime i want to start vista. but i did read about that, so if i plug the vista drive and the xp/ubuntu drive in and for example load the xp/ubuntu in bios, grub on that drive won't mess with or touch the vista drive or otherwise cause any errors?

thanks everybody!

---

