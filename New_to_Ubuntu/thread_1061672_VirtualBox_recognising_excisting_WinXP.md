---
title: "VirtualBox recognising excisting WinXP?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by longtom on 2009-02-06
Hi,

I have downloaded VBox and understand, more or less, from the manual, what it does.

However, I haven't found any references that it might be able to run an existing WinXP installation.

Herewith the plain facts:

First Installation was a WinXP installation on a sata 200GB HD NTFS format.  
Afterwards Ubuntu 8.10 on a seperate 30GB IDE HD.

I kind of had the vision of opening a window in Ubuntu and run WinXP in there and so I never need to boot between my two OSs.  Am I dreaming impossiblities?

Please advice

longtom

---

### Post by konqueror7 on 2009-02-06
well, what you thought is not really impossible, maybe in the near future an new technology would be able to do it...

as of now, virtualbox runs other OSs on from a virtual-harddrive, you must install a fresh copy of winXP on virtualbox...you dont have to boot for it, only that virtualization software such as virtualbox is mostly only for simulating PCs as of now, so some features will still not be able to run on virtualbox, it still better to dualboot (specially of the games can't be ran under wine)...but, still better than nothing...

---

### Post by jrusso2 on 2009-02-06
What you want to do is possible but not recommended as it might damage your XP install if you don't do it right.

This is for an older version of virtualbox but gives you the idea.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

---

### Post by longtom on 2009-02-06
I thought I'm pushing my luck here....

Thank you for the answers.

longtom

---

### Post by anewguy on 2009-02-06
This is indeed not only possible but does work, but as mentioned above with some big "bewares".  I ran this way for a while, against the advice of others, and never ran into trouble.  However, I also have a deep technical background, though dated.  The concepts presented where easy for me to understand and to follow, but that was mainly because of my background.  One minor mistake, and you can kiss your Windows partition goodbye.

I would suggest you read the help included in vbox, as the information is there in a later section.  It's been a while, but I believe I had to do it all with vboxmanage commands.

Personally, I really would highly recommend *NOT DOING IT*.  While a hassle to re-install Windows, install your programs and data, doing so in virtualbox using a virtual disk is really the only way to go.

If you want access to USB devices, be sure to download and install the closed-source (but free) version.  The open-source version does not have USB support.

Dave :)

---

### Post by hyper_ch on 2009-02-06
it is possible to run vbox on a real install but it's not recommended. Windows doesn't like hardware change that much and you would change all your hardware because vbox uses virtual hardware...

---

### Post by HittingSmoke on 2009-02-06
> **anewguy said:**
> This is indeed not only possible but does work, but as mentioned above with some big "bewares".  I ran this way for a while, against the advice of others, and never ran into trouble.  However, I also have a deep technical background, though dated.  The concepts presented where easy for me to understand and to follow, but that was mainly because of my background.  One minor mistake, and you can kiss your Windows partition goodbye.

I would suggest you read the help included in vbox, as the information is there in a later section.  It's been a while, but I believe I had to do it all with vboxmanage commands.

Personally, I really would highly recommend *NOT DOING IT*.  While a hassle to re-install Windows, install your programs and data, doing so in virtualbox using a virtual disk is really the only way to go.

If you want access to USB devices, be sure to download and install the closed-source (but free) version.  The open-source version does not have USB support.

Dave :)

+1 here. I had the idea of doing that at first and realized it wasnt the best idea after looking into it.

After all, Windows installs in Vbox in a flash so if you hose anything you can reinstall in a matter of minutes.

---

### Post by longtom on 2009-02-06
> **hyper_ch said:**
> it is possible to run vbox on a real install but it's not recommended. Windows doesn't like hardware change that much and you would change all your hardware because vbox uses virtual hardware...

Yeah - this is it....thank you for reminding me.  I guess a reinstall is on the cards if I decide to run Windows in Ubuntu.  In the meantime I'll try to get the rest going, like network printers on XP network machines, fixing my samba and the like......I appear to be closer to a Ubuntu reinstall right now...

---

### Post by konqueror7 on 2009-02-06
didn't know there exist a way to do it, thanks for the info...but, still, its still recommended (as you said) to just fresh install a copy of winXP...

---

