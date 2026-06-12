---
title: "Need advise in regards of DVD file that is saved on my hdd"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-12-12
Hi guys,

First of all Merry Xmas and how you all have great plans in the coming holidays.

I backup some DVD's in my hard drive and now i wanna convert them on a .mpeg or avi format so i can put lots of movies on a single cd.

Problem i have installed acidrip winff and dvd::rip and none can convert them to mpeg or avi direct from HDD i can id i put the DVD in.

When i was using windows. i was using a program called windvd which can do all what i mention above. is there any program that is same or similar to windvd? or could you suggest a program that can do what i am trying to achieve?

---

### Post by zaphod777 on 2009-12-12
Try Handbrake you can convert the VIDEO_TS folder after you mount the ISO. Right now I am using "Furius ISO Mount" to mount my ISO files. You need to download latest handbrake from their site and ISO mounter should be in the repos.

---

### Post by Gazneth on 2009-12-12
I am assuming you mean you want several movies on a dvd, and plan to play them with a set top dvd player. Try devede I think it will do what you describe. I have only used it for single movies myself though.

---

### Post by zaphod777 on 2009-12-12
> **Gazneth said:**
> I am assuming you mean you want several movies on a dvd, and plan to play them with a set top dvd player. Try devede I think it will do what you describe. I have only used it for single movies myself though.

Right but the problem he is having is he wants to RIP the ISO file from his HDD to MPG or AVI and then burn a multiple movie DVD.

He is stuck on the first part. He doesn't want to waste a DVD to burn it then re-rip it.

---

### Post by Gazneth on 2009-12-12
Well, for that I agree Handbrake is a favorite of mine also.

---

### Post by vlad1975 on 2009-12-13
Thanks for the tips.
Is handbreak available in repository or should i go to a website to download it?

---

### Post by zaphod777 on 2009-12-13
I would download the latest from the web as I believe the one in the repos has a problem in 9.10.

---

### Post by emiliec15 on 2009-12-14
I don't know if any of the other options are what you want or not but what I usually do is mount the iso of the dvd in a virtual drive and then use vlc or mencoder (both in the repos though you might need to enable medibuntu to get full functionality) and use them to rip the movies.

---

### Post by pulpinator on 2009-12-14
I agree to use handbrake to rip the image into a smaller video file. One thing the OP mentioned was .avi. Handbrake is not going to do that. Really, that has become an obsolete container.

You should use .mkv. A big advantage of .mkv is that you can store h.264 (which will make your video much smaller), and multiple audio tracks and subtitle tracks that you can turn on/off just like a DVD.

Handbrake supports all of that.

---

