---
title: "new nvidia drivers 180"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by nutpants on 2009-04-05
i just installed the new nvidia drivers on my dell xps m1210.
problem is the colors on my laptop display are all wrong now.
the screen looks like its almost in 256 colors.. maybe more like 65000 colors. but not 16 or 24 bit colour. 
the real big problem is that it appears to be the same no matter what os i boot into. or what i do to change the drivers..

i cant swear that it is because of the drivers. but everything was fine untill i changed the drivers in ubuntu..

the only good thing is that external monitors connected to the laptop still look fine..
 if anyone knows of a fix. or any other help..

thank you in advance

(and yes i have the color setting at max, and yes i have checked everything i can think of. same color issues in ubuntu AND winblowx xp)

---

### Post by tread29 on 2009-04-06
revert back to 170.

---

### Post by KhaaL on 2009-04-06
Since you don't know for sure what change made your desktop goof-up, it's hard to help you get it working again. 

have you run the nvidia config tool and tried the settings there? It might be something there, since as i understand externam monitors are working fine...

---

### Post by oooh on 2009-10-17
I agree, simply go back to the latest stable version, 177 I believe. 180 I think is so far a BETA

Sytem-administration-hardware drivers. The previous drivers must be listed.

I had another problem, colours where having the wrong tone (al reds where greenish) so I had to go back to 177. I tried in 180 to solve the problem, I managed by telling all programs to use Xvideo, but gxine and mplayer and skype where not switching to xvideo, so I gave up !

---

### Post by xxterry1xx on 2009-10-17
> **nutpants said:**
> i just installed the new nvidia drivers on my dell xps m1210.
problem is the colors on my laptop display are all wrong now.
the screen looks like its almost in 256 colors.. maybe more like 65000 colors. but not 16 or 24 bit colour. 
the real big problem is that it appears to be the same no matter what os i boot into. or what i do to change the drivers..

i cant swear that it is because of the drivers. but everything was fine untill i changed the drivers in ubuntu..

the only good thing is that external monitors connected to the laptop still look fine..
 if anyone knows of a fix. or any other help..

thank you in advance

(and yes i have the color setting at max, and yes i have checked everything i can think of. same color issues in ubuntu AND winblowx xp) heh try compiling the drivers for your kernel
if you want the latest kernel it is right here [http://www.kernel.org/](http://www.kernel.org/) and a tutorial [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
anyways
so download the latest nvidia driver off [www.nvidia.com](www.nvidia.com)
make sure the file is on your desktop
so heres an example of what your going to do i would write this on paper or print it
ctrl alt f1 this will bring you to tty1 then log in
then sudo /etc/init.d/gdm stop
sudo -s (make sure numlock is on if you use the numpad)
then cd Desktop
and sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
btw this is case sensitive like 
NVIDIA = right
nvidia = wrong
see if that works if it doesnt then idk
o i forgot theres a few options and keys to use when you install the latest drivers
it will say something like would you like to download nvidia drivers and say no
and once your done it will say would you like to update your xconfig or w.e its called and select yes

keys to use:
tab-for selecting yes or no stuff like that
enter-its just like clicking on a button

---

### Post by Paqman on 2009-10-17
> **xxterry1xx said:**
> heh try compiling the drivers for your kernel


Probably not necessary, or really a suitable endeavour for the Absolute Beginner's forum ;)


> **nutpants said:**
> same color issues in ubuntu AND winblowx xp)

Then your problem is hardware, not software.

---

### Post by xxterry1xx on 2009-10-17
> **Paqman said:**
> Probably not necessary, or really a suitable endeavour for the Absolute Beginner's forum ;)


Then your problem is hardware, not software.
heh yeah true lol but if he or she does want to then master kernel explains it very good

---

### Post by RedRat on 2009-10-17
Is this a laptop. Please excuse my ignorance of all Dell products. It does sound like a hardware problem if it occurs in both Windows and Linux. If it is a hardware problem, you might try the old trick of powering off the computer, disconnecting the power cord and then physically removing the battery for a minute. Replace battery and power back up.

If it is desktop, sounds like a problem with your video card--this is not unheard of. I had to replace a supposedly high quality video card after about year and half.

---

