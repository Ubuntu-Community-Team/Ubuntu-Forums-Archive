---
title: "Few questions"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Autospy on 2010-11-27
Hello everyone;

My friend gave me the Ububtu 10.04 LTS CD. But I am a bit confused I have few questions :

1) Now I am using WIndows 7 can i still using it while I install ubuntu on the other partition that have 25GB only? 

2) I used the Live edition (without installing ubuntu) to test it and it's pretty cool but when I use firefox to enter arabic website like [http://www.f1arab.com](http://www.f1arab.com) the writing in arabic is pretty weird and the font is not like windows 7 how to fix that?

3) WIll my videos .avi and .mp4 work on ubuntu? and can i write in arabic? like there's a program like Microsoft word?

Thank you !

---

### Post by AngelDE98 on 2010-11-27
1 ) It will not create partitions but a file with Ubuntu in it . 

2 ) Just downlaod the Fonts , Language Files and such ... 

3 ) Again , just do it and Drivers / Codecs will be automaticly searched . I just launched a MP3 and some AVIs worked too ;)

---

### Post by Autospy on 2010-11-27
> **AngelDE98 said:**
> 1 ) It will not create partitions but a file with Ubuntu in it . 

2 ) Just downlaod the Fonts , Language Files and such ... 

3 ) Again , just do it and Drivers / Codecs will be automaticly searched . I just launched a MP3 and some AVIs worked too ;)

Thanks! but please can you include more details? your answers are helpful but i am pretty confused how to do it and where to do it.

Thanks again !

---

### Post by matt_symes on 2010-11-27
[LEFT]Hi

> **Autospy said:**
> Hello everyone;
[/LEFT]
> **Autospy said:**
> 
 
My friend gave me the Ububtu 10.04 LTS CD. But I am a bit confused I have few questions :

1) Now I am using WIndows 7 can i still using it while I install ubuntu on the other partition that have 25GB only? 

2) I used the Live edition (without installing ubuntu) to test it and it's pretty cool but when I use firefox to enter arabic website like [http://www.f1arab.com](http://www.f1arab.com) the writing in arabic is pretty weird and the font is not like windows 7 how to fix that?

3) WIll my videos .avi and .mp4 work on ubuntu? and can i write in arabic? like there's a program like Microsoft word?

Thank you !

!. Yes
2. Ubuntu is not windows so it will not have the exact same fonts. Saying that you can get others.
3. At a terminal type (case sensitive)

sudo apt-get install ubuntu-restricted-extras

and enter your password (you willl not see  your password echoed to the screen. This is normal) to get codecs

4. Try open office.

 > and can i write in arabic?

I believe so, but others can correct me here if i am wrong

Kind regards

---

### Post by sikander3786 on 2010-11-27
Welcome to Ubuntu and Welcome to the forums :-)

Yes 25 GB space is more than sufficient for Ubuntu.

There are 2 different methods of installing Ubuntu in dual boot to Windows. First is Wubi install which just needs that you run a .exe file inside Windows and it guides you through the installation. It would appear under Programs just like any other Application and you can un-install it from there. But it has a few drawbacks. It is a bit slower, less stable as updates often break it.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The second is to install Ubuntu in proper dual boot to Windows just as you would dual boot 2 Windows install (XP and 7 for instance). It would install Grub (the Ubuntu bootloader) and the menu is presented when you boot your computer to let you choose Windows or Ubuntu.

If you need a long term/production solution, I would recommend a proper dual boot i.e, second method.

You can go through this page. It would give you a basic idea of everything and then we'll be able to answer your queries more efficiently.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I use the Urdu fonts in Ubuntu (Urdu is based on Arabic basically) and never had any problems. So Arabic might just work well.

And Openoffice is included by default in Ubuntu and it would let you type Arabic once you install the language/fonts.

Yes you can play .mp4, avi and anyother media files.

---

