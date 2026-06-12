---
title: "Installing ATI drivers"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jetgraphics on 2010-06-04
I wish to install ATI drivers for my graphics card.
I access the "run" file, but it says it must be run as "superuser".

Question: HOW does one do that?

---

### Post by sandyd on 2010-06-04
> **jetgraphics said:**
> I wish to install ATI drivers for my graphics card.
I access the "run" file, but it says it must be run as "superuser".

Question: HOW does one do that?
```

sudo sh ./*filename*

```
you can just install the drivers from System -> Administration -> Hardware drivers you know.

---

### Post by porchrat on 2010-06-04
The one in that hardware drivers app is never the latest one though. I remember when I first got a 4850 on 8.04 the hardware drivers app didn't have a driver available so I had to get the one online. It was wicked unstable though.

Note that those drivers you get off the website are not the most stable things in the world. If you don't need some sort of new feature in the latest driver I would recommend you use the hardware drivers application to install it instead.

---

### Post by TBABill on 2010-06-04
Try here [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver). I got my ATi driver to work with this method. It did not come up as an option under hardware drivers from the menus so I had to do it this way.

---

### Post by lavinog on 2010-06-04
If you are trying to install the latest ati drivers from the website, make sure your card is at least a radeon hd2xxx or higher.
Actually make sure it is a supported card.  If your card is in legacy status (most cards that are older than 3 years old may be) you could break your system if you install the proprietary driver.

To install the driver use carlee's method:
```
sudo bash ati-driver-installer-10-5-x86.x86_64.run
```

---

### Post by QIII on 2010-06-04
"The one in that hardware drivers app is never the latest one though."  Depends on what you mean by that.  AMD/ATI has been making it a habit for several releases of Ubuntu to get  their latest drivers into the Ubuntu repos at the time of release --  before the driver is available for general consumption.  At the time of the Ubuntu release, the driver in the Ubuntu repos IS the latest driver, and it's only available for Ubuntu users.  Phoronix makes smart remarks about this with every Ubuntu release.  "AMD/ATI gives Ubuntu the candy again..." sort of stuff.

Unless you are hell-bent on having the latest driver, run with the one in the repo for your release.  No  fuss, no muss.

If you have a legacy card, you'll have to use the legacy driver, and that will take some work in the terminal

---

### Post by lavinog on 2010-06-04
the 10-5 driver does seem to have a memory leak if you use desktop effects.
The work around to recover the lost memory is to issue the glxinfo command every now and then...kind of weird that it works.

---

### Post by Stormtrooper42 on 2010-06-05
I have Kubuntu 10.04 64 bits and a radeon HD.

At first, I also went to ati/amd website, and downloaded the latest catalyst drivers. It worked but it was impossible to enable 3D acceleration, and even 2D rendering was incredibly slow.
The ones from "Hardware drivers" work much better. ;)

---

