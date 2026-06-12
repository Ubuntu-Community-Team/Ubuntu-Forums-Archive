---
title: "MSI WIND WebCam to work"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-11
i've installed Ubuntu 8.10 on my MSI Wind U100 and i'm wondering if anyone can direct on how to or where to get additional information on how to make my WebCam working and use it...

thanks for any help in advance

---

### Post by hashimoto on 2009-01-11
How about these two links:
[http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron)
[http://ambospeak.blogspot.com/2008/12/getting-msi-wind-webcam-to-work-under.html](http://ambospeak.blogspot.com/2008/12/getting-msi-wind-webcam-to-work-under.html)

---

### Post by manuleka on 2009-01-11
thanks - wiki page has installation guide for 8.10 that worked for me - cheers :)

---

### Post by vajohn1308 on 2009-03-27
noob here so please bear with me...

The Bison (acer) webcam is the one that i have in my Wind U100. I found that out by doing the lsusb command from a terminal window.  I am having a bit of a problem with one step in the configuration that's in the wiki file.

I downloaded the file from LinuxTV.org to my desktop. The one i downloaded was 
uvcvideo-56cf0f1772f7.tar.gz

I did the first step and got the install subversion build part installed  fine.

but the second step...
$ tar -xvzf <source.tar.gz file downloaded from LinuxTV.org>
I am at a loss as to EXACTLY what to enter to get the file to decompress/extract it. I have tried a few combinations and none worked. Once i get past this step i should be fine.

If anyone can post **exactly** what to type to get that to work i would really really appreciate it. After that, the make and make install are self explanatory. 

 Thanks for any that take the time to help a pretty much total noob.

vajohn1308

---

### Post by vajohn1308 on 2009-03-27
OK i tried  something and got it to work
 Instead of doing the -xvzf i simply right clicked the file and then selected extract here and it took a WHILE to extract but it finally did.  Then i followed the rest of the steps in the wiki and it works in cheese.

However, the quality of the webcam  is the same as in windows. Still pics are fine. Video on it blurs/drags.

FYI i added a one GB DIMM so i have 2GB in my Wind U100 now so it's not a lack of memory problem. My guess its that MSI changed the original webcam to a cheaper one( same thing that they did with the  touchpad, which was originally a synaptic one.)  I might try a Logitech Notebook Pro webcam later on to see if that works any better.  But for now at LEAST i got  the built in webcam working.

vajohn1308

---

### Post by tofiluk on 2009-04-27
hi there. how will i know from lsusb what webcam is installed in my msi wind?

---

