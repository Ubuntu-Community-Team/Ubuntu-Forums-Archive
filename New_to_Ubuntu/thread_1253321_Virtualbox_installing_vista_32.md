---
title: "Virtualbox installing vista 32?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-29
i am trying to install Vista 32 bit on Vrbox, it wont install compleatly. i have mt reinstall disks from hp  there's 2 of em not sure if i have to add some thing or what. ya i am basicly clueless so if someone knows of a HowTo that would be great. as i dont know what infor to give for this problem

---

### Post by theozzlives on 2009-08-29
Did you give it enough RAM/Disk Space?

---

### Post by R3fr4cti0n on 2009-08-29
i did the exspanding disk space but 10 to start off with and 2 gigs of ram that enough?

---

### Post by overdrank on 2009-08-29
Please correct me if I am wrong but you can not use restore disc for the install. :confused:

---

### Post by R3fr4cti0n on 2009-08-30
[IMG]http://i645.photobucket.com/albums/uu179/deleteentershift/Screenshot-VR-VistaRunning-SunVirtu.png its not a restore disk per say, its the disks i got when i deleted my whole vista os off the system, this is th error i get
[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://i645.photobucket.com/albums/uu179/deleteentershift/Screenshot-VR-VistaRunning-SunVirtu.png%5B/IMG%5D

---

### Post by R3fr4cti0n on 2009-08-30
ok tried a vista reg disk an di get nothing

---

### Post by R3fr4cti0n on 2009-08-30
ya i cant even get it to start a boot with my vista home premimum diskz any ideas?

---

### Post by Merk42 on 2009-08-30
Are you mounting the CD image in Virtualbox? In your case, put the Vista disc in the drive. Then in VirtualBox, DO NOT START THE MACHINE YET (it's okay if you already created it).  Highlight the machine then under Settings > CD/DVD ROM Drive, tell it to Mount CD/DVD Drive and specify Host CD/DVD Drive.
Then start the machine, it should try to boot from the Vista CD, and (I believe) you press any key to start the installation.

Keep in mind, you need to click into the virtualbox window which will "capture" the mouse, and also let it respond to key commands.  You can fix this post installation by adding the additions.

---

### Post by R3fr4cti0n on 2009-08-30
i got it to install however what it gets to "checking your computer" just after typing a login id VRbox shuts down completely.. what am i missing?

---

### Post by Merk42 on 2009-08-30
> **R3fr4cti0n said:**
> i got it to install however what it gets to "checking your computer" just after typing a login id VRbox shuts down completely.. what am i missing?

I've never installed Vista, installed XP and 7 though. Where are you typing a login ID? Once the entire installation is complete?

---

### Post by R3fr4cti0n on 2009-08-30
when it asked you to make a login id and password i do all that, then it says "checking your computer" then VRBox closes itsself

---

### Post by Merk42 on 2009-08-30
I see, I take it your signature is the specs of the computer you're trying to install it on?
How much HDD and RAM did you give your virtual machine? Also which version of VirtualBox are you using?

---

### Post by R3fr4cti0n on 2009-08-30
well i got it all installed finally, but the width and lenth in full screen is off, i have to scroll  down to even see my start bar, also i have no net, it says that i am connected to my router but there is no signal from router to net, now my net works through ubuntu and i have had this problem before when i did a fresh install of vista, except now the places for the drivers n such r diffrent. Am i sapost to confiure the net outside of the VM in the settings and how do i know what to use, also after i get the net up can i install the Drivers off hp's site like i would with a fresh install or is it diffrent on a VM?
n yes this is all on my tx2
thanks!

---

### Post by Merk42 on 2009-08-30
> **R3fr4cti0n said:**
> well i got it all installed finally, but the width and lenth in full screen is off, i have to scroll  down to even see my start bar, also i have no net, it says that i am connected to my router but there is no signal from router to net, now my net works through ubuntu and i have had this problem before when i did a fresh install of vista, except now the places for the drivers n such r diffrent. Am i sapost to confiure the net outside of the VM in the settings and how do i know what to use, also after i get the net up can i install the Drivers off hp's site like i would with a fresh install or is it diffrent on a VM?
n yes this is all on my tx2
thanks!

Okay you have Vista installed now? Don't think of it as running on HP hardware though, it's like its own virtual machine.

What you want to do now is install guest additions. Just start Vista and at the top of the VB Window: Devices > Install Guest Additions.

You should already have internet though, let us know if you still don't even after installing the Guest Additions.

---

### Post by R3fr4cti0n on 2009-08-30
i clicked it, a few times, i didnt do anything. damn

---

### Post by R3fr4cti0n on 2009-08-30
it wont shut down properly aswell

---

### Post by R3fr4cti0n on 2009-08-30
ya 5 mins now and still has not compleatly stoped just say at 70% and "stopping"

---

### Post by Merk42 on 2009-08-30
Sorry I was out...

What didn't do anything the additions? Maybe you need to unmount the host CD/DVD drive first. Then redo the install Guest Additions, it should appear as a CD in My Computer. Also autorun may be disabled so once you install the additions manually run by exploring the CD.

This step is in the manual. Page 62, if you're using the most recent Virtualbox, 3.0.4.

Also how much ram are you giving the virtual machine?

EDIT: Also there is an entire [subforum dedicated to Virtualization](http://ubuntuforums.org/forumdisplay.php?f=308), so you may find your answers there.

---

### Post by R3fr4cti0n on 2009-08-30
well installed and works well but freezes when i try to shutdown and i have to manualy shutdown by holding in the  button. anyone else have this problem or know a solution.

---

### Post by kokoshmusun on 2010-05-24
Can I install VISTA on ubuntu lucid virtualbox using the RECOVERY DISK that came with the laptop?

I was going to, but then I got to a screen in the recovery process that said my hard disk will be formatted.  And I wasn't sure if this would actually format my actual HD or just a virtual HD (since I've never used virtualbox).  

Any ideas?

---

### Post by Mark Phelps on 2010-05-24
> **kokoshmusun said:**
> Can I install VISTA on ubuntu lucid virtualbox using the RECOVERY DISK that came with the laptop?

Did you even read post #4??

The so-called Recovery disk will completely wipe and replace your hard drive partitions; it is NOT an installation disk.

So basically, as post #4 already said, NO.

---

