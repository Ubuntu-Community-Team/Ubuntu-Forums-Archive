---
title: "drivers to increase my resolution from 800x600 for my note book without grapic card"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by kuchipudi on 2009-11-05
help me plz

i installed ubuntu in my wipro note book which has no graphic card. So its showing resolution of 800x600 so plz help me to increase the resloution from 800x600 to 1280x800.
can u plz post the drivers of audio and graphic card drivers pls

---

### Post by jimmy the saint on 2009-11-05
Have you checked the Hardware Drivers utility?

Go to 

System>Administration>"Hardware Drivers"

And see if any drivers show up there.  If there are, enable them.  If more than one video driver shows up, activate the "recommended" one.  Once it is finished doing what it does, you will need to reboot the machine for the drivers to be activated.

---

### Post by kuchipudi on 2009-11-05
I had gone through that but i is not showing any drivers

---

### Post by kuchipudi on 2009-11-07
plz i dont want to remove my ubuntu from my note book plz help me to change the resolution from 800x600 to 1280x780 plz

---

### Post by karimruan on 2009-11-07
Is installing a graphics card an option?

I didn't know that you could run a GUI OS without one. ;)

---

### Post by Ant59 on 2009-11-07
> **karimruan said:**
> Is installing a graphics card an option?

I didn't know that you could run a GUI OS without one. ;)

He's probably got integrated graphics.

What does this output?
```
lspci
```

---

### Post by The Real Dave on 2009-11-07
> **karimruan said:**
> Is installing a graphics card an option?

I didn't know that you could run a GUI OS without one. ;)

Think he means a chipset ;) Can you please run

```
sudo lshw > hardware.txt
```

That'll create a file called "hardware.txt" in your home dir. Post that here.

That'll at least show us what graphics controller you have. That could help in finding drivers

EDIT: The method in the previous post is alot quicker :) My bad :lolflag:

---

### Post by themusicalduck on 2009-11-07
Which version of Ubuntu have you installed? 9.10? or 9.04? Or something else?

Also run this in a terminal and post the output here -

```
lspci | grep VGA
```

9.04 had problems with intel graphics, which might be what you have. If you do a fresh install of 9.10, then it might fix things.

Otherwise post that output here and we'll see if we can help.

---

