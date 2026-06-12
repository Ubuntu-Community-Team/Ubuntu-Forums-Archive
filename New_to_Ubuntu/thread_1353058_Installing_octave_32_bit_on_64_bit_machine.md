---
title: "Installing octave 32 bit on 64 bit machine"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Hetepeperfan on 2009-12-12
Hi,

I'would like to run a 32-bit octave version on a 64-bit AMD machine. (to run software which is not supported for 64-bits machines)
If I type: sudo apt-get install octave3.2

I'll automatically end up with a 64-bit configured octave installation.

Is there an easy way to install a 32-bits version? 

Best Hetepeperfan

---

### Post by LuisGMarine on 2009-12-18
My best suggestion is that you run and install the program in a 32-bit chroot mode.  I have never done it myself, just heard of the procedure.  Here is the best documentation that I could find, hope this helps:

[https://help.uhttps://help.ubuntu.com/community/DebootstrapChrootbuntu.com/community/DebootstrapChroot]("https://help.uhttps://help.ubuntu.com/community/DebootstrapChrootbuntu.com/community/DebootstrapChroot")

---

### Post by jpkotta on 2009-12-19
> **LuisGMarine said:**
> My best suggestion is that you run and install the program in a 32-bit chroot mode.  I have never done it myself, just heard of the procedure.  Here is the best documentation that I could find, hope this helps:

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

You should double check your links to make sure they work (fixed above).  

But this is probably what I would do.  I've set up a chroot, it's not too bad.  You can force installation of 32-bit packages in a 64-bit system, but most times you need to install the dependencies as well, and they might conflict with the 64-bit versions.  Octave has many dependencies, so it's probably easiest to just make a 32-bit environment for it and let the package manager take care of all the details.

---

