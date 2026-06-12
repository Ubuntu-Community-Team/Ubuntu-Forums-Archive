---
title: "Firmware-b43-Installer is behaving erratically, issues installing Java"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by WestonTurner on 2011-03-25
These kinds of problems have been posted here before, but I assure you I've searched through and I think mine is unique. Read on:

So to start, I'm entirely new to Ubuntu and to Linux in general. I'm running meerkat, which I installed off a thumb drive and run on my Dell Inspiron 1525. I activated the Broadcom STA wireless driver since I heard it's better than the Broadcom B43. I'm trying to install the JAva Runtime Environment (so I can play Minecraft, of course), but when I put in

sudo apt-get install sun-java6 sun-java6-jre

It returns the error message

dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

For reference, I'm trying these instructions: [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-10-10-maverick-using-ppa.html)

And naturally, the Java JRE doesn't work because of the error. No surprises there.

The strange thing about this is that I've been getting that error message every time I try to install anything, except in most other cases whatever I've installed works just fine. For example, I tried installing Conkeror just to see if it would work, and it returned the same error message, yet Conkeror works just fine! This happens time and time again, but for some reason Java won't install. Can anyone shed some insight on this problem? I apologize if it's embarrassingly simple; like I said I'm new at this. Any help at all would be greatly appreciated. In fact if my problem gets resolved I'll draw a picture of the American flag on the moon in OpenOffice Drawing and share it  with you guys as a token of my gratitude (no kidding).

---

