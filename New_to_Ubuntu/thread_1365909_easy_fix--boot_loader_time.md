---
title: "easy fix--boot loader time"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by hollowtd on 2009-12-27
I just want to change the boot loader time for ubuntu from 10 seconds to like 2. I've done this before but can't find out how but have opened gconf-editor. 

cheers

---

### Post by steveneddy on 2009-12-27
```
sudo gedit /boot/grub/menu.lst
```

Scroll down until you see the 

```
## timeout sec
```

line and change the value from 10 to 2

Easy as pie.

---

### Post by hollowtd on 2009-12-27
under the menu.lst tab it is blank. Where might I find the ## timeout? I'm in ubuntu 9.10

cheers

---

### Post by marshmallow1304 on 2009-12-27
If you have grub, the above post will work.


If you have grub2 (you do if you installed 9.10 (fresh install, not upgrade)), do this:
```
gksudo gedit /etc/default/grub
```
change the value of 
[QUOTE=/etc/default/grub]GRUB_TIMEOUT[/QUOTE]
to what you want and make sure the line is not commented out with a leading '#'.
Save and close, then run
```
sudo update-grub
```

---

### Post by hollowtd on 2009-12-27
I think that did it, cheers. I'll reboot and see now. Why is that so hard to find now?

---

### Post by hollowtd on 2009-12-27
I'll give it a go now. cheers

---

### Post by steveneddy on 2009-12-28
Sorry - I keep forgetting that Karmic runs grub2.

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Use_Startup_Manager_to_change_Grub_settings](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Use_Startup_Manager_to_change_Grub_settings)

---

