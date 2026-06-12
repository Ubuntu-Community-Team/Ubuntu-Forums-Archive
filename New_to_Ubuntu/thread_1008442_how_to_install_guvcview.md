---
title: "how to install guvcview"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by edcouch on 2008-12-11
Hello, I want to install guvcview, so I downlaoded the file, and I extracted it in my home folder, then I tried to run sudo at-get install guvcview and it says it can't find the file.
Sorry for being such a dummy, but could someone please help me out here, I have a Logitech quic cam pro 9000 and it works with aMSN but no sound just video.  And I would like to install  guvcveiw to just use the cam to take videos and pictures.
Thanks in advance folks!

---

### Post by UbuWu on 2008-12-11
If you just want to take pictures and videos, it is probably easier to install [Cheese]("apt:cheese") and use that (click the link to install).

---

### Post by edcouch on 2008-12-11
Thanks for the reply, but, I did install cheese and it didn't work.

---

### Post by Michael.Godawski on 2008-12-11
Hi edcouch,
can you please give us the link from where you have downloaded the file, so we can see what sort of package this is and help you to install it.

---

### Post by albinootje on 2008-12-11
In this case either double-click on the deb package, or : sudo dpkg -i /home/your_username/Desktop/guvcview_0.9.6_i386.deb

And thanks for mentioning it, i knew cheese, but i didn't know this one.
Could be useful for testing a webcam on a laptop from a colleague.
[http://guvcview.berlios.de/downloads.html](http://guvcview.berlios.de/downloads.html)

---

### Post by albinootje on 2008-12-11
This could be useful : [http://blog.gnist.org/article.php?story=Linux_and_LogitechQuickCamPro9000](http://blog.gnist.org/article.php?story=Linux_and_LogitechQuickCamPro9000)
[http://scratchdrive.com/wordpress/?p=15](http://scratchdrive.com/wordpress/?p=15)

I also remember that sometimes with some users the settings in skype needed to be adjusted before sound worked.
Can you check the settings/options in amsn to see whether you have options to change to input and output of the sound ?

Which soundcard do you use by the way ?

cat /proc/asound/cards

---

### Post by edcouch on 2008-12-11
[http://packages.debian.org/source/sid/guvcview](http://packages.debian.org/source/sid/guvcview)

Thanks for the reply, this is where I downloaded guvcview from, but i just can't seem to get it installed.

---

### Post by edcouch on 2008-12-11
> **Michael.Godawski said:**
> Hi edcouch,
can you please give us the link from where you have downloaded the file, so we can see what sort of package this is and help you to install it.
[http://packages.debian.org/source/sid/guvcview](http://packages.debian.org/source/sid/guvcview)

Thanks for the reply, this is where I downloaded guvcview from, but i just can't seem to get it installed.

---

### Post by adult swim on 2008-12-11
ed, with the link you gave, you would have to build gucview from source, which could be a headache!  if you download it from here, once the file downloads you can double click it to install it.
[http://prdownload.berlios.de/guvcview/guvcview_0.9.6_i386.deb](http://prdownload.berlios.de/guvcview/guvcview_0.9.6_i386.deb)

---

### Post by albinootje on 2008-12-11
You downloaded the source code from Debian Sid.
It makes sense to download this one instead :
[http://prdownload.berlios.de/guvcview/guvcview_0.9.6_i386.deb](http://prdownload.berlios.de/guvcview/guvcview_0.9.6_i386.deb)

---

### Post by edcouch on 2008-12-11
Thanks for your reply, I finally did get guvcview installed, and the video works perfectly I just can't get any sound to work.  I am just using the onboard sound on my Asus M/B.

---

### Post by oluapSissa on 2008-12-17
Have you checked your alsa configuration? ;)
Maybe your mic is disable.

You can also use the camera built-in mic, it should list in
guvcview as a usb mic, has for the rest of the audio configuration
just leave it in default.

Best regards,
Paulo

---

