---
title: "Can I do this with my Linux Ubuntu?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by icyest on 2009-06-18
I'd like to keep all the settings/programs/repositories/everything and such from my current laptop (which is running 9.04) on to a virtual machine which will be on another computer. 

Can I do this easily? And how?

---

### Post by clive littlewood on 2009-06-18
Hi

Create a live CD/DVD of your sytem using remastersys backup (it's in the repos)

Then just use the live disc to load onto your virtual machine

Voila !!

Clive

---

### Post by Cheesemill on 2009-06-18
Or use CloneZilla to take a disc image of your machine and then restore this into your VM.

---

### Post by adam_kimber on 2009-06-18
There is a way of getting DPKG (the program that installs and uninstalls all the programmes (packages) on your machine) to list all the packages installed on your machine. YOu can then put that in a text file and then tht can be used as a package install on the new machine. Also, most settings such as wallpaper etc are stored in "." files in your home directory so I just keep my /home on a seperate partition. That way i can reinstall as much as I like without loosing settings. So backing up your /home is useful. 

Having said that there are a few system settings that reside in /etc that are very useful to back up. The contents of /etc/apt/ (which should be sources.lst and maybe a folder with additional sources in it) is one such example as that will backup all your repos. Another one (that is no so important these says) is the xorg.conf that resides in /etc/X11. However newer versions of xorg automagically configure themselves so this file is not so important. 

However if you don't want to miss anything I would go with remastersys or a clone of the hd.

---

