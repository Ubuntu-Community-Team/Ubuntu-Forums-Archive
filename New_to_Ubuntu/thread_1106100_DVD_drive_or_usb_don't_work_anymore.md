---
title: "DVD drive or usb don't work anymore"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-03-25
Using pcmanfm as file manager and when I click on either in side panel it says directory doesn't exist
What am I doing wrong?

---

### Post by kanikilu on 2009-03-25
Can you try another file manager (nautilus?), or from the terminal to try to rule out a problem specifically with pcmanfm?

---

### Post by S0m3th1ngw13rd on 2009-03-25
from command line I tried 

mount command

tried doing cd /media/cdrom0     this used to work

also tried with nautilus but nothin yet

NOTE: I'm using fvwm-crystal as WM
recently changed to this WM and thats when it quit working

---

### Post by kanikilu on 2009-03-25
When you put a CD in the drive, can you go to a terminal and type: ```
mount
``` do you see /media/cdrom listed? If not, it doesn't look like it's mounting, so you may need to do it manually, something like ```
mount /dev/scd0 /media/cdrom
``` (scd0 for me, yours may be different).

If so, can you do ```
cd /media/cdrom
ls
``` If so, it's definitely mounted and readable. If not, do you get any errors?

---

### Post by S0m3th1ngw13rd on 2009-03-25
Fixed it with a 


```
mkdir /mnt/media
mount -o ro /dev/sr0 /mnt/media
```

Thanks for your input all

now I can use handbrake again yay

---

