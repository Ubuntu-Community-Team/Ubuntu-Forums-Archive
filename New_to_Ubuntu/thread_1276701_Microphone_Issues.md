---
title: "Microphone Issues"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Catraphact on 2009-09-27
Hi,
I've been using Ubuntu for the past few months now. Everything has been working perfectly. I installed it on an HP Pavilion DV7 laptop, and at first, had issues with the sound. I tried the following fix, and this worked perfectly.
[HP DV7 Sound fix for ubuntu. - Notebook Forums and Laptop Discussion]("http://forum.notebookreview.com/showthread.php?t=331172") 

I want to use Skype for Ubuntu. Everything works, including the integrated Webcam. Sound works too, I can hear someone on Skype. I've had no luck however in getting my onboard microphone to work.
 All I get is static. I'm honestly at the end of my wits with this one. Hopefully someone here can help. I'll post the outputs to any command that is requested- I looked at the Sound FAQ, but couldn't find anything helpful for my situation there. This is honestly my last resort. 

Thanks

---

### Post by Catraphact on 2009-10-01
Bump. I'm still struggling with this one.

---

### Post by mangurt on 2009-10-01
On board mic can be a pain.
In terminal
```
alsamixer
```
and check to make sure you have your input device on


I also had to use skype that was in the repository (instead of downloading it from skype).

Hope that helps you a bit

---

