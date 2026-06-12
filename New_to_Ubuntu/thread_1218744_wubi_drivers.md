---
title: "wubi drivers"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Dayofswords on 2009-07-21
in the wubi site it says

> 
Wubi is Safe

You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, **and does not install special drivers**. It works just like any other application. Wubi is free of spyware and malware, and being open source, anyone can verify that.


does that mean it doesn't install all the driver ubuntu disc and installed on a seprate partion would normally install?

---

### Post by philcamlin on 2009-07-21
yes it installs everything you would see in ubuntu if you installed from the cd 

it doesnt install any crap to your windows machine :) is whats its saying besides the wubi application itself 

woo my 700th post :D

---

### Post by lavinog on 2009-07-21
> **dayofswords said:**
> in the wubi site it says



does that mean it doesn't install all the driver ubuntu disc and installed on a seprate partion would normally install?

Wubi is the full install with some file system differences from the normal install method.
It doesn't install any windows drivers. It does have the drivers that ubuntu needs.

Is there a specific driver you are concerned about?

---

### Post by Clorow on 2009-07-21
No, it does not install on a separate partition. It uses a technique called "loopmounting", where an image of a partition is stored as a file on the Windows partition. It installs Ubuntu to that file, and you have the option to boot from it as if it were a partition.

And just a warning I have to say to everyone:
**Only use Wubi to try Ubuntu temporarily!** If you use it long-term, and eventually your PC crashes while in Ubuntu, Windows will also be broken.

---

### Post by philcamlin on 2009-07-21
> **Clorow said:**
> No, it does not install on a separate partition. It uses a technique called "loopmounting", where an image of a partition is stored as a file on the Windows partition. It installs Ubuntu to that file, and you have the option to boot from it as if it were a partition.

And just a warning I have to say to everyone:
**Only use Wubi to try Ubuntu temporarily!** If you use it long-term, and eventually your PC crashes while in Ubuntu, Windows will also be broken.

and if your windows breaks ubuntu does too

---

### Post by Clorow on 2009-07-21
Heh. When I used Wubi, I was installing something in Synaptic, when a Debconf window popped up and crashed the computer somehow. IN THE MIDDLE OF AN INSTALLATION. I ran fsck and Ubuntu was fine afterwards, but Windows was completely broken - it wouldn't boot at all. Eventually we had to reinstall it.

---

### Post by lavinog on 2009-07-21
> **Clorow said:**
> 
**Only use Wubi to try Ubuntu temporarily!** If you use it long-term, and eventually your PC crashes while in Ubuntu, Windows will also be broken.

Can you shed some light on how wubuntu crashing breaks windows?

---

### Post by halsboss2 on 2009-10-02
yes please, I'd like to know exactly too, as WUBI would otherwise be my preferred installation method.

---

