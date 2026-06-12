---
title: "Yet another Dell 720 printer installation problem"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2010-07-14
About a year ago I installed my Dell 720 printer using the Lexmark driver z600 on my netbook.  I know that Ubuntu does not play well with Lexmark but the drivers installed and I had a printer.  Now, I installed Lucid on the netbook and tried to duplicate my feat and behold I got a nasty error message.  Does any one know what it means?  What do I do now?

---

### Post by cariboo on 2010-07-15
Have you got libstdc++5 installed, and if so what version?

---

### Post by Rex Bouwense on 2010-07-15
> **cariboo907 said:**
> Have you got libstdc++5 installed, and if so what version?
I may have been using Ubuntu for a while but I am still a noob at heart.  I have no idea if I have libstdc++5 installed and if I do what version.  How do I find out?
After I posted that stupid answer I realized that I know how to find out and the answer is no I do not have libstdc++5 installed.  I have libstdc++6 installed, version 4.4.3-4ubuntu5. Does that mean I am screwed?

---

### Post by LowSky on 2010-07-15
No your not screwed. You can probably have both installed side by side, all you need is the file, and its easy to get from here:

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

if you need additional pacakages search for them on here... I found your required file in the Jaunty repos

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Rex Bouwense on 2010-07-15
From reading your response, I would assume that I must download and install the required program.  It would make sense that it would be in the Jaunty repositories because I was using Jaunty before I installed old Lucid here and it worked fine then.  Is this a program that will install side by side?  Many will not if you have a newer one installed.  I guess I will find out.

---

### Post by LowSky on 2010-07-15
Yes you need to download and install the program. Because they are named different verisons they should in most cases install side by side.

---

### Post by Rex Bouwense on 2010-07-15
OK, I successfully installed libstdc++5.  I then installed z600llpddk_2.0-2_i386.deb (successfully) but when I tried to install the driver (z600cups_1.0-2_i386.deb), I got an error message Error: Failed to satisfy all dependencies (broken cache).  So I downloaded the driver again but got the same error message.  I do not remember it being this difficult when I installed it before.  Frustrating.  Now what?

---

### Post by Rex Bouwense on 2010-07-18
Update on this beast.  After I installed libstdc++5_3.3.6-17 and z600llpddk_2.0-2__i386.deb and z600cups_1.0-2_i386.deb,I kept on uninstalling the driver because the system told me to uninstall it  I searched in different forums and different sites and decided to not uninstall it the next time and CUPS let me choose the z600 Lexmark printer and I can print now.  Unfortunately, I now have a big red dot in my top panel with a white horizontal line running through it  It, in effect tells me that I cannot update until I uninstall a broken package and guess which package is broken (the printer driver for the Dell 720/Lexmark z600).  What next.  I really hate to get another printer since the printer cartridges for this one are relatively cheap and I do not print a great deal of documents in a year.  Does anyone have any suggestions?

---

