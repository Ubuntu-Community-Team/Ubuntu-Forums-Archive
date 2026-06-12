---
title: "shutdown while updating form 8.10 to 9.04"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by dkumar on 2009-07-04
Hi all,

i am little new to linux .

i was updating my ubuntu from 8.10 to 9.04 and it was only half way done and the power went off. Now when i open ubuntu, it although lets me give my user name and password but after that its all blank screen. 

I am not sure what to do and i am helpless now. 

Please help me with this as i don't want to use windows.

thanks

looking for replies.

---

### Post by ubudog on 2009-07-05
Go to another computer and download 9.04 from [www.ubuntu.com](www.ubuntu.com) and install it off the cd.

---

### Post by hallenr on 2009-07-05
I am also new to ubuntu, but i have been running 8.10 for more then a month now. Today I decided to upgrade to 9.04. I successfully downloaded the 1018 files. but since the installation progress showed that installation will take more then an hour, so after some 20 minutes i decided to take a bath in the meantime. When I came back, i could only see the Ubuntu default desktop image, nothomg else seemed to work. So, i manually resarted the computer. Now, when ever i start, i am struck with the following message:

"Your session only lasted less then 1- seconds. If you have not logged off yourself this could mean that there is an installation problem. Try logging in with one of the failsafe options. See if you can repair............"

ow that is totally greek to me. Can some one help me to restore my system. Presently I am working from the Ububtu 8.10 CD without installing!

---

### Post by ubudog on 2009-07-05
You probably got that message because you turned it off with the power button.  You need to boot into recovery mode I think.  It's been a long time since I've had that problem.

---

### Post by ubudog on 2009-07-05
Boot into your main hard drive I mean.  Not the CD.  In grub select the one that says Recovery Mode at the end.  If that doesn't work then boot from your cd and select Repair a Damaged System.   Hope that helps.

---

### Post by hallenr on 2009-07-05
Yes, i rebooted my system, but am unable to figure out how to repair. Please tell in a bit more detail. I got to the grub, but what command should i use. Similarly I get no option from my 8.10 CD supplied by UBuntu.

---

### Post by ubudog on 2009-07-05
Use the one that has "Recovery Mode" at the end or something involving Recovery.

---

### Post by hallenr on 2009-07-05
Can you please spell out the command that i need to type in at the grub command prompt?

---

### Post by ubudog on 2009-07-05
You shouldn't need to use the command prompt.  Just select the one with Recovery Mode.

---

### Post by LewRockwell on 2009-07-05
> **hallenr said:**
> i am also new to ubuntu, but i have been running 8.10 for more then a month now. Today i decided to upgrade to 9.04. I successfully downloaded the 1018 files. But since the installation progress showed that installation will take more then an hour, so after some 20 minutes i decided to take a bath in the meantime. When i came back, i could only see the ubuntu default desktop image, nothomg else seemed to work. So, i manually resarted the computer. Now, when ever i start, i am struck with the following message:

"your session only lasted less then 1- seconds. If you have not logged off yourself this could mean that there is an installation problem. Try logging in with one of the failsafe options. See if you can repair............"

ow that is totally greek to me. Can some one help me to restore my system. Presently i am working from the ububtu 8.10 cd without installing!


this should be a separate thread, moderator if you would please...


.

---

### Post by hyperdude111 on 2009-07-05
Fresh installs ALWAYS work better than upgrades in my experience. 8.10 is also now quite old I would recommend 9.04.  

Both of your problems were caused by shutting down prematurely during an update. This would have the same effect as turning of our pc when installing the OS (a broken system).

Use the live cd to save any precious docs to usb then re-install.

---

### Post by LewRockwell on 2009-07-05
> **hallenr said:**
> I am also new to ubuntu, but i have been running 8.10 for more then a month now. Today I decided to upgrade to 9.04. I successfully downloaded the 1018 files. but since the installation progress showed that installation will take more then an hour, so after some 20 minutes i decided to take a bath in the meantime. When I came back, i could only see the Ubuntu default desktop image, nothomg else seemed to work. So, i manually resarted the computer. Now, when ever i start, i am struck with the following message:

"Your session only lasted less then 1- seconds. If you have not logged off yourself this could mean that there is an installation problem. Try logging in with one of the failsafe options. See if you can repair............"

ow that is totally greek to me. Can some one help me to restore my system. Presently I am working from the Ububtu 8.10 CD without installing!

Is ubuntu the only operating system on your computer?

If it is then during your previous installation the grub bootloader would NOT have been installed...therefore some of the previous posts do not apply.

Best Solution:

Rescue anything you want off the hard drive and then...secure erase the drive, repartition, and do a clean, fresh install of Jaunty!

Here, this will help you with any erasing, cloning, and partitioning you might need to do([http://www.partedmagic.com/](http://www.partedmagic.com/))

.

---

### Post by louieb on 2009-07-05
> **LewRockwell said:**
> ... the grub bootloader would NOT have been installed...
.

Thats not true. GRUB is install by default. Hiddenmenu may be turned on. If so you need to press esc during boot to show the GRUB menu.  

> **LewRockwell said:**
> Best Solution:..

I agree.  Have had problems with upgrades in the past - guess about 50% have worked without a problem. For the other half - I did a reinstall.

---

