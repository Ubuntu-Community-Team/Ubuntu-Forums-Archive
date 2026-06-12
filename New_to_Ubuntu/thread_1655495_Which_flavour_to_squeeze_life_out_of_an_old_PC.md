---
title: "Which flavour to squeeze life out of an old PC"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by ElectricMonk73 on 2010-12-29
Hi Everybody!  Sorry about a question that y'all have probably seen many variations of...  But I'm new to Linux and need help choosing the best version for my computer.  I have installed Ubuntu 10.10 and have been using it for about a month now, I really like it, but my graphics card is an ATI Radeon x300, so i have been experiencing some performance issues - and as far as i can tell by reading other posts in the forum, there is nothing i can do to improve things with 10.10.  So would rolling back my version of Ubuntu to 8.x and installing the propriety ATI drivers be a good idea, or is it unsafe to use such an old version of Ubuntu? Or maybe there is a different type of Linux that would work better with my car? Or should i just keep with Ubuntu 10.10?  Cheers.

---

### Post by XeonBloomfield on 2010-12-29
Did you disable visual effects?

---

### Post by ElectricMonk73 on 2010-12-29
I'm sorry, i should have been a bit more specific. The bad performance is when I'm trying to play games, or use something like Blender or Inkscape. generally speaking other applications are fine. Visual effects don't seem to make an effect one way or the other.

---

### Post by XeonBloomfield on 2010-12-29
Can you tell us yours PC specs? Specially which processor you have.

Small 3D performance is probably normal for this graphic card. Sorry for that, but it is not a graphic card "monster".

---

### Post by davidmohammed on 2010-12-29
would be useful to know the specs of your PC - processor, RAM, diskspace etc.

---

### Post by ElectricMonk73 on 2010-12-29
Thanks for the replys,  My PC has an AMD Athlon 64 3200+ 2GHz processor : using 32bit linux, ATI Radeon X300 graphics card, 2GBs of RAM and a 500GB hard disk. Admittedly it isn't a great card, but i don't play graphic heavy games - Gish, Osmos, ect. Osmos actually runs really nice in windows, but i'm hoping to be able to wave goodbye to windows for good.

---

### Post by XeonBloomfield on 2010-12-29
Try to disable visual effects and check if speed of 3D apps is better.

System > Appearance > Visual Effects

Check first option "None".

If it will not help you can restore them by selecting previous value.

---

### Post by Hur Dur on 2010-12-29
You could try Fluxbox, LXDE, JWM, or IceWM if disabling visual effects does not help.

---

### Post by ElectricMonk73 on 2010-12-29
Thanks, I just tried disabling Visual Effects, but it made no difference. I might have to take a look at those distros.

---

### Post by Hur Dur on 2010-12-29
> **ElectricMonk73 said:**
> Thanks, I just tried disabling Visual Effects, but it made no difference. I might have to take a look at those window managers.

They aren't distros, just Window Managers, and LXDE is a desktop environment. You can get them by going into the terminal and typing:

sudo apt-get install fluxbox jwm lxde icewm

Then log out, go down to session, and choose whichever one you want to use, and log in.

As for distros, SliTaz, BasicLinux, and muLinux are about as light on the system as they get. For an in the middle distro, Wolvix and Absolute Linux are popular. Although, Absolute is based on Slackware, which may be off-putting. For Ubuntu-Based, I heard Fluxbuntu is light. But, you would probably be better off with just using Fluxbox on your Ubuntu install.

---

### Post by marl30 on 2010-12-29
> **ElectricMonk73 said:**
> Thanks for the replys,  My PC has an AMD Athlon 64 3200+ 2GHz processor : using 32bit linux, ATI Radeon X300 graphics card, 2GBs of RAM and a 500GB hard disk. Admittedly it isn't a great card, but i don't play graphic heavy games - Gish, Osmos, ect. Osmos actually runs really nice in windows, but i'm hoping to be able to wave goodbye to windows for good.

It has more to do with your video card, definitely. I have the exact same amount of ram; same processor, But I have an Nvidia 6200 (256mb). I'm using the 64bit Ubuntu 10.10. I can even do serious mult-tasking even while running XP in Virtualbox and my computer doesn't slow down. Sounds more like hardware 3D acceleration is not enabled for your graphics card.

---

### Post by trinitydan on 2010-12-29
> **Hur Dur said:**
> 
As for distros... ...For an in the middle distro, Wolvix and Absolute Linux are popular. 
The best "in the middle" distro I have seen so far is CrunchBang linux.  It installs in under 2GB and is very easy on system resources.  It is debian based so you would still be able to use familiar .deb packages.  It is not at all uncommon on decent hardware to have boot times under 20 seconds with CrunchBang and once running the performance is impressively snappy and responsive as well.

My ATI Radeon Xpress card has kinda taken a hit recently too.  It's unfortunate but it somehow performed better in Fiesty Fawn... :(  That's not too good.

---

### Post by frustratednerd on 2010-12-29
You might want to consider installing Xubuntu (Ubuntu with the Xfce desktop environment) or Lubuntu (Ubuntu with the LXDE desktop environment). Both desktop environments are designed to be easy and light on system resources, perfect for your aging machine.

---

### Post by ElectricMonk73 on 2010-12-30
> **Hur Dur said:**
>  sudo apt-get install fluxbox jwm lxde icewm

Then log out, go down to session, and choose whichever one you want to use, and log in.


Wow, i didn't realize it would be that simple to try different window managers. I thought i'd have to install a different type of Ubuntu to do something like that.

Thanks everyone for your help. I tried the other window managers and they do seem to help a bit - though i'm not sure i like lxde that much... Anywho, it seems that it is definitely my ATI Radeon card - even though hardware acceleration is on, it just isn't supported with the right drivers anymore.

'Tis a shame, but i'm willing to live with it for a bit, i mainly just do programming anyway.
 
Thanks again!

---

