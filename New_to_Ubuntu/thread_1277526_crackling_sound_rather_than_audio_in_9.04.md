---
title: "crackling sound rather than audio in 9.04"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by jake958 on 2009-09-28
Hello all!

I am a newbie to Linux/Ubuntu with limited technical knowledge.  

I recently upgraded to 9.04 and have been experiencing sound problems ever since. Instead of audio I get a ¨crackling¨ sound through the speakers. My laptop is an Acer Aspire 9525 WHSI. The audio worked fine on the previous Ubuntu install.

Any help would be greatly appreciated. 

Thanks in advance.

Jake.

---

### Post by hyperdude111 on 2009-09-28
During the alpha and beta stage of 9.04 i had a similar problem but since the final release sound has been fine for me.

What worked for me on the alphas was to fiddle with the PCM setting on sound settings and to kill the pulseaudio process.

---

### Post by wobin77 on 2009-09-28
Did you try to install the ALSA mixer?

sudo apt-get install gnome-alsamixer

---

### Post by jake958 on 2009-09-28
Thanks for the speedy response chaps.




I tried the alsa mixer update and got this:

gerard@gerard-laptop:~$ sudo apt-get install gnome-alsamixer
[sudo] password for gerard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gerard@gerard-laptop:~$ 


And having adjusted all the sound settings and killed pulseaudio still no luck or change.

---

### Post by jake958 on 2009-09-30
Hello,

just wondering if anyone has any other ideas to solve this problem?

Thanks.

---

