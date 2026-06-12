---
title: "Black screen after Ubuntu start up"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by hzrunner on 2009-04-03
I have Ubuntu 8.10 installed on a Dell Inspiron 2650 with a nVidia GeForce2 graphics processor. I use it mostly as a back-up internet computer. It worked fine until I decided to change a graphics setting. Now after rebooting it shows the start-up display, plays the sound and goes blank.
I tried some of the suggestions, e.g. pressing "Esc" during booting, which gives me a selection of several options: Ubuntu 8.10 Kernel 2.6.27-11 generic or -11 gerneric (recovery), same for -9 and -7. From there I can select various options but I don't really know what to do with them.
I also pressed 'Ctrl'-'Alt'-'F1' at the black screen, but there it wants a user name and password from me. I did write my password, but I have never needed a user name. 
How do I get out of this without having to re-install.
Thanks in advance and keep suggestions simple.

---

### Post by Black_Wolf_92 on 2009-04-03
Ok, there are a few things you should try.

When it asks for your "username" it is the first word of the NAME you entered when installing ubuntu. Its also the name that appears by default on the button in your task bar.

I basically had the same problem as you, when attempting to install the recommended "hardware driver" for my computer's graphics card. I fixed this by booting into recovery, and choosing the option that fixes broken packages (can't recall the option right now)

---

### Post by hyperyoda on 2009-04-03
> **hzrunner said:**
> I have Ubuntu 8.10 installed on a Dell Inspiron 2650 with a nVidia GeForce2 graphics processor. I use it mostly as a back-up internet computer. It worked fine until I decided to change a graphics setting. Now after rebooting it shows the start-up display, plays the sound and goes blank.
I tried some of the suggestions, e.g. pressing "Esc" during booting, which gives me a selection of several options: Ubuntu 8.10 Kernel 2.6.27-11 generic or -11 gerneric (recovery), same for -9 and -7. From there I can select various options but I don't really know what to do with them.
I also pressed 'Ctrl'-'Alt'-'F1' at the black screen, but there it wants a user name and password from me. I did write my password, but I have never needed a user name. 
How do I get out of this without having to re-install.
Thanks in advance and keep suggestions simple.

Hi,

I'd boot up with a Live CD and then chroot into the root partition and change your /etc/X11/xorg.conf

Zach

---

### Post by mgmiller on 2009-04-03
> I tried some of the suggestions, e.g. pressing "Esc" during booting, which gives me a selection of several options: Ubuntu 8.10 Kernel 2.6.27-11 generic or -11 gerneric (recovery), same for -9 and -7. From there I can select various options but I don't really know what to do with them.You are very close to the answer.  Get back to that screen and select the line ending in -11 generic (recovery).

Press enter to boot that kernel.  You will get a lot of text stuff scrolling by on your screen.  It will then settle down to a blue screen with a few choices on it.  I believe the last one is "xfix  fix the xserver" or something very close to that.  Use the up and down arrow keys to high lite that entry and press enter.  It will do it's thing and then you will be prompted to continue the regular boot.   Hopefully, you will be back on your normal desktop.  You will be running whatever the open source driver is for you video card at this point, so you may need to run the System > Administration > Hardware Drivers application again to get back your accelerated driver.

Hope this helps.

---

### Post by hzrunner on 2009-04-03
Thanks to all of you. Now I got my user name and following mgmiller's xfix suggestion got me back going again. It worked.

---

