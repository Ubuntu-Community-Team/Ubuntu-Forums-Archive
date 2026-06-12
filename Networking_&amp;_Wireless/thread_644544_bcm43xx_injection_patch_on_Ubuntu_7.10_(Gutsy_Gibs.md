---
title: "bcm43xx injection patch on Ubuntu 7.10 (Gutsy Gibson)"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by tetsujin on 2007-12-19
[http://tetsujin.metamudcreations.com/index.php?/archives/92-bcm43xx-injection-patch-on-Ubuntu-7.10-Gutsy-Gibson.html](http://tetsujin.metamudcreations.com/index.php?/archives/92-bcm43xx-injection-patch-on-Ubuntu-7.10-Gutsy-Gibson.html)

This is a step by step tutorial on how to install the bcm43xx injection patch on Ubuntu 7.10.

Special thanks to waraey.

First you will need to install a few packages if you do not have them already, these are: "build-essential", "dpkg-dev" and "linux-kernel-devel".

In your home directory make a temporary directory we can work in:

#mkdir bcm43xxinject
#cd bcm43xxinjinect

You now need a sub directory for our kernel output

#mkdir kernelout
#cp /boot/config-2.6.22-14-generic ./config-2.6.22-14-generic
#cd kernelout
#ln -s ../config-2.6.22-14-generic .config

Now you need to get the kernel source for Gutsy, go get a snack while it downloads, it is about 60 meg.

#cd ../
#apt-get source linux-image-2.6.22-14-generic

get the new patch (updated for the new kernel), and patch the kernel:

#wget -nc [http://tetsujin.metamudcreations.com/dl/files/bcm43xx-injection-linux-2.6.22.patch](http://tetsujin.metamudcreations.com/dl/files/bcm43xx-injection-linux-2.6.22.patch)
#patch -p1 < bcm43xx-injection-linux-2.6.22.patch 

Now we compile the new bcm kernel module

#cd linux-source-2.6.22-2.6.22/

We have to manually change the version info (bug) so we don't get a tainted kernel.

#sudo gedit Makefile

change extraversion from "= 9" to "= -14-generic" . This should be the default but it has not been updated yet. Save and exit then:

#make O=../kernelout outputmakefile
#make O=../kernelout archprepare
#make O=../kernelout modules

That last one will take awhile. Finish your snack you got before, maybe go watch some tv or something industrious like that.

Now with all gods willing this will compile with no errors. 

Remember to always backup...

#cd ..
#mkdir kernelbackup
#cd kernelbackup
#sudo cp /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/*.ko ./

We are finally ready to install our fancy new patched drivers:

#cd ..
#cd kernelout/drivers/net/wireless/bcm43xx/
#sudo cp -dpR *.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/

Next we have to load our new drivers:

#sudo modprobe -r bcm43xx
#sudo modprobe bcm43xx

It should now work and you can hack wireless to your hearts content!

---

### Post by m4ntis on 2008-01-16
Question: When I run the patch it asks me which file to patch? What should I put?

---

### Post by bobbyw on 2008-01-17
> **m4ntis said:**
> Question: When I run the patch it asks me which file to patch? What should I put?

Me also, does anyone have an answer to this?

---

### Post by jwmsalvatruco on 2008-01-17
the patch file needs to be inside the kernel source directory
and run the patch command inside the kernel source directory aswell

---

### Post by iceman0304 on 2008-01-17
Can anyone answer if it will work with WPA & WPA2 security. Using a Compaq Pres.2100 w/ broadcom 4306

---

### Post by bobbyw on 2008-01-17
From what I understand this is asking you to make the folder bcm43xxinject in your home dir. download not only the patch, but also the souce to that dir, make a kernelout dir that doesn't do anything yet....


here is the output I get:

can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-source-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c    2007-10-08 10:14:25.000000000 +1300
|+++ linux-source-2.6.22-bcm43xx-patch/drivers/net/wireless/bcm43xx/bcm43xx_main.c      2007-10-08 10:13:12.000000000 +1300
--------------------------
File to patch: 
[1]+  Stopped                 patch -p1 < bcm43xx-injection-linux-2.6.22.patch
olivia@olivia:~/bcm43xxinject$ 
olivia@olivia:~/bcm43xxinject$ ls
bcm43xx-injection-linux-2.6.22.patch  linux-source-2.6.22_2.6.22-14.47.diff.gz
config-2.6.22-14-generic              linux-source-2.6.22_2.6.22-14.47.dsc
kernelout                             linux-source-2.6.22_2.6.22.orig.tar.gz
linux-source-2.6.22-2.6.22


> **jwmsalvatruco said:**
> the patch file needs to be inside the kernel source directory
and run the patch command inside the kernel source directory aswell

I'm seeing this patch posted in multiple places all with people posting the same thing.... what file do I patch? everyone is getting this error: can't find file to patch at input line 3

---

### Post by dcro2 on 2008-01-21
> **bobbyw said:**
> From what I understand this is asking you to make the folder bcm43xxinject in your home dir. download not only the patch, but also the souce to that dir, make a kernelout dir that doesn't do anything yet....


here is the output I get:

can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-source-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c    2007-10-08 10:14:25.000000000 +1300
|+++ linux-source-2.6.22-bcm43xx-patch/drivers/net/wireless/bcm43xx/bcm43xx_main.c      2007-10-08 10:13:12.000000000 +1300
--------------------------
File to patch: 
[1]+  Stopped                 patch -p1 < bcm43xx-injection-linux-2.6.22.patch
olivia@olivia:~/bcm43xxinject$ 
olivia@olivia:~/bcm43xxinject$ ls
bcm43xx-injection-linux-2.6.22.patch  linux-source-2.6.22_2.6.22-14.47.diff.gz
config-2.6.22-14-generic              linux-source-2.6.22_2.6.22-14.47.dsc
kernelout                             linux-source-2.6.22_2.6.22.orig.tar.gz
**_linux-source-2.6.22-2.6.22_**




I'm seeing this patch posted in multiple places all with people posting the same thing.... what file do I patch? everyone is getting this error: can't find file to patch at input line 3
The 'kernel source directory' would be **linux-source-2.6.22-2.6.22**. Cd into it and try again, worked fine for me.

---

### Post by tennvolsmb on 2008-01-21
I am still trying... and still confused out of my mind.. I've installed the patch but every time i do

```
patch -p1 < bcm43xx-injection-linux-2.6.22.patch
```

im still getting the error... I've tried just about everything possible could anyone give me exact directions please?????? :confused:

---

### Post by Mandle on 2008-02-03
...here is the patch to the original doc.  

Where it Says:

"get the new patch (updated for the new kernel), and patch the kernel:"

Type in 

cd ~/bcm43xxinject/linux-source-2.6.22-2.6.22

Then continue with

#wget -nc [http://tetsujin.metamudcreations.com/uploads/bcm43xx-injection-linux-2.6.22.patch](http://tetsujin.metamudcreations.com/uploads/bcm43xx-injection-linux-2.6.22.patch)
#patch -p1 < bcm43xx-injection-linux-2.6.22.patch

so on and so forth.  pretty much what was said in the post before last.

---

### Post by Shadow's_Knight on 2008-03-28
Great ! It worked for me. Thank you ;)

---

### Post by T3chn0logic on 2008-04-03
I followed the guide to the part that says
Now we compile the new bcm kernel module

#cd linux-source-2.6.22-2.6.22/

Once i reach here, i'm stuck. That command doesn't compile, nor does it even change dir. How do I compile the linux-source-2.6.22-2.6.22 ? :confused:

---

### Post by LinuxGEEK7288 on 2008-04-14
`cd` should change the directory, make sure your not already in the directory after you ran the `patch -p1 < bcm43xx-injection-linux-2.6.22.patch` command. 
However the actual compiling comes later in the TUT, around the part that says  

#make O=../kernelout outputmakefile
#make O=../kernelout archprepare
#make O=../kernelout modules


and don't forget to edit the Makefile before you run thoes

oh and thanks to every one else so far so good :)

---

### Post by greenelephant on 2008-05-09
:@:@:@ i've spent 3 hrs trying to do all this. Can you not just upload the bcm43xx.ko file somewhere here or on a web page so we can download and but into our kernel directory? I've got a 2.6.24-16 kernel running and cant seem to make the ko file which will work. Im in despair. I've got ubuntu .04 and a broadcom bcm4311 wlan card.


thanks

---

