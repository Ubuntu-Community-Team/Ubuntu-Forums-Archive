---
title: "Installation Walkthrough For Beginners"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by tbhesswebber on 2011-03-10
I need to install Ubuntu onto a computer with no internet.  I have been downloading things via a laptop, transferring them to an external, and then using the external to run the installation.

I was wondering if somebody could walk me through the installation and booting processes in laymen's terms.

Thanks tons.

---

### Post by Ben Page on 2011-03-10
Ubuntu is meant to be installed on a PC with internet connection. Built in package managers and Software Center are highly dependant on internet connection. It's recommended that you provide internet access for your Ubuntu PC.

Nevertheless, you can install Ubuntu on a PC without an Internet connection. You can order a Live CD if you can't download it (but I read you got that sorted). Install from the CD as usual (burn the downloaded .iso file of Ubuntu), follow the on screen instructions, thy are written in layman's terms. Now, it depends what is this PC going to be used for and does it contain the necessary software for those tasks. There are distros made for specific tasks, there is Linux Mint respin of Ubuntu which contains more preinstalled software. You can also take a look at Super OS - which is basically Ubuntu loaded with various software. This will avoid the need for downloading the software separately. 

Finally, you can hunt down software and install it as you would in Windows, just be sure to get the .deb package (which is basicaky the same thing as the famous .exe file for Windows).

Only thing that you can't do, is to update over the internet, but you can upgrade your Ubuntu, again, via downloaded CD.

For more info, ask more specific questions ;)

---

### Post by tbhesswebber on 2011-03-10
When I plug in the hdd, the auto-run screen pops up, asking what I would like to do with the hdd.  I select "run the program"

A message pops up saying "There is no disk in the drive.  Please insert a disk into the drive ?????L?????????..."

If I hit continue enough, it says "Exception Processing Message c0000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c"

After hitting continue another like 20 times, it take me to a menu with a "Demo and full installation" Button.

None of these things happened when I installed it on my laptop with internet.

---

### Post by Ben Page on 2011-03-10
I guess this is going to be harder than I thought.

You downloaded Ubuntu from Ubuntu.com site, right? 

You got a file that has an extension ".iso" e.g. Ubuntu_live_CD.iso, right? 

You have burned this .iso file as image via your burning software to a blank CD. Right?

You have inserted this CD into the CD/DVD drive in your PC and set it up to boot from the CD, right?

You have followed the on screen instructions, right?

When your answer to these questions = "Yes", you will have Ubuntu PC set up and ready to run.

You are trying to install Ubuntu inside Windows (what is called a WUBI install) via external HDD, I presume, this can be complicated for beginners, follow the instructions above.

---

### Post by tbhesswebber on 2011-03-10
Is there a reason that this would work on all of my computers with internet, but not on my one without internet?

---

### Post by ajgreeny on 2011-03-10
Early on in the installation make sure you have not checked the two options **"Download updates at install"** and **"Install third party applications"**.

I may have slightly misworded those options, but it will be clear when you get to the page, what I am talking about.

---

### Post by mastablasta on 2011-03-10
> **tbhesswebber said:**
> Is there a reason that this would work on all of my computers with internet, but not on my one without internet?
 
 
my guess is because you were using Wubi to install and were downloading the OS as you were installing it in a virutal file. kind of like those online games installers.
 
propper way was mentiuoned above and it is with a CD or USB drive (you need 1Gb USB drive). you could also probably get away with a hard drive but it would have to be a bootable drive.

---

### Post by I2k4 on 2011-03-11
I've used the USB option here - which seems foolproof:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

In your case, you'd want to download the .ISO file for the version you choose and the PenDrive installer to the internet computer, then move them to the non-internet computer, create the LiveUSB from the hard drive on the non-internet computer so it picks up the specifications from the right machine.  The actual installation from LiveUSB goes beyond what I've done - I'm still version shopping from a "Persistent" LIve USB which actuallly functions pretty well..

---

### Post by fabricator4 on 2011-03-11
> **I2k4 said:**
> I've used the USB option here - which seems foolproof:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

In your case, you'd want to download the .ISO file for the version you choose and the PenDrive installer to the internet computer, then move them to the non-internet computer, create the LiveUSB from the hard drive on the non-internet computer so it picks up the specifications from the right machine.

Since tbhesswebber already has an Ubuntu machine the PenDrive installer may not be necessary.  The instructions you pointed to include the Ubuntu version of installing to a "USB stick" and they really are foolproof.  The Startup disk creator hasn't failed for me yet; very nice.

tbhesswebber, just make sure you select the correct target drive for the install ;-)

Chris.

---

