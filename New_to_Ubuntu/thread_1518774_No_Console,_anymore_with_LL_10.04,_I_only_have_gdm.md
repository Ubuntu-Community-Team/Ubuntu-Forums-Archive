---
title: "No Console, anymore with LL 10.04, I only have gdm"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by xlr8.at on 2010-06-27
Hello Ubuntu-Friends, 

I just want to introduce myself, my name is Andre, I am from Germany, and I love my Ubuntu ;). Im doing Linux since quit a time now, but still i am not a pro ;). 

Well right now I am facing a problem I never had, I think the problem is so easy that i just cant think of the answer right now.

I had a hard time getting gdm, gnome xserver and newest nvidia-drivers to work with each other, and everything was fine. I had the newest drivers from NVidia downloaded etc. Then I wrote my xorg.conf, and had 1980x1020 at 24 - with all desktop-effekts working quite decent. It worked for over 6 weeks without any probs. 

Day before yesterday there were some automatic updates and I wanted to make them. 

At first i didnt notice a change after rebooting , but then I reallized that all effekts had been gone. I can´t switch resolutions anymore, I cant use for example glxgears in X anymore, I suddenly have the "jockey"-pakets reinstalled, and my system is like really crappy right now. 

Starting glxgears results in:
Error: glXCreateContext failed

BUT NOW THE WORSEST THING IS STILL TO COME. I cant switch to the ALT-F1 - F6 anymore, there is just a blank screen. When I stop GDM, I don`t see anything anymore, and I can`t return to gdm, because I dont know / see what I am typing. 

The Ubuntu Start-Logo is gone too. The only thing that still is ok is the resolution when gdm / gnome runs. 

I think the auto-update destroyed my X-configuration or tried to use an other drivers.
My suggestion is that there may be a problem with the resolution when I switch to ALT-F1. Is there a way to say that i could use 640x480 when switching from x to console.

I want my tty1 back ;) please ubuntu .... 

Can somebody give me a hint 

have a nice sunday folks... 

Greetings from Andre

---

### Post by Dr_Willis on 2010-06-27
I have noticed on several of my nvidia systems that (with the live cd, and an installed system) That  I can be at  the gdm screen, and alt-ctrl-f1 trough F6 do not go to the consoles either. They 'sort of' work but the screen basically freezes showing the now 'looks like its hung' gdm screen.

IF i hit alt-ctrl-f7 to get back to GDM - then gdm does indeed work.

Its as if the consoles are some how showing the GDM screen image, and never updateing.


A fix i found is simply to install the non-free nvidia drivers from the 'hardware drivers' tool , this disables the other  open sourced nvidia drivers which i think are the source of the issue.

Hopefully this will get improved in  10.10 as it stands now. I cant get to the consoles on my live cd, or a 'fresh' new install, without some work.

---

### Post by -humanaut- on 2010-06-27
I had a similar problem with nouveau killing X try blacking the nouveaufb & nouveau

---

### Post by Dr_Willis on 2010-06-27
Right - when you install the nvida drivers it does automatically blacklist that driver

in /etc/modprobe.d/nvidia-graphics-drivers.conf

it adds the 2 lines to blacklist the driver
blacklist nouveau
blacklist lbm-nouveau

So this points to a nouveau issue.

---

### Post by xlr8.at on 2010-06-27
hey guys thanks for the reply, good evening everybody else. 

I think I will give it a shot, reinstalling the nouveau, jockey etc. I hope I will get my normal ttys to work. then I will remove nouveau again, and reinstall my nvidia-195 pkg´s .... 


BTW: When I try to switch on the desktop effekts, the hardware driver installation wizard shows up ending up with no result... 


@Dr_Willis: I dont have a nvidia-blacklist at /modprobe ... should I have one ? 
I read in a todo/tutorial, that I should do blacklist the nouveau manually when having issues with a original nvidia driver, but there was no need for me to do it, because my system run flawless. nouveau and jockey removed completely from system. Running for weeks now... 

hmmm .... this is annoying. Took me quiet a while to get my Lynx walking, now he is lame again. This is crazy, having a x-server running with no chance to get to a console ... I remeber times when I only had console, and no X running ;)

I will give it a shot right now, and will post what happended later on

CU

---

### Post by -humanaut- on 2010-06-27
What kernel version are you using? Kernel 2.6.32-23 killed my X with nvidia. I had to fall back on 2.6.32-22

---

### Post by xlr8.at on 2010-06-27
Well looks like I solved it, but it wasn grub. I managed to get everything back working like a charm, Console + Bootscreen + X.
The Problem was gone when I was setting up Plymouth again, and I changed the resolution inside Grub + update Grub... thats it....

Next reboot everyting was ok again. Strange behavoir, I didn´t reallized I changed anything in grub, plymouth, etc. ... 

10.04 is quite difficult to get it working right. I had many issues .... well ... but here it is , back again.

Have a nice evening. 

Andre

---

### Post by -humanaut- on 2010-06-27
Try falling back to the 2.6.32-21 kernel

---

### Post by Dr_Willis on 2010-06-27
One of the many reasons i tend to disable plymouth totally, and black list  the framebuffer modules. :) The eyecandy is getting in the way of getting the work done.

At least you figured it out.  You may want to tag the thread as fixed now.

---

