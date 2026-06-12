---
title: "Audio not working after fresh installation of 11.0.4"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by saurabhshah on 2011-07-03
Hi All,

This is my first interaction with Ubuntu and I've installed ver 11.0.4 with no errors.
After installation the laptops sound is not working, however in windows the sound is fine.
Can someone please help me resolve this issue? Thanks.

Regards,
Saurabh

---

### Post by Muskegman on 2011-07-03
Hi welcome to the ubuntu forums.

The first thing you should try is to open terminal and type in 'alsamixer' without the quotations. Using your arrow keys on your keyboard make sure all the volume levels are turned up. then exit the terminal and try your sound. If that fails post again and we will see what we can do.

---

### Post by saurabhshah on 2011-07-06
done that but still no luck...!

---

### Post by Muskegman on 2011-07-07
Take a look at this it may help              



[http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966)

---

### Post by candtalan on 2011-07-07
I have often found that at install the sound is often set as muted, so double check that it is not muted.

---

### Post by saurabhshah on 2011-07-07
Thanks Muskegman...your post helped me solve the problem..
all I had to do was the following
1.) sudo gedit /etc/modprobe.d/alsa-base.conf
2.) add this line..options snd-hda-intel model=hp (since my laptop make is hp and the on board sound card is ALC260)

Thanks again for making my day..!!
Saurabh

---

### Post by Muskegman on 2011-07-08
Hi, glad to hear you solved it, please mark this thread as solved :p

---

### Post by saurabhshah on 2011-07-08
How can I do that??

---

### Post by candtalan on 2011-07-09
> **saurabhshah said:**
> How can I do that??
To mark your own thread as 'solved' 
go to Thread Tools at the start of the thread, and choose the 'solved' option.

---

