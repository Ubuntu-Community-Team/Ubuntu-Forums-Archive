---
title: "How to startup directly to XP"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by theopneustos on 2010-02-04
I am still learning Ubuntu. I have the 9.10 version. As I am still learning Ubuntu, I want to startup in XP and only when I have time, startup in Ubuntu, to improve my skills with Ubuntu.

How can I tell my PC to start directly to XP? And how will I change it later to startup directly to Ubuntu again, when I am more "qualified"to use it?

Thanks!

---

### Post by Tiede on 2010-02-04
you need to modify the file /boot/grub/menu.lst and specify that you want XP as default.

Instructions can be found [in this thread](http://ubuntuforums.org/showthread.php?t=170757).

---

### Post by dbowlin17 on 2010-02-04
I would reccomend finding out what version of Grub you have, and also make it so that when you start your computer you can actually go into grub and select either xp or ubuntu. You could set XP as your automatic selection and to go to ubuntu when told otherwise.

---

### Post by Bartender on 2010-02-04
Go to System>Administration>Synaptic Package Manager, maximize the page, click on the Search tool, type in
 
```
startupmanager
```

You should get one result.  Click on the little box just to the left of "startup manager", click "Mark" in the window that pops up, then click "Apply" back on the main screen, then "Apply" in the Summary window.  It's a small download, won't take more than a few minutes even on dial-up.  When Synaptic is done downloading, it'll install.

When it's done, you'll find Startup-Manager in System>Administration.  Fire it up, change the "default operating system" to Windows XP, and Close.  There are other settings you can change in Startup-Manager, but that's the one that'll set Windows to boot first.  You'll still get the GRUB screen when the PC starts up.  Don't touch anything.  It should boot to Windows.

---

### Post by theopneustos on 2010-02-04
> **Bartender said:**
> Go to System>Administration>Synaptic Package Manager, maximize the page, click on the Search tool, type in
 
```
startupmanager
```You should get one result.  Click on the little box just to the left of "startup manager", click "Mark" in the window that pops up, then click "Apply" back on the main screen, then "Apply" in the Summary window.  It's a small download, won't take more than a few minutes even on dial-up.  When Synaptic is done downloading, it'll install.

When it's done, you'll find Startup-Manager in System>Administration.  Fire it up, change the "default operating system" to Windows XP, and Close.  There are other settings you can change in Startup-Manager, but that's the one that'll set Windows to boot first.  You'll still get the GRUB screen when the PC starts up.  Don't touch anything.  It should boot to Windows.
Thanks! The job is done! Working fine!!! Keep up the good work. I still have a question on my NVIDIA driver, but will post a new thread.

---

### Post by dzsulius on 2010-02-05
> **Bartender said:**
> Go to System>Administration>Synaptic Package Manager, maximize the page, click on the Search tool, type in
 
```
startupmanager
```

You should get one result.  Click on the little box just to the left of "startup manager", click "Mark" in the window that pops up, then click "Apply" back on the main screen, then "Apply" in the Summary window.  It's a small download, won't take more than a few minutes even on dial-up.  When Synaptic is done downloading, it'll install.

When it's done, you'll find Startup-Manager in System>Administration.  Fire it up, change the "default operating system" to Windows XP, and Close.  There are other settings you can change in Startup-Manager, but that's the one that'll set Windows to boot first.  You'll still get the GRUB screen when the PC starts up.  Don't touch anything.  It should boot to Windows.
I did it with the startupmanager.
It was perfect and very simple.
Thanks a lot

---

