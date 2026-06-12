---
title: "Intel 536"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by sancho on 2005-04-18
Hey.  
Has anybody managed to get a Intel 536 working in hedgehog?

I've read through prior forum posts and tried all the suggestions for warty.  I've also read Intels documentation, but it didn't seem to get me anywhere either.  

heres the error i'm getting :
ERROR: write() in Modem::writeLine faile
(only thing i see about that on the net is in a source file that say  "// TODO do something meaningful with the error code (or ignore it)" which of course isn't useful at all)   

Now, here is what i've tried :
installed build essential, gcc, kernel source and headers....
then tried installing from source.   
it couldn't finish the make but i believe the error i was getting was simply because it couldn't put together the right startup script for the system.   
I followed intels step by step guide....
   0.  log in as root.
   1.  insmod -f Intel536.o (Intel536.ko for kernel 2.6)
   2. you can start "hamregistry &" at this point if you wish.
   3.  rm /dev/536ep
   4.  mknod /dev/536ep c 240 1   (note "240" is the default, if it does not 
       work see what /proc/devices says 536ep's major number is)
   5.  ln -s /dev/536ep /dev/modem
   6.  start a comm application like minicom and use the modem.
   7.  see section 3 (International Users) for info on setting the correct 
       country settings.

I've also tried installing some RPM's from intels site using alien.  same error.  

Finally i tried the sl-modem drivers from .debs  as per someone suggested.   No luck with that either.  

Tried wxdial, pon, and kpp.   

I've just tired several different things.  And, I've been working on this for a few days now and its starting to drive me up the wall.  


Has anybody got anybody got any suggestions?  Or has anybody got a 536 working in headgehog; if so please post me a simple walkthrough of what you did.  

almost forgot to mention that this is kubuntu with stock kernel of 2.6.10-5-386 if that helps anybody....

Thanks for the help.

---

### Post by az on 2005-04-18
"Finally i tried the sl-modem drivers from .debs as per someone suggested. No luck with that either"

What errors did you get?  Did youinstall the right packages for your modem?  Why did you install the kernel-source as well as the headers?

In a console, do 
sudo tail -f /var/log/messages
and in another console, load the modules you made (it they are not loaded)

do sudo pppconfig and enter all the information.  Make your conncectin name "provider" and do not forget to save before you quit.
do
sudo pon and see what is shown in the other console.

Post it here, if you can...

---

### Post by sancho on 2005-04-18
Hey man.

Sorry my first post wasn't thorough enough.   Just did a fresh install of kubuntu once again.   I'm going to try building the drivers from source again, and this time i will post all my messages.  I downloaded the uncompiled drivers from intel (intel-536ep-4.69.tgz) because they don't have a precompiled binary for ubuntu or debian.   

I did install the kernel source and headers before trying to compile the drivers, b/c if you don't it errors out, as far as i know whenever you build most standard modules from source to insert into the kernel you need the source and headers installed so it can drop them in the proper /lib/modules folder and do the proper linking.  I could be wrong about this assumption though, i dunno.  

I extraced them.  
then did the following:
make clean
make 536
everything appears fine.  the warngings i recieved during make 536 are below.

----
/home/owner/intel-536EP-2.56.76.0/coredrv/coredrv.c:756: warning: initialization from incompatible pointer type
/home/owner/intel-536EP-2.56.76.0/coredrv/coredrv.c:757: warning: initialization from incompatible pointer type
/home/owner/intel-536EP-2.56.76.0/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/home/owner/intel-536EP-2.56.76.0/coredrv/coredrv.c:879: warning: function declaration isn't a prototype
include/linux/module.h: At top level:
/home/owner/intel-536EP-2.56.76.0/coredrv/coredrv.c:286: warning: `power_callback' defined but not used
/home/owner/intel-536EP-2.56.76.0/coredrv/softserial.c:125: warning: assignment from incompatible pointer type
  LD [M]  /home/owner/intel-536EP-2.56.76.0/coredrv/Intel536.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/owner/intel-536EP-2.56.76.0/coredrv/.536core.lib.cmd for /home/owner/intel-536EP-2.56.76.0/coredrv/536core.lib
------
make install
 give me this
-------
rm -f /etc/hamregistry.bin
bash Intel536_inst
running kernel 2.6.10-5-386
installing hamregistry, used for persistant storage
installing Intel536 driver
unknown distribution. no boot scripts installed
make: *** [install] Error 1
--------
make -d install i get this as the last few lines..
-------
installing Intel536 driver
unknown distribution. no boot scripts installed
Got a SIGCHLD; 1 unreaped children.
Reaping losing child 0x08075f18 PID 8882
make: *** [install] Error 1
Removing child 0x08075f18 PID 8882 from chain.
-----------

so i think the errors there are only because of boot script issues.   



Now onto the module inserting.  
after the build it is not inserted into the kerenl.   
however a ls /lib/modules/2.6.10-5-386/kernel/drivers/char/In*
shows /lib/modules/2.6.10-5-386/kernel/drivers/char/Intel536.ko .

So it appears that the module was built but not inserted.  then i do a 
insmod -f Intel536.ko
an lsmod shows the module and a tail /var/log/messages/ says Intel536: module license 'Proprietary' taints kernel.
then i do a hamregistry &
it starts and shows up in ps aux
these are the messages i get...
root@ubuntu:/home/owner/intel-536EP-2.56.76.0 # hamregistry &
no registry file, making default

That appears fine.  Onto step 3.  
 rm /dev/536ep
no errors.  the file was never there to begin with, but i did the command anyways just to be sure.

Step 4....
mknod /dev/536ep c 240 1 
i checked cat /proc/devices and the 240 info (whatever that actually means matches up).
no errors and nothing weird in /var/log/messages
 
Step 5...
ln -s /dev/536ep /dev/modem
again no errors and a ls -lha reveals a proper symlink.  

Step 6...
sudo pppconfig and pon testing
ran through all the standard settings.  
pppconfig did not find the port for the modem automatically. so i typed /dev/modem
this should work, right?
saved the settings and exited.  
a vim of /etc/ppp/peers/provider revealed what seem to be proper settings.
still nothing in messages.  

pon 
heres the messages 
-----
root@ubuntu:/home/owner/intel-536EP-2.56.76.0 # hamregistry: packet 1 unknown
-----
a tail /var/log/messages shows the following
-----
Apr 18 16:29:57 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Apr 18 16:29:57 localhost kernel: PPP generic driver version 2.4.2
Apr 18 16:29:57 localhost pppd[9087]: pppd 2.4.2 started by root, uid 0
Apr 18 16:29:57 localhost kernel: ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
Apr 18 16:29:58 localhost chat[9088]: abort on (BUSY)
Apr 18 16:29:58 localhost chat[9088]: abort on (NO CARRIER)
Apr 18 16:29:58 localhost chat[9088]: abort on (VOICE)
Apr 18 16:29:58 localhost chat[9088]: abort on (NO DIALTONE)
Apr 18 16:29:58 localhost chat[9088]: abort on (NO DIAL TONE)
Apr 18 16:29:58 localhost chat[9088]: abort on (NO ANSWER)
Apr 18 16:29:58 localhost chat[9088]: abort on (DELAYED)
Apr 18 16:29:58 localhost chat[9088]: send (ATZ^M)
Apr 18 16:29:58 localhost chat[9088]:  -- write failed: Bad address
Apr 18 16:29:59 localhost pppd[9087]: Exit.
------------------------------


Is there anyway to run pon with a more verbose output?  I'm not familar with that application.


I would really like to get this problem fixed, its making me pull my hair out.  I'm not brand new to linux, but i'm new to the ppp and dial up stuff under linux, so any help would be greatly appreciated.

---

### Post by sancho on 2005-04-18
hunting for help on my own problem.  here are some links that might be helpful for to me and others in the same boat in the future.

[http://forums.gentoo.org/viewtopic.php?t=203605&highlight=536ep](http://forums.gentoo.org/viewtopic.php?t=203605&highlight=536ep)

[http://kerneltrap.org/node/2998](http://kerneltrap.org/node/2998)  -- very bottom talks about debian distros.  

[http://ubuntuforums.org/archive/index.php/t-11851.html](http://ubuntuforums.org/archive/index.php/t-11851.html)  --athlon 64 info.  



[http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)    --damn it.   if this is the final answer i will be upset.  possibly need patch for all 2.6.10 kernels.  can anybody confirm this?

---

### Post by sancho on 2005-04-18
also.  this must be new, or i must have been blind the past few days.  

there is a wiki walthrough.    Ugh....

[http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto)

I'll try this in a few days and if i still have problems i will post back.  

Sorry for posting questions about something in a walkthrough.  I just never saw it.  And the apparent kernel incompatibily thing really through me (and by the looks of other forums, tons of others) off.

---

### Post by az on 2005-04-19
The sl-modem drivers cover your modem.  They should work.

---

### Post by sancho on 2005-04-29
Forgot to post back....

The walkthrough on the wiki solved my problem.   Feel free to mark this thread solved or close it.  

Thanks for all your help.

---

