---
title: "SD Card, Data Recovery"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by earthpigg on 2009-02-02
So. Shinedown concert last night was great. me and my buddies got backstage and where talking with the band for 5-10 min, something like that. one of my friends got the whole thing on video on his digi camera...

...then drunkenly deleted the video.

i was able to prevent further picture/video taking... anyone know how i would go about recovering this video?

---

### Post by Neural oD on 2009-02-02
go to this site: [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

should be what u need  - btw the also do photorec - look for it on the left panel

---

### Post by Neural oD on 2009-02-02
btw - testdisk is in the repos - just: sudo apt-get install testdisk

---

### Post by earthpigg on 2009-02-02
worked great, thanks!

---

### Post by Neural oD on 2009-02-02
glad to have helped :)

---

### Post by ZxEfR on 2009-02-03
Wow.....thank you for recommending testdisk.

I had been dinking around with installing W7 Beta and I forgot to unplug my 500gb backup drive with all my most important stuff! Well W7 touched the drive and bam left it partitionless.

So thanks to testdisk (I'll be making a donation to that guy ASAP) I recovered all my data very quick and very easy! Pretty powerful stuff!

---

### Post by earthpigg on 2009-02-03
This is the video you helped recover, btw:

[Shinedown Backstage with Drunk US Marines]("http://www.youtube.com/watch?v=lfQ4K0s3hc0")

:)

---

### Post by hellocatfood on 2009-09-16
Does anyone have step-by-step instructions on how to do this?

---

### Post by LewRockwell on 2009-09-16
> **hellocatfood said:**
> Does anyone have step-by-step instructions on how to do this?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[http://www.forensicswiki.org/wiki/TestDisk](http://www.forensicswiki.org/wiki/TestDisk)

[http://freewarewiki.com/TestDisk](http://freewarewiki.com/TestDisk)

[http://www.zoinks.org/home/technology/tech-wiki/sw-testdisk](http://www.zoinks.org/home/technology/tech-wiki/sw-testdisk)

.

---

### Post by ayenack on 2009-09-16
BTW. When you install Test Disk you also get photrec along with it. It's basically the same app but geared towards SD/MMC MS CF/MD SM cards (it can also be used for Hard Drives) and alike and recovering images/video.

To run photorec. In terminal.

**sudo photorec**

---

### Post by egalvan on 2009-09-16
The big names in memory cards have picture/video recovery software available on their websites,
and a call to customer support will usually result in have the program e-mailed to you.

A totally-computer-illiterate friend of mine erased her camera's memory card.
 The company e-mailed her the software, she installed it, and recovered all her pictures.

They have a vested interest in keeping their customers happy.
Because for some reason, folks tend to blame the manufacturer when they hit "delete" by mistake :)

---

### Post by vishal_b31 on 2009-09-28
> Re: SD Card, Data Recovery
btw - testdisk is in the repos - just: sudo apt-get install testdisk

i just installed test-disk using this command, but i can't find it anywhere on the applications menu. where exactly does it get installed? i even ran the command again just to make it had been installed, and apparently it is...just can't find it...

---

### Post by earthpigg on 2009-09-28
its a command line program, you wont find it in the menus.

> sudo photorec
sudo testdisk

---

### Post by seixcl on 2010-11-01
> **Neural oD said:**
> btw - testdisk is in the repos - just: sudo apt-get install testdisk
Thank you!! works great!!

---

