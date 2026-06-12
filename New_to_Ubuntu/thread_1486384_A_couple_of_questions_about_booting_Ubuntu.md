---
title: "A couple of questions about booting Ubuntu"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by EdiblePlastique on 2010-05-17
So, I just have a couple of quick questions that I'm hoping to get answered about Ubuntu and booting. Not really problems, just questions.

I have Ubuntu installed on one of two partitions of my external hard drive. I've got it all set up so that I can boot into Ubuntu when it's plugged in, and when it's not, I can use Windows. Of course, I can plug it in after Windows starts. 

When I start up my computer with the external plugged in, it shows a menu (supposedly grub) where I can choose between different versions of the Linux kernel. I'm wondering if everyone gets this, or is it just me? I'd kind of like to disable it for slightly faster boot times. 

My second questions is pertaining to the splash image that's shown on boot. I'm pretty sure 9.04 or 9.10 had a nice little spotlight with the Ubuntu logo in it, and some cool pulsating load bars. Why was this changed to a far more boring arrangement of dots that light up and the Ubuntu logo? Could you point me in the direction I could go to change it? 

Well, that's all. Thanks.

---

### Post by ubunterooster on 2010-05-17
Sounds like you want the "startupmanager" program to speed up the GRUB process; You do not _really_ want to remove grub.

---

### Post by EdiblePlastique on 2010-05-17
Of course I don't want to remove GRUB, I just want to, if possible, disable the menu where I select which version of the kernel is to be used. Still, I'll get startupmanager.

---

### Post by wilee-nilee on 2010-05-17
> **EdiblePlastique said:**
> Of course I don't want to remove GRUB, I just want to, if possible, disable the menu where I select which version of the kernel is to be used. Still, I'll get startupmanager.

The last thing you want to do is disable this, but startup manager will you to what you want with a shorter wait time.

---

### Post by ubunterooster on 2010-05-17
startupmanager will disable this. Which reminds me... I need to go do this myself (just did a reinstall)

Edit: change "timeout in seconds" to 0

---

### Post by drs305 on 2010-05-17
EdiblePlastique, Welcome to Ubuntu and the Ubuntu forums. :-)

If your menu is displayed for about 10 seconds, you can change it either with startupmanager as mentioned previously, or edit the Grub 2 configuration file: /etc/default/grub

```
gksu gedit /etc/default/grub
```

Change:
> GRUB_TIMEOUT=10

To:
> GRUB_TIMEOUT=1

Save the file, then run "sudo update-grub".


The extra menu items are recovery modes and older kernels. Each time a new kernel is introduced, it is added to the menu. The older kernel option is retained. In the "SUM" link in my signature line is a section on older kernels that explains it and what to do as the number of old kernels increases.

Note: Startupmanager is much easier for this task.

---

### Post by anewguy on 2010-05-17
Set the default time out to 0.  don't forget to run update-grub afterwards.

As for the logo screen - I've wondered the same thing.  They took something that looked kinda cool and made it boring.

Dave ;)

---

### Post by ubunterooster on 2010-05-17
> **anewguy said:**
> Set the default time out to 0.  don't forget to run update-grub afterwards.

As for the logo screen - I've wondered the same thing.  They took something that looked kinda cool and made it boring.

Dave ;)
Get: gnome-splashscreen-manager

---

### Post by n213978745 on 2010-05-17
Hi, I will try my best to help you :)

Grub normally will boot automatically into login screen unless it discovers another OS.

Next time before you install ubuntu on your external hard drive, disconnect your computer's internal hard drive first.  This way your grub bootloader of your external hard drive wouldn't record the OS of your internal hard drive.  I have the similar experience as you, however, I am not sure.

And as for timeout, here is the pages that can help you:
[https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202](https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202)

Look for the session: configure grub2


Edit the following document with terminal, enter:
[PHP]gksudo gedit /etc/default/grub[/PHP]
Change the following:
***#GRUB_HIDDEN_TIMEOUT=0*** 
To:
***GRUB_HIDDEN_TIMEOUT=***


And change the below:
***GRUB_TIMEOUT=10***
To:
***GRUB_TIMEOUT=1***


The line ***GRUB_TIMEOUT=1 ***will tell you computer to display grub menu for 1 second.  I never try 0 myself so I don't know.

---

### Post by ubunterooster on 2010-05-17
If possible, use the GUI route until you know more about the OS. I mean, if you want you *can* use CLI but it is often going to make others stressed if the first thing you tell them to do includes the terminal.

---

