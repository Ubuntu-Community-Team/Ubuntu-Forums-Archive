---
title: "how to utilize more of my 8Gigs of ram for a faster system."
date: 2009-06-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-29
I love my Jaunty but I would love to make it a little snappier.

I have an intel quad 2.83Ghz cpu with 8 gigs of 1066mhz ram and a 10,000rpm HD 

Even with all this fast hardware usually when I launch something in Jaunty, although everything runs fast, there is often a lag between clicking something and when it opens. sometimes one second sometimes half a second. Not a big deal but...

Is there an option in Jaunty to utilize more of the ram i have installed by preloading things I often use or leaving things in ram when I close their window.

I know there is some kind of technical term for this but I have forgotten it. Read ahead or something like that.

I have tested this hardware setup with other operating systems and have found Jaunty to be the least snappy. I would very much like to be able to say the opposite.

Any help is appreciated.

Powel

---

### Post by Mark Phelps on 2009-06-29
If you installed the 32-bit version, AFAIK, apart from setting up things like RAM disks, there's nothing you can do to utilize more memory because 32-bit addressing limits the usage to a little over 3GB.

---

### Post by Paqman on 2009-06-29
Sounds like you want preload, it adaptively caches apps that you use regularly so that they'll launch quicker. Note that it takes a little while to learn your habits, so you won't see an immediate improvement.

---

### Post by WRDN on 2009-06-29
To use more RAM (as opposed to swap), you can change the swappiness value of the system. To do this, open the Terminal and type:

```
gksudo gedit /etc/sysctl.conf
```

Add to the bottom of the file the text:

```
vm.swappiness = 0
```

0 indicates the system won't use the swap at all (unless it has to). You can change the value to something between 0 and 100.

You may also want to look at [preload]("http://packages.ubuntu.com/hardy/misc/preload") which monitors usage, and loads commonly used programs into memory for you.

---

### Post by halitech on 2009-06-29
which version did you install?

whats the output of
```
uname -a
```
should get something like this
```
daryl@debian:~$ uname -a
Linux debian 2.6.26-2-amd64 #1 SMP Thu May 28 21:28:49 UTC 2009 x86_64 GNU/Linux

```

---

### Post by powel212 on 2009-06-29
I am running 64 Bit

I have swap turned off and did not notice any difference with swap on or off as I have so much overhead in RAM.

I will look into preload.

Thanks for the feedback.

Powel

---

### Post by powel212 on 2009-06-29
Is preload configurable?

I have installed it and it is now running but I can't find a GUI configuration window anywhere.

Powel

---

### Post by mikechant on 2009-06-29
> I can't find a GUI configuration window anywhere.

There's no gui supplied. You can edit the config file with the terminal command
```
gksudo gedit /etc/preload.conf
```
This file should have comments in it which explain the various parameters.

The following article seems like a useful introduction to preload:
[http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

It also tells you where to find the log files that let you know what preload is doing.

---

### Post by powel212 on 2009-06-29
Thanks for the info.

Sounds great and seems to make a difference already.

I couldn't find anything in "man" about it so thanks again for the info and help.

Powel

---

