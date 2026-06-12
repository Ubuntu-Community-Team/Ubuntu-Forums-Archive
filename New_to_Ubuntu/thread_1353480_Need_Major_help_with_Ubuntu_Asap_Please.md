---
title: "Need Major help with Ubuntu Asap Please"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Volcom350Z on 2009-12-12
Hey guys I was rebooting my computer, and randomly it takes me to this screen , and it wont let me go through so I really really need your guy's help on this.


it goes on to this screen


find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find menu.lst
find /boot/grub/menu.lst
command line
reboot
halt


I tried reboot , but it just turns off my computer and doesnt do anything.

This is so wierd my computer was working perfectly fine, and I didn't do anything except reboot my computer, any help would be greatly appreciated from you guys & gals!

---

### Post by spiderbatdad on 2009-12-12
Do you dual boot windows or use wubi install? If either did you suspend windows last time you used it? Boot windows. Shutdown cleanly.

---

### Post by Volcom350Z on 2009-12-12
yes I do, and okay next time I definitely well sorry. but how do i get out of this so I can go on my computer !

because when I click enter windows xp it just shuts down my computer and reboots ?

---

### Post by spiderbatdad on 2009-12-12
Are you using Karmic?
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Scrolling way down is a section on reinstalling grub2.
If you are using an earlier release the procedure is completely different.

---

### Post by Volcom350Z on 2009-12-12
> **spiderbatdad said:**
> Are you using Karmic?
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Scrolling way down is a section on reinstalling grub2.
If you are using an earlier release the procedure is completely different.

i'm using 8.0.4 hardy heron

---

### Post by sandyd on 2009-12-12
boot into livecd
```

sudo grub

```
```

find /boot/grub/stage1
//copy down the output should be something like (hdx,x)
root (hdx,x)
setup (hd0)

```

---

### Post by Volcom350Z on 2009-12-13
when i did all of your commands carlee non of them would work


I would get Error 23: Error while parsing number
and Error 21: unrecognized command!!

still need help please cant log in to my computer even on win xp

---

### Post by Volcom350Z on 2009-12-13
nvm i am just going to reformat my computer and re download ubuntu since I really need to go on my computer asap, and dont have any other options right now thanks again for trying to help me guys and gals.

---

### Post by lisati on 2009-12-13
> **Volcom350Z said:**
> when i did all of your commands carlee non of them would work


I would get Error 23: Error while parsing number
and Error 21: unrecognized command!!

still need help please cant log in to my computer even on win xp

You need to replace the "x" with whatever's in the output from the "find" command.

---

### Post by ubername on 2009-12-13
Lisati


'Don't be fooled by my post count or my join date: in many ways I'm still a beginner'

um - your beans are hidden

---

### Post by Volcom350Z on 2009-12-13
Oh I see what you mean , thanks again for everyone who helped me out, I had to reformat my computer anyways, so I just downloaded Hardy Heron version again, and now back with Linux :thumbs up:

---

