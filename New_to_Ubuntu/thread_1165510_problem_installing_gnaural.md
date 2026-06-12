---
title: "problem installing gnaural"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by PerpetualM8tion on 2009-05-20
Hello, I am new to ubuntu and tried to install gnaural onto my computer, it installed and promted to the package manager, but then it came up with the error Dependancy not satisfiable libpango1..0-0 please advise as to how I can remedy this problem. Thank you!

---

### Post by madmaxou on 2009-05-22
try
 ```
apt -get install gnaural
```

---

### Post by keplerspeed on 2009-05-22
It should be in the repo. It is for me. So search synaptic for libpango1.0-0 and install that package.

apt-get, aptitude and synaptic all use the same repositories. A "Dependancy not satisfiable" means one of the required packages for gnaural is not in the repo. U can install it manually, by downloading it off the net: [http://packages.ubuntu.com/jaunty/libpango1.0-0](http://packages.ubuntu.com/jaunty/libpango1.0-0) but try and see if u can find it in synaptic first.

---

### Post by velmont on 2009-08-11
> **keplerspeed said:**
> It should be in the repo. It is for me. So search synaptic for libpango1.0-0 and install that package.

I've got Universe and Multiverse and everything. But I can't find gnaural in the repositories.

```
odin@bekk:~/Video$ apt-cache search gnau
odin@bekk:~/Video$ apt-cache search gnaural
odin@bekk:~/Video$ 

```

---

### Post by Khufucius on 2009-11-11
Hey,

I feel your pain.  I made a .deb of the AMD 64 bit version of gnaural (standard config), which I've attached to this post. (first time compiling from source!) Here's the information I used to make it happen:

- [http://www.linuxjournal.com/article/10491](http://www.linuxjournal.com/article/10491)
- [http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092) (especially bodhi_zazen's post, 3rd or 4th down)
- [http://sourceforge.net/projects/gnaural/forums/forum/498482/topic/2075570?message=7551897](http://sourceforge.net/projects/gnaural/forums/forum/498482/topic/2075570?message=7551897)

Hope that helps,

-K

---

### Post by lkstone on 2009-11-26
Thanks for the .deb file! I've been going nuts trying to find sndfile for my system.   Your deb worked great on ubuntu 9.1 (koala) x86-64.   -lk

---

### Post by Swirlingabyss on 2009-12-03
I tried it on 9.04 and am not getting any sound, even if i export it as a sound file first. Any help. I tried going into preferences, but all It gave me was a number. A number that does I know not what.

---

### Post by Swirlingabyss on 2009-12-03
It killed the sound for my entire computer. I removed the package but it can't get it back! I need sound on my computer for my work! Please help!

---

### Post by bescritt on 2009-12-14
Thanks for compiling Gnaural for x64 and making the .deb available!

---

### Post by Argiod on 2010-05-21
> **Khufucius said:**
> Hey,

I feel your pain.  I made a .deb of the AMD 64 bit version of gnaural (standard config), which I've attached to this post. (first time compiling from source!)

-K

Many thanks for this fine program. I will be manually adding presets from BWGen, the brainwave program I'm accustomed to under Windows. Once I'm done I will, of course, share with the group.

---

### Post by kokoshmusun on 2010-05-27
Argiod, totally, please share some gnaural presets, BWGen had great ones but gnaural comes with only one, so I really need to find some... cheers.

---

