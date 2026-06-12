---
title: "Installed Video Driver...got slower, Im new please help"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by xdominitalianx on 2010-03-25
I'm completely new to ubuntu, I have installed ubuntu 9.10 and did a fresh install and the computer booted fine...I went to system then Administration then finally I clicked on Hardware drivers.

I activated the proprietary driver, and then was asked to restart the computer so I did so, when it reboted everything; graphics wise...became a-lot slower, I tried to enable compiz or extra desptop effects and it didn't let me.

Now I Don't know what to do...
solved....

I had to restart the computer twice then somehow it took affect :D

---

### Post by Doctor Mike on 2010-03-25
> **xdominitalianx said:**
> I'm completely new to ubuntu, I have installed ubuntu 9.10 and did a fresh install and the computer booted fine...I went to system then Administration then finally I clicked on Hardware drivers.

I activated the proprietary driver, and then was asked to restart the computer so I did so, when it reboted everything; graphics wise...became a-lot slower, I tried to enable compiz or extra desptop effects and it didn't let me.

Now I Don't know what to do...What driver did you install for what card?

---

### Post by xdominitalianx on 2010-03-25
Ati/Amd proprietary FGLRX graphics driver, and ATI Technologies Inc RV710 [Radeon HD 4350]

---

### Post by Doctor Mike on 2010-03-27
> **xdominitalianx said:**
> Ati/Amd proprietary FGLRX graphics driver, and ATI Technologies Inc RV710 [Radeon HD 4350]Ok, proprietary drivers in don't always work in 9.10 because there not custom to the OS. There's a lot of work going on to resolve ati driver issues. An earlier version (9.0-4) may work for now, or you could wait for Lucid Lynix to solve your video issues. I've had problems myself because ATI had not made the driver information available to linux debian software users. New information is being incorporated, but may only be available in most recent distributions. Please Uninstall proprietary drivers and use system default for now. It worked for me in 9.10 even though I had no real 3d.

---

### Post by coffeecat on 2010-03-27
If you're prepared to wait a month for compiz and special effects, the default open source ATI driver in Lucid (10.04) supports special effects with many/most recent ATI cards. The proprietary fglrx driver was pretty grim with my Radeon HD4200 card in Karmic (9.10), but I will be sticking with the open source driver in Lucid.

Since you are new to Ubuntu I would suggest you stick with Karmic and the open source driver for the next month and do without compiz. Lucid is still in beta so it's not a good idea for a new user to try it just yet. But when Lucid goes final, you should be OK to install it. Make your mistakes with Karmic (:wink:) and then do a fresh install of Lucid at the end of April. That's the best way.

---

