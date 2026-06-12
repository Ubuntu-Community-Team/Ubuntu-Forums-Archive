---
title: "Rip DVD to CD"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by DrWho8 on 2009-10-01
Yes I have searched Google. Yes I have searched the forum. So, I have not been able to find out how to Rip a DVD to a CD. I have K9Copy and that will rip a DVD to an .avi file, but at the same size. I would like to get the DVD to fit on a CD. I have tried Avidemux but that will change the video and audio separately and then mplex is supposed to put the together, but Avidemux makes the video choppy. Since I have not been able to get past the choppy video, I have not been able to check out how well the mix would synchronize the time.

I just think there must be an easier way to get the DVD down to a CD size.

Thank you in advance for any help.

The Doctor.

---

### Post by laidback on 2009-10-01
DeVeDe creates DVDs/CDs from files like avi. I've found that after Rendering (a function in Kino) the sound is OK again but I'm only messing with my own video files from a camera. Give DeVeDe a try it's in the repositories.

---

### Post by Ropetin on 2009-10-01
What format are you trying to get it into on the CD?  Or I guess the better question is, what device(s) are you trying to watch the copied movie on?

Assuming its a commercial DVD for which you have the rights to copy, and that you want to watch on your computer, it should be fairly easy.  The two packages I've used recently are dvd::rip and HandBrake.  Handbrake seems to be the one getting lots of positive feedback these days, so I'll recommend that one to you.  The documentation is great, and there are any number of how-to files for it on-line.  My preference is for using the XVid codec, but that's really up to your size vs quality preference.

Once you've ripped the DVD to an AVI file small enough to fit on a CD, just burn it to CD with Brasero or whatever.

---

### Post by Hallvor on 2009-10-01
> **DrWho8 said:**
> Yes I have searched Google. Yes I have searched the forum. So, I have not been able to find out how to Rip a DVD to a CD. I have K9Copy and that will rip a DVD to an .avi file, but at the same size. I would like to get the DVD to fit on a CD. I have tried Avidemux but that will change the video and audio separately and then mplex is supposed to put the together, but Avidemux makes the video choppy. Since I have not been able to get past the choppy video, I have not been able to check out how well the mix would synchronize the time.

I just think there must be an easier way to get the DVD down to a CD size.

Thank you in advance for any help.

The Doctor.

You can adjust the output file size for an avi in K9copy. At least the feature was there last time I checked.

---

### Post by halitech on 2009-10-01
something to keep in mind, a dvd will either be up to 4.4 gig or 8.5 gig in size and you want to drop that to fit on a 700meg cd. Thats up to a 12x reduction in size. I don't know if it will work but K9copy does have a copy function that I've used to "compress" an 8.5gig dvd down to a 4.4gig dvd and the quality was fine. Not sure how well it would work to get down to 700meg cd.

---

### Post by cjv8888 on 2009-10-01
Use AcidRip. You can specify the size of the resultant file and rip subtitle along with the avi file.

---

### Post by MrWES on 2009-10-01
> **DrWho8 said:**
> Yes I have searched Google. Yes I have searched the forum. So, I have not been able to find out how to Rip a DVD to a CD. I have K9Copy and that will rip a DVD to an .avi file, but at the same size. I would like to get the DVD to fit on a CD. I have tried Avidemux but that will change the video and audio separately and then mplex is supposed to put the together, but Avidemux makes the video choppy. Since I have not been able to get past the choppy video, I have not been able to check out how well the mix would synchronize the time.

I just think there must be an easier way to get the DVD down to a CD size.

Thank you in advance for any help.

The Doctor.

Get Handbrake, it has presets for ripping a DVD to a 700mb avi to fit on a CD.

[http://handbrake.fr/]("http://handbrake.fr/")

Bill

---

### Post by 3rdalbum on 2009-10-01
K9Copy definitely has settings for changing the file size down to 700mb. Settings > Configure k9copy...

Click the MPEG-4 tab on the left, click the File Size radio button and it's already preset at 700mb.

---

### Post by mister_p_1998 on 2009-10-01
If you want to put video onto a VCD you ought to look for software to create a VCD. 80minutes of video on a CD disk. Try this:
[http://ubuntuforums.org/showthread.php?t=120895](http://ubuntuforums.org/showthread.php?t=120895)
Steve

---

### Post by admiralspark on 2009-10-01
I'm curious, *why* are you trying to put a dvd on a cd? The quality of such a reduction would be absolutely horrible on anything larger than a 3" monitor... why not just buy a pack of blank DVD's at Walmart?

But if you want to go through with this, make sure that the sound is still high enough quality for playback, otherwise you may find it's become garbled, possibly filled with static. Been there done that with .avi files ;-)

---

### Post by MrWES on 2009-10-01
> **admiralspark said:**
> I'm curious, *why* are you trying to put a dvd on a cd? The quality of such a reduction would be absolutely horrible on anything larger than a 3" monitor... why not just buy a pack of blank DVD's at Walmart?

But if you want to go through with this, make sure that the sound is still high enough quality for playback, otherwise you may find it's become garbled, possibly filled with static. Been there done that with .avi files ;-)


I disagree with that; I can reproduce better quality avi files than taking a DVD9 to DVD5. Especially using mp3 audio and cropping.

~Bill

---

