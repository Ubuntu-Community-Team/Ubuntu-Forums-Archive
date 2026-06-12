---
title: "Help clearing up hard drive space ?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by NetTripper on 2009-03-29
I just upgraded to ubuntu 8.10 from 8.04. Fairly new to linux. Learning the do's and do not's ! My question is this. I am using 8.10 on a P2 400 Mhz machinem with a 7-8gig hdd. With the current upgrade to 8.10 i have 3.5gig free. Nothing major there you say ? I have noticed a slow down or lag in the system. I suspect it is related to low hdd space. Would like to know how to go about uninstalling unneeded apps and programs. Or how to clear up hard drive space in general ?

On a side note. I have an Ati video card that ubuntu appears to have not installed or using the correct drivers ? I am in low image mode.
Video card is an ati rage/rago pro card. Older then sin, i know. But figured ubuntu would supoort it. If it does can someone direct me in the right direction ?

Thanks for any help. And sorry if this is a question already covered. Was unable to find alot of information regarding either issue ! Again thanks for your time guys and gals ! :popcorn:

---

### Post by hovzio on 2009-03-29
hi

```
sudo apt-get clean
```

this will clean up apt's package cache, there may or may not be a bit in there.

---

### Post by mvalviar on 2009-03-29
Try ```
sudo apt-get autoremove
```

more here>>>[http://ubuntuforums.org/showthread.php?p=800462#post800462]("http://ubuntuforums.org/showthread.php?p=800462#post800462")

---

### Post by NetTripper on 2009-03-29
> **hovzio said:**
> hi

```
sudo apt-get clean
```

this will clean up apt's package cache, there may or may not be a bit in there.

That's was fantastic. I did that, and it cleared up almost 1gig of space! Might sound odd. But can a difference already. Thank you greatly ! :D

---

### Post by pbpersson on 2009-03-29
For your video problem, use synaptic package manager and search for something wonderous that should solve your problem - here is the description:

[B]EnvyNG is an application written in Python which will download the
latest ATI or NVIDIA driver or the Legacy driver (for older cards)
(according to the model of your card) from ATI or Nvidia's website
and set it up for you handling dependencies (compilers, OpenGL,
etc.) which are required in order to build and use the driver.[/B]

---

### Post by hovzio on 2009-03-29
> **NetTripper said:**
> That's was fantastic. I did that, and it cleared up almost 1gig of space! Might sound odd. But can a difference already. Thank you greatly ! :D

Cool, glad to be of help ;)

---

