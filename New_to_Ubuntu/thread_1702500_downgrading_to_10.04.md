---
title: "downgrading to 10.04"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by mrstir57 on 2011-03-07
I would like to do a clean install to replace 10.10. This system is dual boot with win xp. When i use the live cd and specify the partition manually and select the linux partition do i need to select a mount point ? I know i need to select the file type and check format.

---

### Post by wojox on 2011-03-07
Pretty much, that's why they call it man·u·al·ly. :P

---

### Post by mrstir57 on 2011-03-07
> **wojox said:**
> Pretty much, that's why they call it man·u·al·ly. :P
Is that a yes and if so what mount point? Please keep in mind i am a super noob the first OS install i have ever done was last week  and im still learning.:P

---

### Post by Bucky Ball on 2011-03-07
Select these, they are defaults in there:

/ = where your OS will live;
/home = where your personal settings and data live;
/swap = 2Gb or the size of your installed RAM if you intend to hibernate the machine.

This will replace your current 10.10 /, /home and /swap, although you can leave the swap - just make sure it is not ticked to format - the new install will pick up the existing /swap and use it.

;)

---

