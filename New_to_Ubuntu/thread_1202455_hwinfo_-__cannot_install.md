---
title: "hwinfo -  cannot install"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by richardnew on 2009-07-02
Hi All,
I have downloaded Ubuntu and I am running it from CD to determine if it is the distro I should be using.
The first problem is the screem resolution. The display says that the max is 800x600 (System - Preferences - Screen resolution).
I checked a few places and the issue appears to be the video card (not the monitor).
This is an old P3 machine and I do not know what the video card is.
So I tried to run hwinfo - not found
I tried to install it using the command sudo apt-get install hwinfo.
I get the error message "E: couldn't find package hwinfo"

I cannot determine what to search for to locate the package.
Any idea so I can give Ubuntu a decent " try before I buy" ?

Running Ubunto 8.10
Hardware CPU Intel P3 Katmai
memory 640M
Disk about 10Gb for Linux
Intel mother board I think
Extra Video card (not using motherboard video)
monitor LQ W1942T

---

### Post by WRDN on 2009-07-02
Use:

```
lshw -C display
```

---

### Post by Sef on 2009-07-02
I would try running the onboard video card, if the card has it.   That way you could tell if the problem is with the video card or not.

---

### Post by richardnew on 2009-07-02
Hi All,
I looked at a few more posts and located the lshw command. This works.

However the entry for the display says "display UNCLAIMED"
                       82740 AGP Graphics Accelerator (Intel Corp).

I seem to remember this was an issue when this machine ran Windows - hence the second graphics card.

Any ideas how I determine the card type and how I get Ubuntu to recognise it ?

Thanks
R.

---

