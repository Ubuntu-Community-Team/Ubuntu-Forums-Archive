---
title: "Help with Broadcom 4311 wireless chip"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by xonecas on 2006-10-28
First of all, has anyone successfully made this work ?

So this is my situation:

I can get everything set with ndiswrapper, and get the "hardware present; driver present" message when I do "ndiswrapper -l".

But after this, all the documentation says "Now it works!" but with me it doesn't, and I noticed that my wireless card led light on my laptop, hasn't worked since I moved to linux, and I've been looking around and I tryied a couple of thins to turn the radio on, but whatever I do I can't get my wireless to work, and I think is because my internal pci card isn't powered up in linux.

Anyone that has anyidea how to help, please step up.

---

### Post by AlReece45 on 2006-10-28
Here you go (btw, forum search really helps):

[AMD 64 and broadcom 4311]("http://ubuntuforums.org/showthread.php?t=266088")
[Problem with Broadcom 4311 in Edgy]("http://ubuntuforums.org/showthread.php?t=278441")
[Wireless - from the beginning...again]("http://ubuntuforums.org/showthread.php?t=283696")
[Broadcom 4311 wireless card issue]("http://ubuntuforums.org/showthread.php?t=283547")
[dv2020, broadcom 4311 problems]("http://ubuntuforums.org/showthread.php?t=250083")

If none of those help you, do a forum search for "4311"

---

### Post by AlReece45 on 2006-10-29
Don't know why, but I read this again and it looked completely different.

Have you run the following before?

```
sudo ndiswrapper -m
sudo ndiswrapper -da
sudo ndiswrapper -di
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by ariefbayu on 2007-05-07
ah, so your trouble is 4311 chip.
We have same chip here.
You might want to consider reading my blog post for this problem as I have same problem too and I have solve it.
[http://bayu.freelancer.web.id/index.php/2007/05/05/setting-broadcom-wireless-device-in-kubuntu-in-detail-part-1/]("http://bayu.freelancer.web.id/index.php/2007/05/05/setting-broadcom-wireless-device-in-kubuntu-in-detail-part-1/")
Please note that I'm using Ubuntu 7.04 and converting it into Kubuntu 7.04 using repository (not fresh kubuntu 7.04 install).
If you still have problem, just write a comment there of write it here.

---

