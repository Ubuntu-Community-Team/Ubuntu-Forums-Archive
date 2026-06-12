---
title: "Webcam not working"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by jhazard112 on 2011-04-03
Hi all,

Currently I have Ubuntu 10.04 64 bit loaded on my machine, and I am having issues with my webcam.  I am not sure on how to find it, or get it to start working with skype.  If anyone could tell me the commands to find out what it is and then how to load a "driver" for it, it would be greatly appreciated.  My computer is an Acer Aspire 7741z-4433.  Thank you in advance.

Hazard

---

### Post by nickleboyblue on 2011-04-03
The most important bit of info:  which webcam are you using?  Some of them don't have the greatest support under Linux.

If your camera is supported, it should simply work when you plug it in.

Another question: does the camera connect to your computer via usb?  If so, have you had problems with other usb devices in the past?

---

### Post by jhazard112 on 2011-04-03
Firstly, let me answer the question I know the answer to, no this is not a USB camera, it is a built in.  Secondly, I am not sure how to find out what type of camera I have.  If there is a command that I can run that will let me know what hardware I have and then I can go from there, please let me know.  I appreciate the assistance.

---

### Post by Paqman on 2011-04-03
What happens when you hit the "test" button in the video settings of Skype? Anything?

---

### Post by earthpigg on 2011-04-03
hi,

1) you could give imo.im a shot. [https://imo.im/](https://imo.im/) - it uses flash, instead of skype's software, to access your webcam. worth a shot - i've heard of people that could not get skype+webcam to work on linux, but could get chatroulette (flash+webcam) to work.

2) see if webcamstudio and/or cheese webcam booth (both in the repos) can work with your webcam. if they can, then could mean your webcam is supported by linux but not by the linux version of skype.

---

### Post by jhazard112 on 2011-04-03
So I tried Cheese and it works perfectly, and when I hit test in Skype 2.1 Beta, it is just black.  Is there another software that is compatible with both Windows and Linux that I could try out for video conferencing?  My ex who has my kids wont be able to work in linux at all.  You guys have been such a help and I appreciate it so much.

---

### Post by dcsoldschool53 on 2011-04-03
Built in web cam. What computer do you have. name and model of your computer, pls. Sorry I jst read that you have an Aspire

---

### Post by jhazard112 on 2011-04-03
It is an Acer Aspire 7741z-4433 at least that is what it says on the bottom.:D

---

### Post by jhazard112 on 2011-04-03
I'm sorry clarification Make is Acer Model is Aspire and Model number is 7741z-4433

---

### Post by earthpigg on 2011-04-03
> **jhazard112 said:**
> Is there another software that is compatible with both Windows and Linux that I could try out for video conferencing?  My ex who has my kids wont be able to work in linux at all.  You guys have been such a help and I appreciate it so much.

have you tried imo.im? it runs a skype client inside your web browser. see my above post for why this may work.

there have also been folks that got skype webcam to work by starting cheese and *then* starting skype *with cheese still open*.

because skype is closed source, no one really knows why skype is wonky and no one can fix it.

then again, there is also the option of migrating to 32-bit ubuntu and giving it a shot there. run a 32-bit livecd or liveusb, and see if the webcam works there.

---

### Post by dcsoldschool53 on 2011-04-03
[B]This site may help you.

[/B][https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by madjr on 2011-04-03
> **jhazard112 said:**
> So I tried Cheese and it works perfectly, and when I hit test in Skype 2.1 Beta, it is just black.  Is there another software that is compatible with both Windows and Linux that I could try out for video conferencing?  My ex who has my kids wont be able to work in linux at all.  You guys have been such a help and I appreciate it so much.

actually you can still use skype with a workaround (is not about forcing skype or anything technical but worth a try):

1- start cheese cam booth
2- share your desktop with skype.

she or you will now see your desktop + the video in cheese.

yea the lazy skype people should work on these bugs, since the cam works perfectly.

anyway this workaround is only if you still want to use skype, am sure some people will suggest other messaging clients that really detect your hardware.

---

### Post by madjr on 2011-04-03
> **earthpigg said:**
> have you tried imo.im? it runs a skype client inside your web browser. see my above post for why this may work.

there have also been folks that got skype webcam to work by starting cheese and *then* starting skype *with cheese still open*.

because skype is closed source, no one really knows why skype is wonky and no one can fix it.

then again, there is also the option of migrating to 32-bit ubuntu and giving it a shot there. run a 32-bit livecd or liveusb, and see if the webcam works there.

sounds interesting

---

