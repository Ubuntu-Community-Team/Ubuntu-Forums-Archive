---
title: "Pentium 4"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by beginer101 on 2011-02-15
I salvaged a P$ with 1 MB ram and installed 10.10 on an 80 MB HD
the system is soooo sloooow.
is it not recommended for P4 machine?
It did a system check and it did not finish overnight

any advice?

---

### Post by TeoBigusGeekus on 2011-02-15
If you mean 1Gb of ram and 80Gb of hd then it should run perfectly.
What do you mean by system check?

---

### Post by kn0w-b1nary on 2011-02-15
I experienced similar problems, on a P4 1gb RAM. Until I switched to Xubuntu.

---

### Post by Kirboosy on 2011-02-15
[COLOR=Red]**Welcome to the forums! :D**[/COLOR]

Xubuntu or lUbuntu are recommended for slower machines. :)

---

### Post by beginer101 on 2011-02-15
I will give a try for Xubuntu
I will report any outcome later

Thanks

---

### Post by sikander3786 on 2011-02-15
Welcome to the forums :-)

You hardware seems pretty capable and 10.10 shouldn't slow it down at all.

Which graphics card is there? And what specific issues are there? How much time does it take to boot? And which applications you think are mostly slow?

Did you install the graphics drivers for your card?

---

### Post by snowpine on 2011-02-15
Welcome to the forums!

Ubuntu's system requirements are published here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I have run Ubuntu very successfully on Pentium 4 (and even Pentium 3) machines in the past.

Since you say the machine is "salvaged" I would recommend thorough hardware diagnostics before blaming Ubuntu for the problem.

One thing you can do is type the command "top" in a terminal to see what is using the most CPU and RAM. Also you should figure out which graphics card you have and determine if you have the proper video drivers installed. Video driver issues are a common cause of a sluggish system.

---

### Post by beginer101 on 2011-02-15
I takes longer than WIN XP for the login screen to show up as long a **five minutes**.
I figured it must be be hardware not software.
I have no video card installed just the video processor that came with the MB.
How do you run a hardware diagnostics?
It is "salvaged" because the original power supply was defunct and replaced with a new one.
Wiped put the HD that had WIN XP installed and installed 10.10.

---

### Post by sikander3786 on 2011-02-15
Please post the output of this command from Applications > Accessories > Terminal.

```
lspci | grep VGA
```

And when you PC is acting slow, copy/paste the output of this one also.

```
top
```

---

### Post by snowpine on 2011-02-15
The following terminal command will tell you which video card you have:

**lspci | grep VGA**

However a slow boot time (5 minutes is very long!) points to a different problem, maybe hard drive failure?

If you use the forum Search feature, you'll find existing discussions on hardware diagnostics, for example: [http://ubuntuforums.org/showthread.php?t=881617](http://ubuntuforums.org/showthread.php?t=881617)

---

### Post by Rex Bouwense on 2011-02-15
Go to System->Administration->System Testing.  Wait a minute that is for 10.04.  Perhaps it is the same for 10.10 as well.

---

