---
title: "Flickering log in screen"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Registered User on 2009-11-04
Hi,

I'm new to Ubuntu and Linux, so please forgive me if this is a common query/problem.

When I boot into Ubuntu from the Grub menu my screen keeps flickering and I'm unable to input my username and password (it's random which keys are recognized).  I can log in using Recovery mode (the screen doesn't flicker), but I don't know what to do once I'm in a command prompt.

Additional info: 

When I downloaded and tried the 64bit version running from the cd (dvd) I liked it, so I installed it (full install).  I made a 20gig partition and clicked the option to enable access to my files on Vista.  But when I log into windows I don't see a partition other than the 3 I already had (OS, Recovery and D drive).  Does this mean I didn't partition correctly and that's what's causing the problem?

Also, can I change the default boot in Grub back to Vista instead of booting into a broken log in screen?

Thanks for your help


System Spec:

HP HDX18 Notebook
Intel Core 2 Duo CPU P8400 @ 2.26GHz 2.27 GHz
OS: Vista 64 (home)
RAM: 4.00 GB
Graphics: NVIDIA GeForce 9600M GT
HD: 2 X 250 GB

---

### Post by pmp on 2009-11-05
I get the same flickering login window in ubuntu 9.10. Login in normal mode is not possible. I can not start the 9.10 gdm successfully.
 
I see a message that tells about about firewall program (firestarter) going down when I try to login in the flickering login window.
 
I updated from 9.04 (that was working fine) to 9.10.
 
I can get the cli up but not gui, if I first login to to the failsafe mode (failsafe login does not flicker!).
 
If I try to start gdm in the cli it does not come up but gives following error:
 
ubuntu 9.10 acer_acpi: No or unsupported WMI interface, unable to load.
 
My PC is ACER aspire t135 pc with 250 GB hard disk.
 
I have given the manual upgrade steps in the CLI (that are in ubuntu page) to ensure upgrade is complete. I also have done all the steps in failsafe login menu (correct broken packages, update grub etc). None of above has helped the situation. I had the latest 9.10 packages available 4th October and this was the result.
 
Any advice would be appreciated!

---

### Post by hellblazer on 2009-11-05
I answered pmp's problem [here]("http://ubuntuforums.org/showthread.php?t=1315319"), have alook it might work for you

---

