---
title: "fixing graphics resolution"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by MrMagnus on 2009-01-26
Hello!

I would just like to start off by saying that I am a complete beginner concerning Ubuntu and Linux in general.
I'm not very computer savvy either to tell the truth, I know how to find my way around windows and can comprehend most software, but thats basically it...

I know nothing about computer programming and especially not how to configure a Linux distro like Ubuntu.

At the same time I think Linux is awfully exciting, what with its development the last years, and all the different versions available.
Also the plain fact that you can resurrect an old computer with the help of a Linux distro. 
And of course just the fact that there is an alternative to Windows OS is wonderful.

But, I still have a vast universe of knowledge to obtain regarding Linux and although I love to learn new things, I ask you all to bear with me when I ask stupid questions... ;)

My question is, I installed Ubuntu 8.10 yesterday. At first glance it's very impressive, however, I can't seem to get the graphics working at 100%

I'm using a Packard Bell Notebook laptop which is 3 years old and when I first ran the Ubuntu Live CD the screen whould just freeze as soon as the installation had run for a few minutes.
I later switched to "safe graphics mode" and after that the disk installed without problems.
However the graphics won't run higher than 800x600, but when Windows XP was installed it could go to 1024x768.

Does anybody know how I can upgrade my graphics?

Kind regards

///Magnus

---

### Post by x33a on 2009-01-26
did you try system -> preferences -> screen resolution?

if it doesn't work, you might have to get new drivers for your system.

---

### Post by Izek on 2009-01-26
> **x33a said:**
> did you try system -> preferences -> screen resolution?

if it doesn't work, you might have to get new drivers for your system.

[Or try this tutorial]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by MrMagnus on 2009-01-26
Thanks for your reply X33a!

Yes, I did try changing the screen resolution, however 800x600 was the top limit.

Can I simply download a driver from the net, after checking what graphics card I have in my laptop?

///Magnus

---

### Post by MrMagnus on 2009-01-26
Sorry Izek! 

Didn't see your reply there...
I'll check out the tutorial and see if it works!
Thanks! :p

///Magnus

---

### Post by x33a on 2009-01-26
try system -> administration -> hardware drivers.

if you don't find any drivers there, then you'll have to manually install the drivers.

---

### Post by rlj1965 on 2009-01-26
> **MrMagnus said:**
> Hello!

I would just like to start off by saying that I am a complete beginner concerning Ubuntu and Linux in general.
I'm not very computer savvy either to tell the truth, I know how to find my way around windows and can comprehend most software, but thats basically it...

I know nothing about computer programming and especially not how to configure a Linux distro like Ubuntu.

At the same time I think Linux is awfully exciting, what with its development the last years, and all the different versions available.
Also the plain fact that you can resurrect an old computer with the help of a Linux distro. 
And of course just the fact that there is an alternative to Windows OS is wonderful.

But, I still have a vast universe of knowledge to obtain regarding Linux and although I love to learn new things, I ask you all to bear with me when I ask stupid questions... ;)

My question is, I installed Ubuntu 8.10 yesterday. At first glance it's very impressive, however, I can't seem to get the graphics working at 100%

I'm using a Packard Bell Notebook laptop which is 3 years old and when I first ran the Ubuntu Live CD the screen whould just freeze as soon as the installation had run for a few minutes.
I later switched to "safe graphics mode" and after that the disk installed without problems.
However the graphics won't run higher than 800x600, but when Windows XP was installed it could go to 1024x768.

Does anybody know how I can upgrade my graphics?

Kind regards

///Magnus



First thing is to determine what graphics card or chip you have in the computer. There may be a driver for it to install at >System>Administration>Hardware Drivers. If not, you might try to go to System>Synaptic Package Manager and search for envyng. Once you install envyng,you can use it to install the appropriate ati or nVidia driver. Do a google search for envyng and you will find a tutorial.

---

