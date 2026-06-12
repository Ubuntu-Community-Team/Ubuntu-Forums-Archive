---
title: "cherry with a few questions"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by wardD on 2010-01-05
I am having a few issues with ubuntu.

 first when I try to download software I get a message saying waiting for other software managers to finish,  they never do.

 my system seems to freeze a lot.  sys-   sis730-s  amd processor clocks in @ 890mghz.   on board every thing, 40 gig wd hdd.  cd and dvd burners . floppy drive.   512 megs of ram.

 also having a hard time getting on this forum so I am going to see if this post,s,   then continue.   


  regards ward.

---

### Post by wardD on 2010-01-05
I have used the torent transmission and successfully downloaded an avi, went to play it and it says I need  plug in,  so I go for them and I get this error.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


 ok, well at least the forum is working for me now:guitar:.  and so far  the rig hasn't frooze.

I have run mem tests and hdd diags and all are good. the rig has run xp (sorry) for a long time with out a burp.   I am wondering if maybe I did a crapy burn of the .iso file and maybe that has some thing to do with my delema.  

 anyway, thank you for your time,  and just for the record, this is looking like a pretty cool os , if I ever get it figured out.


 regards.   ward.

---

### Post by pricetech on 2010-01-05
Boot to the CD again and test it.  That's one of the boot options and it will tell you if you have a bad burn.

---

### Post by howefield on 2010-01-05
> **wardD said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Open a terminal (Applications > Accessories > Terminal) and copy/paste or type the command in to it, enter your password and press enter if prompted.

```
sudo dpkg --configure -a
```

---

### Post by natravis on 2010-01-05
Do you currently have Ubuntu installed on the hard drive by itself, dual-booting with Windows, installed within Windows via Wubi or running off the LiveCD?

It is possible to test the disc from the boot screen, it is one of the options. Crappy burns are honestly a thing of the past, from the research I have seen unless you have a particularly old or very used drive.

Knowing how you have it installed will help us to help you trouble shoot. The package managers might be running for security updates in the background, and that may be related to the software issue but those shouldn't take more than an hour or so at the most (obviously depending on your internet).

---

### Post by wardD on 2010-01-05
hmmm, the disk seems to work.

 I originally tried to do a side by side install, I didn't pay strict attention to the partitioning section, and may have screwed up their  since it dint load,  but, then thought to hell with it,go for the complete install.  it installed so....

  any idea,s on what other download managers might be runnig. the only thing on this computer is an avi file and ubuntu?



  ward.

---

### Post by mick222 on 2010-01-05
do as howfield says that should allow you to download using synaptic .
Opening synaptic and choosing fix broken packages from edit menu should also fix it . Then if you haven't done so already Enable the mediabuntu repositories by running the following code in terminal just copy paste into terminal.


```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```



 Then install  Ubuntu restricted extras.This will install restricted codecs for audio video , adobe flash and java.

---

### Post by wardD on 2010-01-05
file check say,s integrety test could not be performed.    ??  bad burn?


 I will try to download it using this machine and reburn the .iso file  and use the provided burner soft ware. it did burn the avi file so that works.



 natravis, thanks for the heads up on the check disk thing.   Ill get on the new image and let you know what transpires.

    regards.   ward.

---

### Post by Tyke91 on 2010-01-05
> **wardD said:**
> file check say,s integrety test could not be performed.    ??  bad burn?


 I will try to download it using this machine and reburn the .iso file  and use the provided burner soft ware. it did burn the avi file so that works.



 natravis, thanks for the heads up on the check disk thing.   Ill get on the new image and let you know what transpires.

    regards.   ward.

use the slowest settings when you burn the CD, for some reason burning it quickly can cause problems on older machines.

if the problem persists, reboot into the recovery console (you can choose it from grub) and run fsck

---

### Post by mick222 on 2010-01-05
if you run dpkg your files should update maybe saving you the reinstall

---

### Post by wardD on 2010-01-05
ok, reburnt the disk at 4x speed, did a clean install and it seems to be working better.

 tried to do the updates but it warped out my computer.  maybe too many at one time, theirs like a 160 some odd.

 well guess i will go play around and see what troubles i run into, cheers all.

---

### Post by Bartender on 2010-01-05
A typical newb mistake is to have Update Manager or Add/Remove Packages up at the same time as Synaptic.  You can only have one application running if you want to get updates.  It makes sense if you think about it.

I believe they've tried to fix this with 9.10 by putting all these applications under one roof - the Ubuntu Store.

---

### Post by wardD on 2010-01-12
thanks for the replies.


    so it turned out the cd copy was bad, and its kinda looking like the hdd may be pooched.

at any rate I sparked up one of my older rigs  that  just exceedes min  requirments popped in a DVD reader and well were up and running.   

guess I will plug in a mass storage device and and start playin with some of the software and applications this os comes with.   again, thanks for the replies and Im sure we will be chating soon.


      regards,   ward.

---

### Post by wardD on 2010-01-13
ok, well that was a good time.  every thing seems to work so far.  its a triffle slow, will have to bump the ram, but thats no biggie.
 
 I will mark this thread as solved and start a new one when I run into problems.
 
     thanks all.    ward

---

