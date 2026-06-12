---
title: "Dual Boot Issue"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by sarcazmo on 2009-01-11
Well I recently installed Windows 7 on my linux laptop with the hope of dual booting.

After that, only windows would startup so I re enabled grub from a live cd. 

I tried following the directions located [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu")
to add a windows option to my grub. 

When I restart the computer, I push esc and the grub menu shows up.  I go down to Windows and press enter and it doesnt work...

Not sure what I'm doing wrong.  I noticed on the guide above, it assumes /dev/hda1/ is my windows partition.  Mine is dev/sda2.  I'm not sure what I'm supposed to do to make it recognize that?

Thanks!

---

### Post by adult swim on 2009-01-11
sda2 would be like
```
title		Microsoft Windows
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by sarcazmo on 2009-01-11
> **adult swim said:**
> sda2 would be like
```
title		Microsoft Windows
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

Tried that, I get an error 13: Invalid or unsupported executable format.

---

### Post by stevoo on 2009-01-11
perhaps windows 7 uses something different to boot. Since not many people have actually done that, if the normal one doesnt work youll have to google that perhaps ....

---

### Post by sarcazmo on 2009-01-11
Boy do I feel like a dummy!

 I had "rootoverify" rather than "rootnoverify"  used (hd0,1) and it works like a charm!  Thanks!

Is there any way I can make it boot directly to the grub menu without having to hit esc?

---

