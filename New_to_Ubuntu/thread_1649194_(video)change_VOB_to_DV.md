---
title: "(video)change VOB to DV"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Mikaelo1 on 2010-12-19
How can I change my VOB videos to DV. to be able to work with them in Kinu. I am using cam corder with mini dvd's I know that maybe I can do it from other computer and save it into a USB drive but I will like to do it from my desktop with ubuntu studio. BTW this desktop has no connection to the internet. 
 
Thanks. Please help

---

### Post by Mikaelo1 on 2010-12-20
Am I posting in wrong forum?
this is my second thread with no answers, can someone please tell me what am I doing wrong?:)

---

### Post by BugBuster on 2010-12-20
I think ffmpeg can do it..
```
sudo apt-get install ffmpeg
```
then do
```
man ffmpeg
```
to find how to do it!!

PS : Just realized you don't have internet on this machine..so u have to get the packages from some other machine and install them manually on this one

---

### Post by FakeOutdoorsman on 2010-12-20
Once you figure out how to install FFmpeg on a machine with no internet connection you can try this command:
```
ffmpeg -i input.vob -target ntsc-dv output.dv
```
or if you are using PAL footage:
```
ffmpeg -i input.vob -target pal-dv output.dv
```

---

### Post by Mikaelo1 on 2010-12-21
thanks guys! 
 
At this moment I am trying to do both at the same time with no luck!
 
1-get files from my windows laptop.
 
2- trying to make ubuntu recognize my wireless USB
 
I got to convert the files to dv. but Kinu plays them in what I can only describe as a "fast-foward mode" it goes hyper fast and I can't get it to slow down. 
 
Now I have 3 problems and none seems to be near a fix. I am just trying to hang on now.

---

### Post by gordintoronto on 2010-12-21
WinFF is a graphical front-end for ffmpeg.

You can download, using Windows, from packages.ubuntu.com

You must make sure any "dependencies" are either already installed or downloaded at the same time.

Is there no way you can wire your computer to your router to download things, such as the wireless driver?

Questions which can be answered by spending two minutes with Google sometimes do not get answered in the forums...

---

### Post by Mikaelo1 on 2010-12-21
Thanks!
 
 How do I know which dependencies I have to install first?

---

### Post by Mikaelo1 on 2010-12-21
I tryed it it said all dependencies are satisfied and I went ahead and installed it. Now I am looking how to test it
 
 
Thanks

---

### Post by Mikaelo1 on 2010-12-21
> **FakeOutdoorsman said:**
> Once you figure out how to install FFmpeg on a machine with no internet connection you can try this command:
```
ffmpeg -i input.vob -target ntsc-dv output.dv
```
or if you are using PAL footage:
```
ffmpeg -i input.vob -target pal-dv output.dv
```
 
 
Guys! This is going to sound silly but I know that you open something that I think you call  " a terminal" and type commands in them right?  I am not sure where to open this "terminal" can you please tell me where?

---

### Post by gordintoronto on 2010-12-21
Accessories/Terminal brings you to a command line, kind of like MS-DOS.

One big advantage: you can cut and paste from a message, and you will get it right every time. If I say, "click here, select this tab, fill this check-box," you might not be able to find the things I'm telling you to click on.

---

### Post by Mikaelo1 on 2010-12-21
Thanks!
 
I'll could do that if I ever get my ubuntu studio to recognize my USB wireless that is turning out to be difficult to figure out for me right now.

---

### Post by Mikaelo1 on 2010-12-21
I just used the WinFF application and it worked. So basicly the Vob to Dv problem is solved. 
 
I encountered a problem of speed in Kinu but that's for another thread.
 
Thank you all very much for all the help
 
I hope you have a great Holiday !

---

