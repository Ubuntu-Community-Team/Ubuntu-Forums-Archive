---
title: "I/O Error Boot CD cannot be read?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Rigorous on 2009-04-04
Hello,

I'm trying to install ubuntu 8.10. I burned it on my cd at the slowest speed possible and I booted my computer to the CD. I got the the Menu with all the options such as install, etc. When I went down to install and hit enter it tried to read the CD and it gave me an error similar to this: I/O Error Boot CD cannot be read.

---

### Post by linuxisevolution on 2009-04-04
> **Rigorous said:**
> Hello,

I'm trying to install ubuntu 8.10. I burned it on my cd at the slowest speed possible and I booted my computer to the CD. I got the the Menu with all the options such as install, etc. When I went down to install and hit enter it tried to read the CD and it gave me an error similar to this: I/O Error Boot CD cannot be read.

The disk is most likely scratched or your cd drive is having trouble for some reason...

---

### Post by Rigorous on 2009-04-04
Its a brand new CD and I don't think anything is wrong with my drive because I tried playing different CDs and burning it to different CDs.

---

### Post by Peter09 on 2009-04-04
Saving DATA to a CD rather than say a photo is very dependent on the quality of the burn and the CD itself. A single data bit dropped will stop the thing working. Its worth trying another CD.

---

### Post by Rigorous on 2009-04-04
> **Peter09 said:**
> Saving DATA to a CD rather than say a photo is very dependent on the quality of the burn and the CD itself. A single data bit dropped will stop the thing working. Its worth trying another CD.

I went through 3 CDs already :p

I will try again.

---

### Post by Peter09 on 2009-04-04
Are you getting the same error with all CD's - how many CD drives have you on the machine?

---

### Post by Rigorous on 2009-04-04
> **Peter09 said:**
> Are you getting the same error with all CD's - how many CD drives have you on the machine?

Sorry for the late response, I have one CD drive and i am getting the same error with ALL!

ITS DRIVING ME CRAZY! 

Ermm.. sorry.

---

### Post by Peter09 on 2009-04-04
What is the spec for your computer - I understand that there is a minority of CD drives / Mother boards that have problems in this area.

---

### Post by Rigorous on 2009-04-04
> **Peter09 said:**
> What is the spec for your computer - I understand that there is a minority of CD drives / Mother boards that have problems in this area.

Specs are:
Dell Inspiron 530s
Intel Pentium Dual CPU E2160 @1.80ghz
2GBs of RAM
About 260GB of free space on my hd

EDIT:

Intel G33/G31 Express Chipset Family

---

