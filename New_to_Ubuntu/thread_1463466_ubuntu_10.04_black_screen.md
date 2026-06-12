---
title: "ubuntu 10.04 black screen"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by jude13 on 2010-04-27
I have ubuntu since the 8.10 version, I'm not really good at programming, so I'm kind of a beginner. :KS

Recently, I had to reinstall my ubuntu 9.10. Right after I updtaded everything, I upgraded to 10.04. I did not install Nvidia drivers because I was told that 10.04 would support my card

During the upgrade to 10.04 the update manager got stuck at memtest86+ at the line : image found : /boot/vmlinuz-2.... So I pressed CTRL+C to make the upgrade go on

Now, when I boot my ubuntu, every thing seems to work fine, I see the purple screen with the orange dots :popcorn: When it comes to the login screen, I hear the sound, but I only see a black screen with some color spots at the top of my screen.:(

I tried to go in the ttys and they work fine. Every time I go back to the x server I see the last thing I saw on the ttys at the top instead of the coulour spots.

I would be really pleased if someone can help me

[PHP]Informations about my computer :

Model : Asus notebook K401N Series
OSs : Windows Vista + Ubuntu 10.04 RC
Graphic Card : NVIDIA Geforce g102m[/PHP]

---

### Post by miyagison on 2010-04-27
> **jude13 said:**
> I have ubuntu since the 8.10 version, I'm not really good at programming, so I'm kind of a beginner. :KS

Recently, I had to reinstall my ubuntu 9.10. Right after I updtaded everything, I upgraded to 10.04. I did not install Nvidia drivers because I was told that 10.04 would support my card

During the upgrade to 10.04 the update manager got stuck at memtest86+ at the line : image found : /boot/vmlinuz-2.... So I pressed CTRL+C to make the upgrade go on

Now, when I boot my ubuntu, every thing seems to work fine, I see the purple screen with the orange dots :popcorn: When it comes to the login screen, I hear the sound, but I only see a black screen with some color spots at the top of my screen.:(

I tried to go in the ttys and they work fine. Every time I go back to the x server I see the last thing I saw on the ttys at the top instead of the coulour spots.

I would be really pleased if someone can help me

[PHP]Informations about my computer :

Model : Asus notebook K401N Series
OSs : Windows Vista + Ubuntu 10.04 RC
Graphic Card : NVIDIA Geforce g102m[/PHP]

My recommendation is to grab the latest nvidia driver and boot up ubuntu in command line mode only and either install from a usb stick or hdd. .... or use wget if you know the exact path to download from and run as sudo .... sudo Filename. That should reconfigure your xwindow server to use the nvidia's driver; however, if you update the kernel you will have to go through this every time. Or .. once you get back into ubuntu use the Proprietary drivers as some laptops have issues with the built in drivers ... like mine. :)

---

### Post by jude13 on 2010-04-27
how do I cd to my usb drive in the ttys?

---

### Post by jude13 on 2010-04-29
It worked thank you!

---

### Post by aleixsr on 2010-04-29
> **jude13 said:**
> It worked thank you!

Can you explain how?

---

### Post by jude13 on 2010-05-04
> **aleixsr said:**
> Can you explain how?


I googled how to mount a usb key in the ttys... every tio you need is on the internet ;)

---

