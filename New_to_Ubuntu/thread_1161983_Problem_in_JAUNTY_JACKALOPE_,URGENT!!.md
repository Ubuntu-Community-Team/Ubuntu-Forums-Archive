---
title: "Problem in JAUNTY JACKALOPE ,URGENT!!"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by kapmsd on 2009-05-17
After the progress screen is over,i am stuck .
I have attached the image,refer it
What else i can do to make my jaunty work apart form re-installing?

---

### Post by Didius Falco on 2009-05-17
Hi,

Had you done anything just prior to this happening? I'm thinking in particular about video card drivers - they often can cause this to happen.

What kind of video card do you have - give us some details on your system hardware.

Regards,

Didius

---

### Post by braete on 2009-05-17
did you do dpkg-reconfigure xserver-xorg ?

i got the same thing while toying with this command (it's because i chose to disable the framebuffer)
iwe fixed this (the corupted screen) by using dpkg-reconfigure again and leaving the framebuffer enabled.

i'm new at using ubuntu so i dont know if this will go for you, but it got the job done for me

---

### Post by Tholley on 2009-05-17
I have same problem, see (9.04 not booting anymore).

How can we try that fix if we can't boot all the way up?

---

### Post by braete on 2009-05-17
if i remember correctly i used ctrl + alt + f1
also check [http://ubuntuforums.org/showthread.php?t=65036](http://ubuntuforums.org/showthread.php?t=65036)

---

### Post by philinux on 2009-05-17
Reboot, at grub press esc. Choose the recovery option. From the recovery menu use xfix. Then resume normal boot.

---

### Post by MOOLA on 2009-05-17
wow!

---

### Post by kapmsd on 2009-05-17
I tried the xfix and normal boot option  but no use,still getting that stupid erratic screen .
Details of  video card:
ATI RADEON XPRESS 200 SERIES.

I updated 40MB of  those present under "UPDATE MANAGER" list.
After that ,its not working.
:oops:

---

### Post by bacardiandwatermelon on 2009-05-17
Have you had a look at this?

[http://ubuntuforums.org/showthread.php?t=1135585&highlight=ATI+RADEON+XPRESS+200&page=3](http://ubuntuforums.org/showthread.php?t=1135585&highlight=ATI+RADEON+XPRESS+200&page=3)

---

### Post by Game Over on 2009-05-17
Question: Are you attempting to dual boot? I had this EXACT same problem, and after I backed up my windows files and fully partitioned Ubuntu rather than dual booting, it stopped.

---

