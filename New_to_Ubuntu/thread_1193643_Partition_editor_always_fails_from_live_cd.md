---
title: "Partition editor always fails from live cd"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ginestre on 2009-06-21
Finally got around to backing everything up so as to update to 9.04, wanting to do a clean update and redistribute disk space, eliminating XP which I haven't used for over a year. But from the live CD, every time I specify how to repartition the disk, the partitioner exits after doing nothing, and restarts.

Grateful for any help, as always.

---

### Post by shifty_powers on 2009-06-21
have you tried

a). just doing a dist upgrade from within 8.10


b). instead of going into the live cd desktop going for the install option from the initial menu

c). tried using the alternate install cd

?

---

### Post by RedSingularity on 2009-06-21
Is it a problem with the partitioner?  Try starting it from the terminal with.......


sudo gparted

Then do what you want to do and when it "breaks" see what message is displayed in the terminal at the time of breaking.

---

### Post by LewRockwell on 2009-06-21
You should check out Parted Magic!

[http://www.partedmagic.com/](http://www.partedmagic.com/)

---

### Post by Jimmyfj on 2009-06-21
We need to know a few things: Did you make the Live-Cd yourself? If so did you write the disk at the lowest possible speed? Sounds to me like you have a flaw on the Live-Cd.

If you have GParted installed on your system you can make your new partitions from within 8.10 - Just making a dist-upgrade won't remove your old WinXP partition and free the space for you. 

While you is going to make a clean install anyway I'd suggest that you make that install with the new EXT4 file system.

Now I said we need to know some things, so plz tell us more about your computers specs. That'll make helping a bit easier.

---

