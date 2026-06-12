---
title: "Bought a new hard drive, now there are no drivers?."
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-08-31
Recently i bought a new hard drive and installed ubuntu 10.04 via usb pen. With my old hard drive i always got the drivers installed no problem. Im using an Nvidia 9300 i think. Also, i upgraded once i installed and the update mentioned ubuntu 10.04.1, i never let my drivers update so that can't be the problem.

---

### Post by andrewthomas on 2010-08-31
> **Rave Gloves said:**
>  i never let my drivers update so that can't be the problem.
That, itself, may just be the problem

---

### Post by mapes12 on 2010-08-31
"Drivers" are to support hardware and are mainly a windoze thing. In Linux, hardware support is via what is built into the kernel, although there may be some packages that can help along the way.

If you still have your old HDD and it worked OK with your hardware then it should be possible to clone it to your new HDD. Can you hook up your old HDD to your system? If you can then go to Terminal ```
sudo fdisk -l
``` and post the output back here.

---

### Post by the.phantom on 2010-08-31
one BIG question

does your BIOS see the new hard drive?
BIOS is before a operating system, it is the heart of any computer, if it does not see the drive then the OS can't

---

