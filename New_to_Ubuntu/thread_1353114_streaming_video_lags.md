---
title: "streaming video lags"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by ibbill on 2009-12-12
Is there any way to cut down on the resources Karmic uses to stop this from happening.

When I use windows 7 I have no problem with the lag.

Intel(R) Pentium(R) 4 CPU 3.00GHz

2.0 GB Ram

Linux 2.6.31-16-generic

adobe-flashplugin
Adobe Flash Player plugin version  10.0.42.34

Thanks Bill

---

### Post by s3MA00RRNY on 2009-12-12
Some say that there is a placebo effect with SwiftFox, but I noticed a great improvement with Flash video. Try it out and see if it works. Be sure to get the right version.

---

### Post by TBABill on 2009-12-12
Bill, I do not know if you have an Intel video chipset, but I do on two laptops I have Ubuntu installed on. I had glitchy video, stopping every few seconds to buffer, and it never seemed to play back smoothly even after buffering. I would go to YouTube or click links to videos in news sites, but none played smoothly or continuously without buffering throughout the video.

I realized my wallpaper on the desktop did not look great, pictures weren't great and everything was just 'blah'. Last night I went into admin and chose the option to use the proprietary Intel video driver (183?). Once I installed that driver my system took on a whole new personality. Fonts and images were extremely sharp, the 3D effects began to work, my wallpaper image came to life with shadowing and other 3D effects, and my video playback was immediately improved to load without buffering (initial buffering only, but not throughout the video). Games that required 3D also sped up (even the Tetris like game with Ubuntu that should take few resources to play). 

I was bewildered why some things were so fast while others crept along, especially to find out it was as simple as a better video driver from Intel than built into Ubuntu. 

Good luck.

---

### Post by ibbill on 2009-12-12
pcdude thanks for the help will give it a try. Is it just that my computer is old or does Karmic seem to use a lot more resources than the last few ubuntu os.
Thanks again Bill

---

### Post by ibbill on 2009-12-12
> **TBABill said:**
> Bill, I do not know if you have an Intel video chipset, but I do on two laptops I have Ubuntu installed on. I had glitchy video, stopping every few seconds to buffer, and it never seemed to play back smoothly even after buffering. I would go to YouTube or click links to videos in news sites, but none played smoothly or continuously without buffering throughout the video.

I realized my wallpaper on the desktop did not look great, pictures weren't great and everything was just 'blah'. Last night I went into admin and chose the option to use the proprietary Intel video driver (183?). Once I installed that driver my system took on a whole new personality. Fonts and images were extremely sharp, the 3D effects began to work, my wallpaper image came to life with shadowing and other 3D effects, and my video playback was immediately improved to load without buffering (initial buffering only, but not throughout the video). Games that required 3D also sped up (even the Tetris like game with Ubuntu that should take few resources to play). 

I was bewildered why some things were so fast while others crept along, especially to find out it was as simple as a better video driver from Intel than built into Ubuntu. 

Good luck.

TBABill should have posted that also (oops)  | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)



I was quite surprised as I scrolled throught the apts looking for 183 to see ATI and Nvidia drivers installed also.never found the 183. Thanks for your help. 

Bill

---

### Post by TBABill on 2009-12-12
Sorry, I should have stated I have an Intel GeForce 7000M / nForce 610M graphics processer and I updated to the NVIDIA Driver Version 185.18.36 (thought it was 183, but is a 185).

Hope you found your solution.

---

### Post by ibbill on 2009-12-12
TBABill no luck but sure appreciate your help. Looks like at the moment will(yuk) use windows7 for the streaming video.

Note have tried the chrome and firefox to no avail again thanks for your help.

Going to wait for the new year and treat myself;) to a new computer. The best my bank account will allow. Wait if I don't spend it all on myself the kids will get. Hmmmm maybe charge it and stick the kids lol.

Bill

---

