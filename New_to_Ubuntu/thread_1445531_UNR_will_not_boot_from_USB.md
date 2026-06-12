---
title: "UNR will not boot from USB"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Skipjack138 on 2010-04-02
When I hit esc and it says boot from HDD (windows xp) or USB and then I go down and select USB but it boots windows!

I changed the boot order making (removable) priority 1 but nothing works! 

help please'

---

### Post by Chronon on 2010-04-02
How did you create the LiveUSB?  Is the partition bootable?

---

### Post by warfacegod on 2010-04-02
How exactly did you change the boot order? Did you do it from the BIOS or the boot menu?

---

### Post by warfacegod on 2010-04-02
> **warfacegod said:**
> How exactly did you change the boot order? Did you do it from the BIOS or the boot menu?

In my BIOS, USB's are read as hard drives not removable drives.

---

### Post by nauziem on 2010-04-02
I had the same... puzzled over it for some time.

On my system (an Asus Eee 1005P) There was one menu for select device to boot from (HD, CD, removable)
And a second for choosing which HD to boot, in which the USB appeared.

---

### Post by Skipjack138 on 2010-04-03
Downloaded  7zip to XP then looked into the iso and found somthing called wubi.exe.

That installed it so i guess problem solved?

---

### Post by warfacegod on 2010-04-03
> **Skipjack138 said:**
> Downloaded  7zip to XP then looked into the iso and found somthing called wubi.exe.

That installed it so i guess problem solved?

You've installed UNR inside of Windows as though it were a program. Nothing wrong with that especially, it will just use more of your hardware resources to run it. Don't judge it as a bum OS because of that.

---

