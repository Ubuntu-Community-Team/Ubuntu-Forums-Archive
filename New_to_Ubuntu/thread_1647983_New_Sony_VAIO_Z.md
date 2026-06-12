---
title: "New Sony VAIO Z"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by solor on 2010-12-18
Hi, I've been looking for help for two days now and just can't seem to get any. I have a new Sony VAIO Z13M9E with Windows 7. I want to dual boot with Ubuntu 10.10.

When I put in the Live CD the Ubuntu graphics are messed up. Things on screen are just about readable so I went ahead and installed it. However if I try to boot Ubuntu from Grub all I get is a blank screen. Can anyone please help me?

Thanks.

---

### Post by davidmohammed on 2010-12-18
google search reveals [this]("http://www.adhocism.net/2010/11/installing-ubuntu-10-10-on-sony-vaio-vpc-z13m9eb/").  Looks tricky though for a beginner.

---

### Post by solor on 2010-12-18
Yes I found that too but I'm new to all this and I can't even get into Ubuntu to make the changes this site tells me to.

What is "Ubuntu 10.10 alternate amd64"? I used the normal Ubuntu iso from the official site. If I download this alternate one can I just pop it in to the drive and have it install over the current (normal 10.10) Ubuntu?

Thanks.

---

### Post by davidmohammed on 2010-12-18
the alternate 64 image is just the standard debian installer for the 64bit version of ubuntu - 

basically a very customisable way of installing ubuntu.  Looks complicated for beginners.  The standard installer for ubuntu hides much of this complexity.  However for your laptop, looks like you will struggle to install using the standard installer - especially since you need to install customized linux kernels.

Yes - just pop in the alternate CD and install - look very carefully at the questions posed since you could overwrite your windows 7 install.

I presume you've got a good backup of your entire laptop before you start all of this?

---

### Post by solor on 2010-12-18
Ok I'll give that a go, I'm downloading the Alternate iso now. 

yes I've got a recovery disk ready just in case. The laptop also has a recovery partition if needed. 

Thanks, I'll give feedback (or ask more questions) after the install.

: )

---

### Post by solor on 2010-12-18
Right I've tried to install using the alternate CD but I get the same result. A blank screen when I try to boot Ubuntu. 

I'm having no luck here. Does anyone know what options I need to pick during the install?
I found this video ([http://www.youtube.com/watch?v=_rpHqFPglz0&feature=related](http://www.youtube.com/watch?v=_rpHqFPglz0&feature=related)) which shows how to install using the cd but it didn't help. It installed fine but it failed to install GRUB. So now I'm looking at a screen with text input. It reads "Minimal BASH-like line editing is supported. For the first word TAB lists possible command completions." and "grub>"

: /

---

### Post by davidmohammed on 2010-12-18
did you add the boot options?

single nomodeset i8042.reset i8042.nomux i8042.nopnp i8042.noloop

then when prompted select the failsafe X option

---

### Post by davidmohammed on 2010-12-18
... I've no experience with the alternate CD install myself.

however - what happens if you add those boot options in my post above to the live CD?

i.e. boot the live CD  press spacebar when the icon is displayed at the bottom of the screen.  Then press F6 (I think) to edit the boot string.  Remove quiet splash and add those boot options.

If you can boot to the desktop - use this [guide]("https://help.ubuntu.com/community/Grub2") on how to reinstall grub 2

---

### Post by solor on 2010-12-18
ok I've got a clean install back on the drive. (windows 7 partition, /, /home and swap partitions.)

I poped the live cd in and removed the quiet splash and put in the commands you said to. I'm now at a Recovery Menu. The options available are:
Resume- resume normal boot
Clean- try to make free space
dpkg- repair broken packages
failsafex- run in failsafe graphic mode
grub- update grub bootloader
netroot- drop to root shell promt with networking
root- drop to root shell promt

Should I choose "Resume"?

---

### Post by davidmohammed on 2010-12-18
in that blog - the guy used "failsafe" - suggest you try the same.

---

### Post by solor on 2010-12-18
Awesome! OK I'm Finally looking at an Ubuntu desktop. It's running in a low graphic safe mode.

Following the instructions on the blog I've download the packages and moved them to the vaio z. I've opened up a terminal window. The blog states:
[INDENT]
[LIST]
[*]I opened a terminal and (after changing to the download directory) typed:
[/LIST]
 
sudo -i
dpkg -i *.deb
update-initramfs -u -k 2.6.37-6-vaioz
update-initramfs -u -k 2.6.28.10-vaioz
update-grub
[/INDENT]How do I "change to the download directory"? I'm not to familiar with terminal commands. The downloaded files are sitting in the home/downloads folder.


Thanks.

---

### Post by davidmohammed on 2010-12-18
try 

cd Downloads

the type

ls

this should list the contents of the Downloads directory and also show that it can see the files you have downloaded.

---

### Post by solor on 2010-12-18
Ok that works but when I use [FONT=monospace]"[/FONT]sudo -i" I can no longer see the downloads folder or  it contents. when I dont use "sudo -i" and try to run "dpkg -i *.deb" terminal tells me "requested operations require superuser privileges".

What does that mean?

---

### Post by davidmohammed on 2010-12-18
sudo -i is a short way of making you a "root" user.

To find out where you are type

pwd

for example

/root

then cd to your Downloads folder

e.g.

cd /home/<username>/Downloads


if you run dpkg on its own then this will fail - you have to be root.

You can however do this

sudo dpkg ...

this will run the command as root - this is much safer to do.

sudo dpkg -i *.deb
sudo update-initramfs -u -k 2.6.37-6-vaioz
sudo update-initramfs -u -k 2.6.28.10-vaioz
sudo update-grub

---

### Post by solor on 2010-12-18
Ok I've done everything in the list.

I really need help on this last bit. I'm trying to stop gdm so that I can install the NVIDA driver. I use "sudo service gdm stop" but all I get back is "stop: Unknown instance:". How do I stop gdm???

---

### Post by solor on 2010-12-19
Can anyone help stop gdm? Bump.

---

### Post by davidmohammed on 2010-12-19
You normally would only need to stop gdm if you are manually installing the nvidia driver.  

The standard recommended way is to connect your computer via ethernet to the internet.  Then use System - Administration - Hardware Drivers.  Enable the recommended nvidia driver from there.  That will download and install the driver for you.

However saying all that - the error message means that GDM isnt running - you you could just go ahead and install the nvidia driver manually.

---