### Post by Peter09 on 2009-04-04
Well here is a first`try

[http://www.linuxforums.org/forum/peripherals-hardware/115615-solved-dell-inspiron-530-ubuntu-install.html](http://www.linuxforums.org/forum/peripherals-hardware/115615-solved-dell-inspiron-530-ubuntu-install.html)

---

### Post by Rigorous on 2009-04-04
change your hard disc mode from IDE to RAID?

Huh.. how do i enter bios exactly?

---

### Post by nightshade209 on 2009-04-04
> **Rigorous said:**
> Hello,

I'm trying to install ubuntu 8.10. I burned it on my cd at the slowest speed possible and I booted my computer to the CD. I got the the Menu with all the options such as install, etc. When I went down to install and hit enter it tried to read the CD and it gave me an error similar to this: I/O Error Boot CD cannot be read.

Try downloading the .iso again. The one you downloaded/got might have been corrupted or something.

---

### Post by Rigorous on 2009-04-04
> **nightshade209 said:**
> Try downloading the .iso again. The one you downloaded/got might have been corrupted or something.

I checked the iso using the hash thing and compared the two and it was fine.

---

### Post by Peter09 on 2009-04-04
Entering your BIOS is norally by pressing a key (often DEL) very early in the boot sequence. It should tell you which key as you are booting the machine.

This Bug should have been fixed - what version of Ubuntu are you trying to install?

---

### Post by Rigorous on 2009-04-04
> **Peter09 said:**
> Entering your BIOS is norally by pressing a key (often DEL) very early in the boot sequence. It should tell you which key as you are booting the machine.

This Bug should have been fixed - what version of Ubuntu are you trying to install?

8.10 desktop i386

---

### Post by Cresho on 2009-04-04
Dell is notorious for providing bad ram.  I know this because I change many rams on any type of dell more than any other system.

for your cd burning issue, I expirienced the same thing.  I always wondered why my jpegs where corrupt on some files in a burned cd until I insalled ubuntu.

It took 3 brands of cd's and  4 burners...I think its right...to get the correct combination to burn an error free cd.

Remember there are about 3 main technologies working here for the cd drive itself and also many types of chemicals used to have a cd made.  Anything can go wrong.

You need to do what I did and plus don't burn on a dell....I'm not joking.  Stop fiddling with settings, this won't help either.

If you decide to give up on ubuntu, you will never know if you have a good cd drive and cd media brand combination.  Your problem is for real.

---

### Post by Rigorous on 2009-04-04
> **Cresho said:**
> Dell is notorious for providing bad ram.  I know this because I change many rams on any type of dell more than any other system.

for your cd burning issue, I expirienced the same thing.  I always wondered why my jpegs where corrupt on some files in a burned cd until I insalled ubuntu.

It took 3 brands of cd's and  4 burners...I think its right...to get the correct combination to burn an error free cd.

Remember there are about 3 main technologies working here for the cd drive itself and also many types of chemicals used to have a cd made.  Anything can go wrong.

You need to do what I did and plus don't burn on a dell....I'm not joking.

I have another desktop, do you advise I download ISO recorder on that one and trying burning it from there?

---

### Post by Peter09 on 2009-04-04
While not strictly correct, I would suggest you download the latest Jaunty release - while it is still under development it is due for release on the 19th of April and it is very stable. They have also fixed a lot of bugs. As you are installing from new you might as well use this, rather than upgrade later. It may also overcome your current problem.

Go here for the download

[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by Rigorous on 2009-04-04
I have decided to download 8.04 LTS and give it a try, I will see how it goes.

---

### Post by Cresho on 2009-04-04
you might want to try using a different type of brand cd's.  THis could also help.  I'm telling you this because The first time I tried installing ubuntu, I went from fujifilm, to no brand name, to tdk, to hp, and now using memorex on a pioneer dvd burner.  I also went from emprex to lg to ...well you get the picture.


I think the best way to install ubuntu is make a bootable thumb drive.  you need expirience for this.  IT's not easy making a thumb drive live cd for the newbie.  The only issue is after installation, removing the thumbdrive ghost from the fstab to unlock that particular usb port. (i had experience with a eee usb not working until i removed it).

Just try and see if it works...burn on slow speed like you been doing.

---

### Post by Rigorous on 2009-04-04
Well i burned a copy of ubuntu on another CD (8.10 again) and it gave me the same error again so i changed my Hard drive settings from IDE to RAID and now i get /Casper/Vmlinuz (something like that)

---

### Post by Rigorous on 2009-04-04
Why is ubuntu so annoying to install?

---

### Post by Rigorous on 2009-04-04
Well i burned a copy of ubuntu on another CD (8.10 again) and it gave me the same error again so i changed my Hard drive settings from IDE to RAID and now i get /Casper/Vmlinuz (something like that)

---

### Post by hessczoo on 2009-04-04
Is there any possible way that there is an issue in your ISO? Maybe try redownloading the ISO, in case a bit went missing or something.

---

### Post by Rigorous on 2009-04-04
> **hessczoo said:**
> Is there any possible way that there is an issue in your ISO? Maybe try redownloading the ISO, in case a bit went missing or something.

I Checked it with the original Hash and it was fine...

I just went ahead and requested for the free CD because quiet frankly I'm getting very impatient. I have been at this for 7 hours.

---

### Post by pspsampsp on 2009-04-04
i dont know why your having issues i have the same computer as you (different hd size) and ubuntu works perfect on it for me

---

### Post by Rigorous on 2009-04-04
> **pspsampsp said:**
> i dont know why your having issues i have the same computer as you (different hd size) and ubuntu works perfect on it for me

I'm almost sure its the bad burn.

---

### Post by linuxisevolution on 2009-04-04
I would try a different dvd drive at this point.

I had similar issue. It wouldn't even load the live cd since there was a pin bent on the hard drive. The hard drive was on the same chain as cdrom so it confused the bios as to what drive is master/slave.


Maybe you have similar issue?

---

### Post by Cresho on 2009-04-04
try another cd drive.  Just for your information, all my drives are selected in the bios.  All drives are in cable select mode.  Confusing the drives could also be a problem.  Also, on older systems, if you have the cd and the hardrive on the same ide ribbon on one ide port, you will definelty get problems

It's not that you have issues with ubuntu, your hardware dvd/cd drive could be starting to fail, or you always had a problem with your hardware.

Think about it...you burned a cd with ubuntu files.  you can view it and you can navigate through it just fine.  when trying to install, you get an error in some files.  You have a bad cd copy.

Now lets take pictures or movies:  You don't get this issue because your not reading all the files like when installing an operating system.

Like the guy previously said, try a different iso image.  Could be a bad download too.

---

