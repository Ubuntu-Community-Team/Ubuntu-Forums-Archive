---
title: "Frustrated with X-Fi XtremeMusic and ATI x2900"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by drguerra on 2009-07-28
So it seems that my ATI x2900 won't work well on Ubuntu 8.10, and even worse with Ubuntu 9.04 using the restricted drivers. It lags the entire system immensely. In 8.04 the restricted drivers work great, compiz runs quickly and cleanly and it doesn't take many resources.

Unfortunately, my Creative X-Fi XtremeMusic won't work on 8.04, even after several hundred hours trying different methods to get it to work (OSS, OSS4, ALSA, the alpha build of ALSA with X-Fi support, and the Creative X-Fi driver itself. I can manage to get sound working on 8.10 and 9.04, but these methods won't work with 8.04.

So I'm immensely frustrated. I have a great computer that is crippled with driver issues. New versions of Ubuntu have awful ATI drivers for the x2900 pro, and 8.04 and older can't get my X-Fi soundcard to work.

It's really quite disheartening, considering I've successfully installed Ubuntu on all my family and friend's computers, and here I am, with a good PC that I want to use as a Media Center using Boxee on Ubuntu with so many driver problems.

Is there anyway I can use the 8.04 ATI driver in 8.10 or 9.04? Or is there any way I can possibly get my sound working with my 8.04? I'd ideally want 5.1 sound, but I'm not optimistic at all.

I don't know commands very well, I can really just copy and paste commands into the terminal, despite lots of practice and attempts at learning. 

If anyone can help, I'd appreciate it greatly. I just want sound and video to work. It's not asking for too much I hope.

---

### Post by j.bell730 on 2009-07-28
I'm not too sure about the ATI problem, as I don't have an ATI video card, but I have been successful with getting my X-Fi (XtremeGamer) to work using [these easy to follow directions]("http://ubuntuforums.org/showthread.php?t=870001"). And with flash on a 64 bit machine using [these directions]("http://ubuntuforums.org/showpost.php?p=5678390&postcount=9"), just in case...if you don't have a 64 bit machine, use the package at the top of the first post.

---

### Post by drguerra on 2009-07-29
[B]Creative 1.00 driver guide.

A note to all users:
This driver does not work with Ubuntu 8.04LTS (Hardy)
and the front panel does not work either[/B]

Yeah. I'm using 8.04 because 8.10 and 9.04 have terrible support for my video card. So I've tried that to no avail.

---

### Post by j.bell730 on 2009-07-29
Oh, right, sorry, I should have read better. [Try this one]("https://help.ubuntu.com/community/OpenSound"), it works with any version of Ubuntu.

---

### Post by drguerra on 2009-07-29
Unfortunately that doesn't work either.

---

### Post by Mark Phelps on 2009-07-30
> **drguerra said:**
> ... Is there anyway I can use the 8.04 ATI driver in 8.10 or 9.04? 

ATI doesn't list any X2900 card.  Do you mean X1900? IF so, you're right, there is no restricted driver that works but the problem is incompatibility with the XServer in 9.04.  Some folks have tried compiling an older Xserver, but they then ran into kernel problems.

---

### Post by lestatius on 2009-07-30
> **Mark Phelps said:**
> ATI doesn't list any X2900 card.  Do you mean X1900? IF so, you're right, there is no restricted driver that works but the problem is incompatibility with the XServer in 9.04.  Some folks have tried compiling an older Xserver, but they then ran into kernel problems.

here's the X2900 ati driver

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.3&lang=English)

I used this link:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

go to linux------>select graphic card.....etc :)

---

### Post by Mark Phelps on 2009-07-30
OK, I checked out both your links, including the Release Notes, and I still don't see any "X2900".  There is an X2600, and a 2900 HD.  Maybe, I'm just not seeing it.

---

### Post by drguerra on 2009-08-09
x2900 and 2900 HD are the same thing.

Also that driver won't work on 8.10 with my card, sadly. Runs way too slow. It lags my entire computer to the point it's unbearable.

---

