---
title: "post installation issue"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by khupp on 2009-02-14
I'm a noob (although I have successfully installed and run Ubuntu on my laptop) and am trying to install Ubuntu 8.10 on my HP Pavillion Desktop (P4 2 GHz, 768 MB RAM) so I can learn more about Linux. I tried to install several times using the default settings and when I would reboot and login my screen would turn black except for the curser. I have tried just running Ubuntu from the disk without success. I have checked the disk and it passed. I have also tried Open Suse and Knoppix with similar results. I suspect there is some sort of issue with a driver and my video card. I don't believe my video card is bad because I have been running Windows for years on it with no issues. I appreciate any help.

---

### Post by jpoRS on 2009-02-14
Hey khupp,

It does sound like it could be a driver issue, though we need to know what kind of video card you have.  Try logging into a failsafe terminal (On the login screen go to "Sessions" before you actually log in.)  If that gives you a terminal try

```
lspci | grep VGA
```

That should tell you what video card you have, and we can go from there.

If you can't get into failsafe terminal, then there is probably a different problem, but we will cross that bridge when we get to it.

As a note for future posts, try and be as specific in your subject line as possible.  If you let people know what your problem is there, you are far more likely to attract helpful answers.

Anyway good luck and welcome to the community!
jim

---

### Post by khupp on 2009-02-14
Thanks for the tips. This is what I have. VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

