---
title: "Question about installing openchrome."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by racecar1144 on 2009-01-16
I have been unsuccessful with being able to achieve a successful boot and login on my computer with a S3 Unichrome 3D integrated graphics card. I have never been able to load the live cd, and had to install through the alternative downloader, but still cannot even reach the login screen before the screen freezes. 

I found the Openchrome page and package to download, but how would I get it to work for me so that I can reach the login screen and proceed to the desktop? I guess how would I install it without being able to go beyond the login screen?

---

### Post by overdrank on 2009-01-16
> **racecar1144 said:**
> I have been unsuccessful with being able to achieve a successful boot and login on my computer with a S3 Unichrome 3D integrated graphics card. I have never been able to load the live cd, and had to install through the alternative downloader, but still cannot even reach the login screen before the screen freezes. 

I found the Openchrome page and package to download, but how would I get it to work for me so that I can reach the login screen and proceed to the desktop? I guess how would I install it without being able to go beyond the login screen?

Hi and how much memory does the system have? How much is shared with the integrated S3 graphics?
You may try booting into recovery mode which is usually the second choice from the grub and then using the xfix option to correct the graphics. Then you should be given the choice to boot normally.

---

### Post by racecar1144 on 2009-01-16
I have 1 gb of ram and im not sure on the shared video card size. My guess would be 128 mb.

And Im sure I am booting it normally, and not in recovery mode, although I have to no avail. . .

---

### Post by racecar1144 on 2009-01-16
Sorry, miss read what you put down, will try that when I get back from class.

---

### Post by racecar1144 on 2009-01-16
well, and to be honest, I will try, but not know how. what is a more descriptive step by step to using the xfix option?

---

### Post by overdrank on 2009-01-16
> **racecar1144 said:**
> well, and to be honest, I will try, but not know how. what is a more descriptive step by step to using the xfix option?

The xfix option automatically configures your graphics. The steps are as I described previously. But I will elaborate a little more :)
try booting into recovery mode which is usually the second choice from the grub and then using the xfix option to correct the graphics. You will see four options and the last is the xfix option. After running xfix you should be given the choice to boot normally.

---

### Post by racecar1144 on 2009-01-16
Okay. Thanks for the vivid detail! :) I have a gut feeling that I have done this already by just trying to figure it out myself on late, late night. Will be back later with my results.

---

