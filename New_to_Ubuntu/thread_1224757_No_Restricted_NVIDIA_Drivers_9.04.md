---
title: "No Restricted NVIDIA Drivers 9.04"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by spuddo on 2009-07-27
Hello, I am very new to Ubuntu.  I am in the playing and learning phase.  I have a Gigabyte motherboard M61PME-S2P with an integrated NVIDIA® GeForce 6100 / nForce 430 chipset.

I wish to instal the restricted Nvidia drivers but when I go to System->Administration->Hardware Drivers the screen says there are no resticted drivers installed and does not offer me any.  It is blank.

Am I doing someting wrong, or is there no restricted driver for this chipset?

---

### Post by CatKiller on 2009-07-27
The 6100 should be supported by NVidia's 180 GLX driver.

Do you have jockey-gtk installed?

---

### Post by overdrank on 2009-07-27
Hi and welcome, you may just need to update your system, you can use this command in the terminal located under applications, accessories.
```
sudo apt-get update && sudo apt-get upgrade
```
Or you may use update manager under system, administration.

---

### Post by spuddo on 2009-07-27
Thank you.  How Do I tell if jockey gtk is installed please?

---

### Post by CatKiller on 2009-07-28
> **spuddo said:**
> Thank you.  How Do I tell if jockey gtk is installed please?

You could use Synaptic (System &#8594; Administration &#8594; Synaptic Package Manager). I know that when I upgraded to Jaunty that package wasn't automatically installed, but that's the part of the Hardware Drivers tool that actually looks for the driver.

---

### Post by spuddo on 2009-08-01
Thank you for your help.  All I needed to do was update my system and the new driver appeared.  I have installed it and everything is fine.

---

