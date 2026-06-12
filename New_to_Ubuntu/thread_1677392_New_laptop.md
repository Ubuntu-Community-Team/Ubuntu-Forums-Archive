---
title: "New laptop"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Artanis.ro on 2011-01-28
I have a new laptop, on which I intend to use ubuntu of course (my new laptop is HP 6730b with a super processor T9600).
This being the noobs section, I have some questions:
Could you please point me to a good tutorial on how to install video drivers in ubuntu 10.10? Especially Intel drivers, cause I have a intel video card (Intel 4500 MHD).
Apart from this how do I figure out what drivers I have to install apart from the video card? My PC knowledge strongly relates to windows, on windows you look in device manager and see what drivers you need or don't need. So, what is ubuntu's device manager?
If I want to see my additional drivers from the administration section it tells me that "no proprietary drivers are in use by this system".

Also, I would like very much if I could get one of those awesome animated desktop themes for ubuntu, but I guess its a long way till I will get to handle one of those.

thank you

---

### Post by lisati on 2011-01-28
Have you tried the "Live CD" yet? This might give you an idea of whether or not you need to go hunting for drivers and then figuring out how to install them.

The "Live CD" is the same CD as the regular installation CD, where you tell the boot process that you want to try Ubuntu without installing anything.

---

### Post by davidmohammed on 2011-01-28
generally, intel supports linux very well - you rarely need to install drivers yourself.

That is similarly true for most common types of hardware - the linux kernel takes care of supporting your hardware.

if you type in a terminal

lshw | more

this will give you are hardware listing - if any hardware is "unclaimed" then the kernel doesnt recognise your hardware and you'll need to find and install the drivers.

---

### Post by Artanis.ro on 2011-01-28
> **lisati said:**
> Have you tried the "Live CD" yet? This might give you an idea of whether or not you need to go hunting for drivers and then figuring out how to install them.

The "Live CD" is the same CD as the regular installation CD, where you tell the boot process that you want to try Ubuntu without installing anything.

Unfortunately at this moment I have dual boot installed on my system and I use encryption, therefore I can't use the live cd.

---

### Post by Artanis.ro on 2011-01-28
> **davidmohammed said:**
> generally, intel supports linux very well - you rarely need to install drivers yourself.

That is similarly true for most common types of hardware - the linux kernel takes care of supporting your hardware.

if you type in a terminal

lshw | more

this will give you are hardware listing - if any hardware is "unclaimed" then the kernel doesnt recognise your hardware and you'll need to find and install the drivers.

Thank you for your answer, I saw that for display 0 the videocard is recognised.

What desktop manager would you recommend me for my laptop?

---

### Post by davidmohammed on 2011-01-28
given your specifications I would recommend either standard ubuntu with the gnome interface - or kubuntu with the kde interface.

I'll leave it to you to decide which interface is for you - the rivallary between the kde vs gnome people is legendary :P

Since you got such a great laptop - switch on full desktop effects and have fun!

---

### Post by treesurf on 2011-01-28
I have Intel 4500MHD in my laptop as well, and there is no need to install any additional drivers.  It works just fine out of the box with the drivers already integrated in the kernel.

---

### Post by uRock on 2011-01-28
> **Artanis.ro said:**
> Unfortunately at this moment I have dual boot installed on my system and I use encryption, therefore I can't use the live cd.
The LiveCD will have no impact on your encryption, nor will the encryption prevent the LiveCD from working.

---

### Post by lisati on 2011-01-28
> **Artanis.ro said:**
> Unfortunately at this moment I have dual boot installed on my system and I use encryption, therefore I can't use the live cd.

As uRock has pointed out, the encryption on your hard disk will have no impact on your ability to run the LiveCD. The idea is to boot from the LiveCD and run Ubuntu from there instead of from your HDD. You can then see how well Ubuntu works. If it boots from the CD into a GUI, chances are you won't need to mess about installing drivers.

---

### Post by ashickur.noor on 2011-01-28
You can imagine  live cd is a clone of Ubuntu, which you will see after install. You don't need to worry coz live cd's will not effect on your hardwares. So try it.
Intel gives better support for open source more then AMD. I am using Intel 4500 HD graphics card in my laptop. I have nto install any driver for ubuntu. So try it.

---

