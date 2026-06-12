---
title: "Can't burn DVDs"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by edbarnat on 2009-02-10
I am running Ubuntu 8.10 and several CD/DVDD packages including K3B 1.0.5 and a plextor PX 760 internal IDE drive.

I have successfully burned several CDs from ISO images but cannot seem to do the same with DVDs.

I have successfully made several ISO images that I can burn to DVDs if I transfer to Windows.

I can successfully test burn them using K3B but when I try the real thing I quickly get a message saying that OPC failed.

---

### Post by joey-elijah on 2009-02-10
Don't wanna state the obvious but : -

a) are you sure you have a DVD Burner?

b) is is a dvd-r, dvd+r etc and are you using correspoinding media? (DVD-R burner needs DVD-R discs etc)

---

### Post by crjackson on 2009-02-10
> **joey-elijah said:**
> Don't wanna state the obvious but : -

a) are you sure you have a DVD Burner?

b) is is a dvd-r, dvd+r etc and are you using correspoinding media? (DVD-R burner needs DVD-R discs etc)

The 760 is a DVD+/- DL burner, it will burn pretty much anything.

He said the same files burn under windows.

@edbarnat,

I've had trouble with k3b and brasaro burning DVD's on one of my machines, whereas windows would burn them fine.

My solution - Install Nero for Linux and everything works perfectly. It may NOT be your solution, but I would download the DEMO for testing purposes anyway.

Lots of people here swear by k3b and will throw flams if you mention purchasing 3rd party software, but it was the end all solution for my and I have no reservations about tooting it's horn.

---

### Post by kdixon on 2009-02-10
haha, tooting its horn, thanks i have the same problem so i'll give that horn a toot myself

---

### Post by SamNSane on 2009-02-11
One other option is to install wine, and then to install ImgBurn under wine. ImgBurn (a Windows executable) is really the best optical burning software I've seen on any platform, and it's free. It works far better for me on my systems under both Hardy Heron and Intrepid Ibex than brasero and k3b. I'm not using it any more because brasero finally started working for me under 8.04 about a month-and-a-half ago -- following a kernel update from the repositories. Brasero still tells me that DVD burns fail at the point where it tries to read the freshly burned disc, but I've tested the burned discs and found them to be okay, so I've gone back to just using Open Source software.

---

### Post by edbarnat on 2009-02-11
Thank you all for the replies. It is good to know that I am not the only one having this problem. 

Guess I will have to fall back on Windows dependent software for the time being.

I will keep watching this thread in case a better, Linux based, answer is posted.

---

