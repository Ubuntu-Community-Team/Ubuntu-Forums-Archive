---
title: "Lucid Lynx 10.04 LTS CD/DVD Drive Not Working"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by hellolife on 2010-08-16
I just bought a HP G62 laptop and installed Lucid Lynx 10.04 LTS.
When I tried using my CD/DVD drive the computer did not recognize it.
I tried both playing a movie and burning a disc and it would not show up.

I've tried researching this problem specific to my computer but I've had no luck.
Any help or info would be appreciated.

Thank you.

---

### Post by rosehipzero on 2010-08-16
Do you know the model of the DVD/CD drive? maybe a missing driver? whats the manufacture of the DVD drive only

---

### Post by hellolife on 2010-08-16
The CD/DVD model # is HP CDDVDW TS-L633N.
I know it's a missing driver I'm just curious as to what to do about that.

---

### Post by rosehipzero on 2010-08-17
I was poking through a few things and when i use the synaptic package manager, the only HP related stuff is for printers.

Did anything come up when you installed the Gnome Hardware Drivers application? like for wifi, GPU drivers... anything for your DVD?

also, i had no luck on the HP website... couldnt find your model. I guess HP G62 isnt the full name

---

### Post by jtarin on 2010-08-17
Post your /etc/fstab file.

Also look at your BIOS startup screen and see what your computer recognizes your CD/DVD drive as.

---

### Post by hellolife on 2010-08-17
The full model number of the computer is G62-234DX.

As for the code /etc/fstab, I keep getting permission denied.

Also, when I go to my bios start up screen it says nothing about my CD/DVD drive.

---

### Post by sandyd on 2010-08-17
> **hellolife said:**
> The full model number of the computer is G62-234DX.

As for the code /etc/fstab, I keep getting permission denied.

Also, when I go to my bios start up screen it says nothing about my CD/DVD drive.
```

cat /etc/fstab
```

---

### Post by hellolife on 2010-08-17
I did some further research and found that I needed to install device manager as well as medibuntu. Seems to have solved the issue.

---

### Post by gupta_sumesh63 on 2011-07-12
Could you possibly give out as to what you did that your problem was solved for benefit for others?
Thanks

---

