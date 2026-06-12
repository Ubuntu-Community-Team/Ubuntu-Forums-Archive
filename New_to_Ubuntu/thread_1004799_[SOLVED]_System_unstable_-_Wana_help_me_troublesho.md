---
title: "[SOLVED] System unstable - Wana help me troubleshoot"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-07
Reference: [http://ubuntuforums.org/showthread.php?p=6321972#post6321972](http://ubuntuforums.org/showthread.php?p=6321972#post6321972)

My system has become unstable. Particularly problems with X. I've had to use the fix in Reference (above) twice.

I've removed recently installed applications. Skype, and evolution add ons. I've gone one step further and removed evolution all together.

What log files should I be looking at? 
 
How do I schedule the system to run "fsck -pcf" on all file systems at next boot?

Any other advice?

---

### Post by gettinoriginal on 2008-12-07
It is possible that you have deleted necessary files or programs while deleting evolution.

When rebooting, hit esc during boot splash and choose "fix broken packages" (I don't remember the exact wording)  See if that helps.

---

### Post by ant2ne on 2008-12-08
I removed evolution and skype and things SEEM better. Not sure yet. So the deleting of files theory...

---

### Post by gettinoriginal on 2008-12-08
Places > File System > var > log > Xorg.0.log  might give you some info

---

### Post by bumanie on 2008-12-08
Removing evolution will have caused the problem. At least evolution-data-server-common  has to be kept or else your system will be unstable.

---

### Post by ant2ne on 2008-12-08
> **ant2ne said:**
> I removed evolution and skype and things SEEM better. Not sure yet. So the deleting of files theory...I removed skype and evolution, and it has yet to crash. REMOVING evolution does not seem to be the problem. Installing it may have been

---

### Post by gettinoriginal on 2008-12-08
It doesn't have to do with just Evolution, but the dependencies between that and gnome.  Since it is installed by default, they are tied together by those dependencies.  But if your system is working now as you want it then congrats, and good luck.  If you feel this problem is solved, please go to the tools and mark it as solved   :p

---

### Post by ant2ne on 2008-12-08
> **gettinoriginal said:**
> It doesn't have to do with just Evolution, but the dependencies between that and gnome.  Since it is installed by default, they are tied together by those dependencies.  But if your system is working now as you want it then congrats, and good luck.  If you feel this problem is solved, please go to the tools and mark it as solved   :pNo, not solved. I do want to run evolution and skype, darn it. But as those were the things I was messing with most recently, I removed them to see if stabilization returns, which it has, to some extent.

The plot thickins. I just had to restart the system as All of my RAM and all of my SWAP was being gobbled up. The system locked up on the Resources tab of System Monitor, so I didn't get to see what process was using up all of my RAM. I've got the monitor up and on the Process tab now, in case it does it again.

I still would like to 
> How do I schedule the system to run "fsck -pcf" on all file systems at next boot?On a windows system I'd just do a chkdsk /R and it would prompt me if I wanted it to run at next boot.

Xorg.0.log doesn't show anything obviously wrong.

---

### Post by ant2ne on 2008-12-15
Well... no replies. It has been a week+ and I've had no more crashes. I'm going to re-install applications one at a time (after finals week) and see if crashes start up again. I'll keep you posted.

---

### Post by maddog46113 on 2008-12-15
Might run a prime95 torture test or check your memory blocks. If you run prime95 let it torture your computer for about 6 hours or more. See if its a hardware problem.

---

### Post by RJARRRPCGP on 2008-12-15
Sounds like when the video driver isn't installed properly.
 
Especially when X crashes during the launching of Chromium.

---

### Post by ant2ne on 2008-12-17
I haven't changed my graphics settings since installations. This OS has been running flawlessly for many months. I'm not discounting that it is GUI related. I think there is a good chance of that.

The system locked up and was unresponsive again. Something had gobbled up all of my RAM and SWAP.  I have 8 Gigs of both.  Once again, I couldn't get any information to determine which process was using up all the RAM. I'm going to look into make a CRON job that runs a script to gather info on processes.  

Today I get the message "Software index is broke" and that I must run "sudo apt-get install -f" I'm not sure if that is related to my other problem. 

I would still like to know how to force a disk checking. On a WIN system, RAM and Memory errors are often actually hard drive problems.

---

### Post by ant2ne on 2009-01-04
I think I found the culprit. I notice as my system was begining to lock up, that CPU4 was at 100% and pidgin was using 23% of all resources, IE 1 CPU worth. I killed pidgin, removed and re-installed, and I have had no problems since. I think I will start re-installing other suspected programs. But I'm fairly sure I got this one.

---

