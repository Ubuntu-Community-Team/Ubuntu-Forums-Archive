---
title: "!@#$ Cromium won't start"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-09-13
Okay, so, I am using a fresh install of 10.04.1, I did the normal updates, and installed the NVIDIA driver. I have not installed anything other then Chromium and the extras for it from Synap. The !@#$ still won't start. When I type it into the terminal it tells me Segmentation fault. This is not the first time this has happened, and it is probably the fouth or fith time I have done a fresh install this week and got the same result. 
Does anyone have a real answer to this please. Anyone else who is having this issue, please feel free to post saying so and anything you may have done to fix it. 
Thanks

---

### Post by jtarin on 2010-09-13
Where did you get chromium from?Nevermind...I see....uninstall and try [64 bit .deb (For Debian/Ubuntu)]("http://www.google.com/chrome?platform=linux&hl=en-IN")

---

### Post by AndyP79 on 2010-09-13
> **jtarin said:**
> Where did you get chromium from?Nevermind...I see....uninstall and try [64 bit .deb (For Debian/Ubuntu)]("http://www.google.com/chrome?platform=linux&hl=en-IN")

Yea, that is Chrome though. I really wanted Chromium cause it respects the window button layout of being on the left hand side.

---

### Post by jtarin on 2010-09-13
> **AndyP79 said:**
> Yea, that is Chrome though. I really wanted Chromium cause it respects the window button layout of being on the left hand side.
According to your specs you need 64 bit....and the one in Syanptic is 32 if I'm not mistaken

---

### Post by jtarin on 2010-09-13
I'm not on my Ubuntu machine now but isn't there a setting uner Tools>Options(to use GTK or WM settings?)

---

### Post by AndyP79 on 2010-09-13
> **jtarin said:**
> According to your specs you need 64 bit....and the one in Syanptic is 32 if I'm not mistaken

Ahhh.... I think I see now. So there is no 64bit Chromium I am guessing? Okay, I will try that then see what happens.

---

### Post by jtarin on 2010-09-13
You can compile one if you need one, but I wouldn't advise unless you have some experience doing so.

---

### Post by AndyP79 on 2010-09-16
Hey everyone, just thought I would pass on this bit of advice.... I found a blog, don't remember where, that said there was a bug in the new UbuntuBeta fonts that causedd Chromium to seg fault. Have not had a moment to try it but it sound slike this is what is causeing Chromium and Chrome to not start. I am going to mark this as solved. I guess if we want Chromium and cool font, it is just going to have to wait for a while
Cheers

---

### Post by jtarin on 2010-09-16
[Did he also reccommend installing msttcorefonts package?]("http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/")

The UbuntuBetaFont is exactly what it is....Beta...it has to be downloaded seperately and deliberately. It is not in the repositiories for 10.04> the package name is ubuntu-private-nda-fonts. This font is likely to be released as default font on Ubuntu 10.10 Maverick Meerkat around October this year.I doubt this is your problem. If you have them remove them and install the msttcorefonts package.

---

### Post by Kixtosh on 2010-09-16
Well, I don't know what's going on exactly, but:

- I have a CQ60 as well (great budget laptop!).
- I used the Ubuntu 10.04 Live CD to load Ubuntu.
- I used the Ubuntu Software Center to install Chromium.
- I did not install any "extras".

And ... it's working perfectly. It describes itself as version 6.0.472.43 (57914). Surely this means that the solution can't be that hard to identify? Let me know if I can be of any help troubleshooting this for you. I'll leave the Live CD in use on that machine for a little while in case you post back.

---

### Post by jtarin on 2010-09-17
Can you give a link to the download location for this newer version?

EDIT:Nevermind found the ppa and downloaded version 7.X.....segfault.
Removed and replacing with version 6.X......will see how this one performs. I was having no problems with previous version of 5.X

---

### Post by GaryTheCat on 2010-09-17
Chromium stopped working for me too - I put it down to something being awry with the ppa I had it updating from - back to firefox for me for a short while until I sort it. (I haven't really got the time to do loads of fiddling to make it work).

G

---

### Post by jtarin on 2010-09-17
OK I have got ver-6.0.472.53 (57914) working now from the repositories. I uninstalled Chromium completely from Synaptic and updated the repositories and the newest stable showed, then I downloaded and installed it.

---

