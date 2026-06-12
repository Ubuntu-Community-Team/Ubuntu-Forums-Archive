---
title: "more Nvidia issues..."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Pellucid_Quietus on 2009-01-15
I am new new to Linux and using Ubuntu 8.04 Hardy.  I had installed this version intially with no issues until I tried to get dual screens.  After that I could start up but with no graphics.  I figured out how to reinstall to a previous working state through the recovery mode on startup.  Since then, though, I haven't been able to use the graphics card fully.  I am running an Nvidia 8600 GT.  I have tried downloading the new driver from the Nvidia website but am unable to open it.  I have also searched through the forum and tried all the suggestions I could find.  

I get an error message trying to enable my graphics card after rebooting. 
There is a discrepancy between the:
 Nvidia kernel module? - 71.86.04   and
 Nvidia driver component - 169.12


Can anyone ease this 4 month struggle?

---

### Post by ushimitsudoki on 2009-01-15
It sounds like you have half of one driver installed and half of another.

My personal preference is to install the drivers from the NVIDIA site and just keep them up-to-date myself.

I've had good luck following these steps from the NVIDIA forums: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

I never had much luck with EnvyNG, but some people have. 

I found that once I got all the repository/packed drivers off my system and the ones from NVIDIA installed myself, things went smoothly. However, getting it to that point **after** I messed about with restricted-extras/Envy/etc. took a lot of fiddling.

---

### Post by hyper_ch on 2009-01-15
why are you unable to open it? How did you try to open it?

---

### Post by Pellucid_Quietus on 2009-01-15
> **hyper_ch said:**
> why are you unable to open it? How did you try to open it?
At first I opened a terminal window and pressed CTRL+ALT+F1.  I never even got a prompt after trying all kinds of key combinations I tried CTRL+C (like DOS) and finally got the prompt then I tried to shut down xorg but was unable to. Thats as far as I was able to go.

---

### Post by hyper_ch on 2009-01-15
log out of the session and start a command line session...

---

### Post by Pellucid_Quietus on 2009-01-15
"log out of the session and start a command line session..."

when I logout i am automatically brought back to the command line proabably due to the video card issue.

---

### Post by Pellucid_Quietus on 2009-01-15
This is one of the fixes I tried but couldn't get past the first line:


sudo /etc/init.d/gdm stop

Then change to the directory that you downloaded the driver to
Code:

cd ~/Desktop

Then you can use the command to install the nvidia drivers
Code:

sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run

If that is the name of the driver you have downloaded.
Then you should be able to start x again
Code:

sudo /etc/init.d/gdm start

---

### Post by Pellucid_Quietus on 2009-01-21
figured it out --- had to install Nvidia x configuration tool.

---

