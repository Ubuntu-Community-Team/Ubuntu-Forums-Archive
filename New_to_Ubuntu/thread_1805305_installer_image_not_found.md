---
title: "installer image not found"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by cjordan8 on 2011-07-15
Hey all, when I installed Ubuntu 11.04 I used a USB flash drive to boot the installer then installed to an 

external USB hard drive.  When the installer was finished I got an error message saying the installer image

 was not found and then the installer finished.  So, I rebooted and Ubuntu loaded fine but when I went to do 

the upgrades and new installs I received error messages with the same installer image type of error.  I used 

terminal to search for the hdmedia files I found on the internet that should be the installer image but none of 

them were found and now I do not know where to go from here.  Thanks in advance for any help!

Christopher Jordan

---

### Post by aktiwers on 2011-07-15
Just a guess..  
If you go to System -> Administration -> Software sources
Type in your password..

Then untick the "installable from CDrom/DVD box and close.

Can you run the upgrades now?

---

### Post by cjordan8 on 2011-07-15
Also, I forget to mention that the error messages only occured on those files appearing to be linked to the same image installer type of error (I say appearing because I am brand new to Linux).  All other upgrades and installs went fine

---

### Post by cjordan8 on 2011-07-15
I did what you suggested and I'm not sure if the updates installed or not.  When I re-opened the update manager after changing the setting you mentioned, the update manager said no updates were found.

---

### Post by cjordan8 on 2011-07-15
The error I am getting is as follows

Sorry, the package "linux-image-2.6.38-8-generic 2.6.38-8.43" failed to install or upgrade.

---

### Post by aktiwers on 2011-07-15
Can you go to Applications -> Accessories -> terminal

And type:
```
sudo apt-get update
```
Type in your password - it wont show anything, dont worry it is typing though.

Then afterwords type:
```
sudo apt-get upgrade
```

Does it finish without errors? Then you are good to go.
If not - please post the errors here.

---

### Post by cjordan8 on 2011-07-15
I did get an error message, I'm attaching the screenshot from terminal.

---

### Post by aktiwers on 2011-07-15
Im not completely sure why you are getting this error - but it seams like it wants to install a Linux kernel upgrade - but for some reason fails.

You could try running these commands and see if it helps:
```
sudo apt-get autoremove
```
```
sudo apt-get install -f
```
```
sudo apt-get upgrade
```

It's a bit of a random shot, but try it out. Maybe someone else knows why you are getting this.

---

### Post by cjordan8 on 2011-07-15
I tried all of those and received the same error message, thanks for trying though!

---

### Post by wildmanne39 on 2011-07-15
Hi, a lot of people of had that problem but I have not seen an solution to it, also several people who it did upgrade for could not boot afterwards so maybe you are the lucking one.

---

### Post by cjordan8 on 2011-07-15
Yeah, it is really strange because the entire package itself is missing so it shouldn't boot should it?  I downloaded a .zip file of linux-2.6.38 onto my desktop but I have no idea if I can even install the kernel from there

---

### Post by aktiwers on 2011-07-15
I'm not using the latest ubuntu so I haven't really been follow this..

But I would not recomment installing a kernel manually, if you are new to Linux. 
If you really want to try it, KernelCheck makes it a lot easier.

---

### Post by cjordan8 on 2011-07-16
Okay, I tried KernelCheck but I get the same error message about not finding the boot image for 2.6.38 and so I tried to install an older kernel 2.6.37 but I couldn't do the install with 2.6.38 missing either.  Thanks again for the tip, I'll keep looking and trying to find something

---

### Post by wildmanne39 on 2011-07-16
Hi, this thread was just marked solved maybe it can help you.
[http://ubuntuforums.org/showthread.php?t=1804405](http://ubuntuforums.org/showthread.php?t=1804405)

---

### Post by cjordan8 on 2011-07-16
Well I figured that the problem was that I made my /boot partition too small which is weird because I followed the ubuntu installer recommendations but anyway I reinstalled and just went 10G to / partition 512M to swap and the rest to /home and when the installer finished everything was working perfectly on the new install!

---

