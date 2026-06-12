---
title: "NVIDIA-Linux-x86_64-180.44-pkg2.run  No  Can DO"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-18
How do I install this nvidia  driver?
I have downloaded it, but it needs me to quit the GUI. I don´t know how to make it run, once I have navigated to its folder, either.

Thank you!

OK, I see there are some beta nvidia drivers [here]("ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/"). The 185 series is meant to be very good.
I will try with those, but from the download page, there are actually 3, instead of one files. 
Which one do I choose? And then what do I do? 
(I am using Ubuntu Jaunty 64 Alternate)

---

### Post by Crandom on 2009-04-18
Open a terminal, cd to place where the file is, then run these commands:
```
chmod +x NVIDIA-Linux-x86_64-180.44-pkg2.run
sudo ./NVIDIA-Linux-x86_64-180.44-pkg2.run
```

The first makes it executable, the second one runs it.

---

### Post by yeehi on 2009-04-18
Thank you! 
What do I type when using the following files?

NVIDIA-Linux-x86_64-185.19-pkg0.run
NVIDIA-Linux-x86_64-185.19-pkg1.run
NVIDIA-Linux-x86_64-185.19-pkg2.run

Do I need to run them all?

---

### Post by Crandom on 2009-04-18
For 64 bit: [ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/NVIDIA-Linux-x86_64-185.19-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/NVIDIA-Linux-x86_64-185.19-pkg2.run)

Tutorial for beta drivers: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)


PS, for my last answer, you have to type:
```
sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run
```
instead of "sudo ./NVIDIA-Linux-x86_64-180.44-pkg2.run"

---

### Post by yeehi on 2009-04-18
Thank you, Crandom! You should be given a medal :)8)

---

### Post by Crandom on 2009-04-18
You're welcome.

---

