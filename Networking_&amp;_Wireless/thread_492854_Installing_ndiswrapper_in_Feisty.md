---
title: "Installing ndiswrapper in Feisty"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by slam5050 on 2007-07-05
I've tried several websites's instructions and I'm still having trouble installing ndiswrapper 1.47. I'm installing from source and so far have managed to extract the tarbell file. However I receive errors when I get the step of using the make commands?

---

### Post by sj3fk3 on 2007-07-05
> **slam5050 said:**
> I've tried several websites's instructions and I'm still having trouble installing ndiswrapper 1.47. I'm installing from source and so far have managed to extract the tarbell file. However I receive errors when I get the step of using the make commands?

Maybe this is a silly question, but why not use the packaged ndiswrapper? e.a. apt-get install ndiswrapper?

---

### Post by newbun on 2007-07-05
I know what you mean ;-(  Anyone who is new to Ubuntu/Linux will find it's a bit economical with it's requests as to what it wants....AND, where to get it.  I've already asked a similar question to yours, and although the forumers have tried to help, I find I'm still in the dark.  The other operating system (which most of us are trying to migrate from) at least is a bit more 'vocal' in it's wants and needs.

I hope someone (and I know, they're out there) answers your question - as it will help me, as well

good luck.

---

### Post by slam5050 on 2007-07-05
yes I am a linux newbie but anyway

make distclean command works fine, however doing the "make" command and I receive these errors at the end 

make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/slam5050/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2


Also the packaged ndiswrapper do I have to get this from the live cd?

---

### Post by sj3fk3 on 2007-07-05
> **slam5050 said:**
> yes I am a linux newbie but anyway

make distclean command works fine, however doing the ' make ' command and I receive these errors at the end 

make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/slam5050/Desktop/ndiswrapper-1.47/utils'
make: *** [all] Error 2


Also the packaged ndiswrapper do I have to get this from the live cd?

Aah, I see, you sound not even try to build it from source. Ubuntu has near perfect package management and has done all that already for ya. 

Just type sudo apt-get update and then sudo apt-cache search ndiswrapper, you will find the right ndis packages there. You might need the CD to install the files (if you don't have other means to setup a (wired) network.

btw
Are you sure you need ndis? Maybe you driver is already supported. dmes | grep wireless might tell you something.

---

### Post by slam5050 on 2007-07-05
Yes I need ndiswrapper even though i'm using a Belkin Wireless G USB NIC. I does detect my network but when I try to connect to it I get this error message

"The requested wireless network requires security capabilites unsupported by your hardware"

I posted a thread to this forum about this about a week ago and someone's suggestion was to do with the NIC's drivers.

---

### Post by sj3fk3 on 2007-07-05
> **slam5050 said:**
> Yes I need ndiswrapper even though i'm using a Belkin Wireless G USB NIC. I does detect my network but when I try to connect to it I get this error message

"The requested wireless network requires security capabilites unsupported by your hardware"

I posted a thread to this forum about this about a week ago and someone's suggestion was to do with the NIC's drivers.

Still output from dmesg and iwconfig would help.

---

### Post by kevdog on 2007-07-05
You need the build-essential package installed.

If you have a wired connection to internet go to step #4, if not, start at step #1.  We are going to type #2-#4 commands at command prompt
#1. Put ubuntu installation cd into driver, wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

You should now be able to compile the source files!

---

### Post by slam5050 on 2007-07-05
Ok when I type the "sudo apt-cdrom add" command I receive this: 

slam5050@slam5050-desktop:~$  sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter              ((I pressed enter))
Mounting CD-ROM...
E: Failed to mount the cdrom.

The CD is defantly in the drive as Ubuntu reconises it, and I know that the CD is not damaged.

---

### Post by fredj on 2007-07-05
Try putting the Cd in the drive first then issue the command to add the CD. If you keep getting the CD error
then there must be something wrong with your Cd. It works on my system.

---

### Post by slam5050 on 2007-07-06
Ok I will try to burn anouther CD or see if there is a way of me setting up a wired connection.

---

