---
title: "Ubuntu doesn't boot"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by giulia on 2009-10-03
Hi,

I am quite new to ubuntu and, thus, inexpert. 
I have windows Vista installed. Some months ago I decided to install Ubuntu from Vista. I didn't burn a CD and I didn't partitioned my computer. I directly install ubuntu from windows. I know it's terrible, but I thought it was temporary. At the end I never change it and I kept installing programs on ubuntu. 

Now, a couple of days ago, my ubuntu crashed unexpectely while I was not even using it. Since then, when I try to start ubuntu I reach a black screen. I can see only the cursor on a wating mode. 

I tried to go from the recovery mode, but I don't really know what I am supposed to do. I went on the root and I typed "sudo fdisk dev/sda" and it said that the number of cylinders used is something around 3000 (I think). That there was nothing wrong with it, but since it was more than 1050 (or something similar) it could have caused problems with booting from other OSs.
 
Can someone help me? Can I still fix this problem? I am really a beginner and I don't have any idea on what I am supposed to do! 

Thank you very much!!!

---

### Post by Paddy Landau on 2009-10-03
I guess that you mean you installed [Wubi]("http://wubi-installer.org/").

Wubi is only meant to be temporary, because unfortunately it relies on the underlying Windows and NTFS system. Wubi is not as reliable as a native install; it also runs a little slower and lacks certain features.

As a first step, I suppose you need to check your disk from Windows. Boot into Windows, right-click your C: drive (e.g. from Computer), select Properties, and if I remember correctly then comes Tools and Check Disk. Select Immediately, and the computer will schedule the check for the next boot. Reboot into Windows again to let the check proceed.

Cross fingers (but I'm not hopeful) that this will solve your problem. If not, perhaps someone more experienced than I will be able to help you.

But in the long run, I think that the best bet will be to uninstall Wubi and create a native installation of Ubuntu, and restore your data from your backup (you did make regular backups, didn't you?).

---

### Post by river226 on 2009-10-03
> **giulia said:**
> 

I have windows Vista installed. Some months ago I decided to install Ubuntu from Vista. I didn't burn a CD and I didn't partitioned my computer.



I would burn the disc and do a proper installation, unless you are only experimenting with it, then you could simply use VMware, or virtualbox and try it out virtually. Essentially remove the installation, and go with a safer set up. But if you do do a proper installation i recommend creating the disc space with windows disc manager, then formatting the free space with ubuntu, you don't need to do this for VB, or VM

 > **giulia said:**
> 

Can I still fix this problem?



I don't know if there is a way to fix it without a removing it, sorry

---

### Post by giulia on 2009-10-03
To Paddy: I don't have Wubi. I have Ubuntu 8.10. I download the iso file for the installation and I run it with Daemon Tools. Now each time I start the computer I can choose which one of the operating system I want to use. Unfortunately not anymore cause ubuntu doesn't boot. :) Anyway, I tried to check the disk as you said, but it doesn't seam to have solved the problem... :( But thak you anyway!  

To river226:  I am planning to do a proper installation and I would have already done it (even though I don't have a back up...), but I was hoping to fix the problem and be able to use it until Monday because I have an assignment to hand in and it took me a lot of time to set up all the programs I need to use for my work...

---

