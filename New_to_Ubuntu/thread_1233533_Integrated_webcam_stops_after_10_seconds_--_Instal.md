---
title: "Integrated webcam stops after 10 seconds -- Installing Philips SPC715NC"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by DomNewToLinux on 2009-08-06
Hi, Im a new linux (ubuntu 9.04) user...just switched from Vista to Ubuntu...
Never programmed so I am totally lost, whenever I come across some issues with my HP G60-235. 

The issue is with my webcams...I have a built in webcam, that only works the first 10 seconds I use it everytime after a reboot...so to use it I have to basically reboot my laptop every 15 secs or so.

So I got a Philips **SPC715NC** and tried to install it. I read [http://ubuntuforums.org/showthread.php?t=641006](http://ubuntuforums.org/showthread.php?t=641006) but got totally lost because I just have NO clue what they are talking about. (exept for downloading and "de-tar-ring")

Could anyone please help me with those webcams? Will they work on my machine? 
Thanks a lot in advance!

Thanks for your help! (=
PS-step for step would be great!

---

### Post by DomNewToLinux on 2009-08-10
Ok, I found something about the Philips Cam ([http://ubuntuforums.org/showthread.php?t=641006&highlight=spc715](http://ubuntuforums.org/showthread.php?t=641006&highlight=spc715)) that said they downloaded the latest GSPCA and just followed the instructions in Readme and now the cam works...
 
So I downloaded the latest GSPCA and read through the Readme...unfortunately I really don't know how to do any of what's in the readme! Can you help me, please?! It says:
> 
Well, first you need to compile the driver (see below), then you need to make
sure that the v4l infrastructure is set up and then load the driver. After
you've done that, any v4l enabled application, such as spcaview, gqcam, xawtv,
gnomemeeting, camE etc should work.
Supported kernel versions
=========================
The driver should compile and run successfully against most stable versions of
the official Linux 2.6.x kernel upto version 2.6.11
 
Compiling it
============
The driver module can be built without modifying your kernel source tree.
 
Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.
 
Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.
 
as root
goes to gspcav1 directory and run:
./gspca_build 
 
if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. 			 		


please, what do I have to do? Could you post the commands? Thx
PS-I tried make config but got so lost I just exited the terminal... :confused:

---

### Post by DomNewToLinux on 2009-08-13
Ok just for the record, I give up...apparently none of my 3 external webcams work on my HP G60-235DX under Ubuntu 9.04. I'm guessing that the integrated webcam blocks out the externals...:confused:

---

