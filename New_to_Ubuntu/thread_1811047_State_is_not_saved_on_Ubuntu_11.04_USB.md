---
title: "State is not saved on Ubuntu 11.04 USB"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by eLancaster on 2011-07-24
Hi Guys, 

I installed Ubuntu 11.04 on a 8 GB USB drive. 
When I turn on my laptop, I simply boot from the USB Drive.

There are two problems though, 

1. I don't see that dock on the left hand side. Is there something I have to do to be able to see it?

2. Any changes I make disappear the next time I boot from the USB drive.e.g. if i install google chrome in one session; the next time i'll login, it'll go back to it's original chromelesss self. Is that supposed to happen? Is there a way to stop that from happening.

Thanks for your help.

---

### Post by XubuRoxMySox on 2011-07-24
It's called "Persistence" - You can easily make a "persistent" USB of Ubuntu by following the instructions here: [Create a Persistent Bootable Ubuntu USB Flash Drive]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

Enjoy!

-Robin

---

### Post by amjjawad on 2011-07-24
> **eLancaster said:**
> Hi Guys, 

I installed Ubuntu 11.04 on a 8 GB USB drive. 
When I turn on my laptop, I simply boot from the USB Drive.

There are two problems though, 

1. I don't see that dock on the left hand side. Is there something I have to do to be able to see it?

2. Any changes I make disappear the next time I boot from the USB drive.e.g. if i install google chrome in one session; the next time i'll login, it'll go back to it's original chromelesss self. Is that supposed to happen? Is there a way to stop that from happening.

Thanks for your help.

Hello and Welcome :)

How did you install Ubuntu on that USB drive?
Could you please explain?

---

### Post by helpmeut on 2011-08-25
hello i have a problem i dont know why but when i want to enter on unbutu after i instaled the screen just stays balck and does nothing...can some1 help me with this?

---

### Post by amjjawad on 2011-08-27
> **helpmeut said:**
> hello i have a problem i dont know why but when i want to enter on unbutu after i instaled the screen just stays balck and does nothing...can some1 help me with this?

Hello and Welcome :)

Are you having the same issue as the Original Poster posted in this thread?
If not, please start your "own" thread and explain clearly your problems and the steps you followed/did to fix the issue. Also, please post about your Hardware Specifications and what version of Ubuntu are you trying to install.

Thank you :) 

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by I2k4 on 2011-08-28
> **XubuRoxMySox said:**
> It's called "Persistence" - You can easily make a "persistent" USB of Ubuntu by following the instructions here: [Create a Persistent Bootable Ubuntu USB Flash Drive]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

Enjoy!

-Robin

The current version of the Pendrive installer is available here from Ubuntu, at Step 2 for Live USB:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The "Persistence" is now set with a slider. With an 8GB card you should allocate 5 or 6 GB to "Persistence" (it will take a while to format that.)  My experience with Live USB has been pretty good, but I suggest avoiding major OS upgrades and only installing or updating software one or two packages at a time.  Large upgrades don't work well on slow USB.  

If you intend to keep running Live USB without installing (as I do) you might want to test lighter weight versions like Lubuntu 10.10 - I found 11.04 quite slow by comparison.

---

### Post by beew on 2011-08-29
> **eLancaster said:**
> Hi Guys, 

I installed Ubuntu 11.04 on a 8 GB USB drive. 
When I turn on my laptop, I simply boot from the USB Drive.

There are two problems though, 

1. I don't see that dock on the left hand side. Is there something I have to do to be able to see it?

2. Any changes I make disappear the next time I boot from the USB drive.e.g. if i install google chrome in one session; the next time i'll login, it'll go back to it's original chromelesss self. Is that supposed to happen? Is there a way to stop that from happening.

Thanks for your help.

As others said you need persistence to save your settings. I think, however, a live usb can only support 4G of files (it uses FAT) so you are wasting 4 G with your 8G usb.

For 1, you probably need to update your system and reboot to run Unity. For this you need to be able to save your settings, or everything will be lost on reboot. But be careful what you update because kernel upgrade and updating some system components may break your live usb and you may run out of space.

I find the liveusb a very limited way for testing, I would suggest you make a full install on your 8G usb instead (while unlike the live usb it supports all upgrades and installation of proprietary graphic cards, it will be slow, a much better way would be to install into an external hard drive)

---

