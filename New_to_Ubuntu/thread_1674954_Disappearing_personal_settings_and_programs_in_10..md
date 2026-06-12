---
title: "Disappearing personal settings and programs in 10.10 + USB Drive"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Lone Hunter on 2011-01-24
OK so as the title say's I'm new at this like just a few days and this hopefully is a simple question.
I have 10.10 installed to a 4 gb USB pendrive.  I've partitioned it into roughly 3gb primary and 1gb logical drives ( I've done this latterly in an attempt to solve the problem I have)
 
The problem I have is that when I boot from the pendrive 10.10 loads no problem, I can enetr my wireless details and then I configure it's appearance, set regional keyboard settings, install VLC and truecrypt and copy TOR browser to the desk top and all is wonderful in the world of ubuntu.  Then... I shut down and when I come to reboot the next time absolutely everything is lost ie I'm back to the begining again having to set everything up and install.
 
From what I have gained from reading about all your personal settings are store in your "home directory" and that directory should be kept in a seperate partition (hence my partitioning exercise) however trying to copy the home folder to the new partition hit a few bugs and error messages occured about not being able to display "symbolic icons" or something similar and either way the next time I booted everything was undone again!!
 
I love the idea of Linux but clearly I must be doing something wrong because I can't see a whole population of Linux users spending time setting their systems up each time they boot up.
 
HELP !!!  (thanks :redface:)

---

### Post by [Snc] on 2011-01-25
> **Lone Hunter said:**
> OK so as the title say's I'm new at this like just a few days and this hopefully is a simple question.
I have 10.10 installed to a 4 gb USB pendrive.  I've partitioned it into roughly 3gb primary and 1gb logical drives ( I've done this latterly in an attempt to solve the problem I have)
 
The problem I have is that when I boot from the pendrive 10.10 loads no problem, I can enetr my wireless details and then I configure it's appearance, set regional keyboard settings, install VLC and truecrypt and copy TOR browser to the desk top and all is wonderful in the world of ubuntu.  Then... I shut down and when I come to reboot the next time absolutely everything is lost ie I'm back to the begining again having to set everything up and install.
 
From what I have gained from reading about all your personal settings are store in your "home directory" and that directory should be kept in a seperate partition (hence my partitioning exercise) however trying to copy the home folder to the new partition hit a few bugs and error messages occured about not being able to display "symbolic icons" or something similar and either way the next time I booted everything was undone again!!
 
I love the idea of Linux but clearly I must be doing something wrong because I can't see a whole population of Linux users spending time setting their systems up each time they boot up.
 
HELP !!!  (thanks :redface:)

Hey there!

You are not totaly clear on this issue, so i will guess:

"You have a live USB install there?" 

If that is so, please take your time and create the live install USB again, this time the full USB key (no need for two partitions!)

Just make sure to enable the **persistent** file out of the remaining space, this is going to represent your home directory and save your network/browser/desktop settings

So, if under Ubuntu, run this program in terminal or Alt + F2
```
gksu usb-creator-gtk
```In the attached image, there are three steps, you have to do:
1. select the ISO from where the live USB will be created
2. select the pen drive, to where it should be created, if in Live mode, make 100% sure to select the right pen drive (not the one, the system is on!)
and 
3. this is what you want, enable a persistance file and make it as large as possible

One more info: while running on Live USB, never update software, that makes changes to the kernel, i messed some of my live USBs that way...

Let me know how it went!

---

### Post by Lone Hunter on 2011-01-25
Thanks Snc
 
Firstly sorry i was not clear.  I had downloaded Ubuntu 10.10 ISO to my computer along with a util "USB Installer" from Pendrivelinux.com and use the latter to install 10.10 on a 4gb USB pendrive.
I then used the pendrive to boot my desktop system. I'm not sure about the terminology but I would guess this is what is called a "live USB install".
 
When I don't know what I'm doing I tend to leave install settings at default and this is what I did with the USB installer software.  I had seen a box with "persistance" label and 4 options but chose the default "No Persistance".
 
Now with you mentioning that you need this "persistance" thing it's meaning becomes obvious. (well almost obvious to someone raised on Windows for the last 2 decades and use to things still being there when you next boot up lol !! )
 
Well by now my pendrive re-partitoned and a new install of 10.10 has just fininshed with 3gbs of persistance.  I'll be back to let you know if all is well \\:D/

---

### Post by [Snc] on 2011-01-25
> **Lone Hunter said:**
> Thanks Snc
 
Firstly sorry i was not clear.  I had downloaded Ubuntu 10.10 ISO to my computer along with a util "USB Installer" from Pendrivelinux.com and use the latter to install 10.10 on a 4gb USB pendrive.
I then used the pendrive to boot my desktop system. I'm not sure about the terminology but I would guess this is what is called a "live USB install".
 
When I don't know what I'm doing I tend to leave install settings at default and this is what I did with the USB installer software.  I had seen a box with "persistance" label and 4 options but chose the default "No Persistance".
 
Now with you mentioning that you need this "persistance" thing it's meaning becomes obvious. (well almost obvious to someone raised on Windows for the last 2 decades and use to things still being there when you next boot up lol !! )
 
Well by now my pendrive re-partitoned and a new install of 10.10 has just fininshed with 3gbs of persistance.  I'll be back to let you know if all is well \\:D/

Great to hear again from you :)

I am happy to see, that my guess was right :), so if everything turns out OK, please markt this thread as "solved" (under" thread tools").

PS. Please, really remember, that a live USB is only a partial install ie. for test or rescue purposes (!!!), a "real" Linux USB install rocks even more ;)

Even if this article covers version 7.04, it still goes for any other Ubuntu/Linux version
```
http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/
```

---

### Post by Lone Hunter on 2011-01-27
Hi yep everything turned out fine although now slightly confused as to whether I have a "Live Linux USB" or a "Real Linux USB" running.
 
Now to look for a thread which guides me through a "How to do" a WDE of a Linux USB using Ubuntu 10.10 and Truecrypt.
 
Thanks once again :KS

---

