---
title: "Upgraded to 10 and now my screen goes blank! Please help!!!!"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Spottydog on 2010-08-20
Hi there:
 
I'm operating a Dell Inspiron 6000. I've been using ubuntu 9.04 and everything was running really well. I had the previous version to that also, and upgraded to 9 no problem.
 
However, after upgrading to the latest version of Linux, my screen slowly fades to a pale ghostly looking white screen. Everything seemed to upload fine, and when you start the computer it looks great - the login screen is there and it all looks beautiful. However, after signing in with my password, the screen just fades away until it looks like smoky white. You cannot see anything, so I am unable to see anything. If I were running Windows, I would do a safe start and try to figure out the problem, but i'm afraid I do not know enough about linux to do this. Any suggestions would be extremely helpful....... please??!!
 
Thanks so much.
 
spottydog

---

### Post by QIII on 2010-08-20
Does your model have an ATI Mobility X300 (or X anything) GPU, or is it newer than that?

---

### Post by Spottydog on 2010-08-20
Hi there - i believe it does have the ATI X300

---

### Post by QIII on 2010-08-20
Did you have the proprietary ATI driver installed before you upgraded?

---

### Post by Spottydog on 2010-08-21
I'm such a newbie at this....I'm sorry. I don't think I did have the proprietory driver installed.  I seem to remember trying to find one quite a long time ago, with no joy.  Because my system had been running so well in Ubuntu 9.?, it did not occur to me that there would be any problems upgrading to 10.4 :(   

It just fades away to a cloudy white-ish screen _after_ I log in.

---

### Post by Spottydog on 2010-08-21
is there any hope do you think?

---

### Post by QIII on 2010-08-21
Always.

I'm going to do some research.  Meanwhile, someone more clever than I may stumble across this thread.

---

### Post by jmfal on 2010-08-21
Hi Spotty

Ubuntu has a recovery mode, restart, get to your boot menu (not bios)

On my pc it is F12, not sure about yours. If your not sure, when you restart and pc/laptop logo comes up press tab key and pc specs will come up, at bottom of screen should say to enter bios/setup press???, and, to enter boot menu press????

Anyway, the boot menu screen will list your kernel,kernel recovery mode,maybe memtest
select recovery mode using up/down arrows on keypad  hit enter to make selection.

window will appear with some options:
1: try to fix broken packages
2:resume boot 
3:low graphics mode
4: i forgot what it is

Try #1(fix broken) , use up/down arrows on keypad to change selection, press enter to make selection

enter username/password if asked, will spew code, may ask if you want to continue

y/n  hit y then enter if you read the code it looks like it`s uninstalling packages, it is because it found something wrong and will attempt to uninstall those packages then reinstall them  

when done will ask for username/password press enter after each entry
after that ,you will see $$ type startx press enter
the fix broken/resume boot window might come up or it may just start to boot, give it a few seconds. if it does nothing restart and let it boot

---

### Post by Spottydog on 2010-08-21
Hi there: first o al I just want to say a great big thank you for trying to help me - I REALLY appreciate it!
 
after several attempts with the different recovery modes, I have at last got a message I think maybe understandable?.  The folowing is displayed:
 
   libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
   mountall: mountall.c:3204: Assertion failed in main: udev_monitor = udev_monitor_
   new_from_netlink(udev "udev")
   init: mountall main process (2573) killed by ABRT signal
   Generalerror monting filesystems.
   A maintenance shell will now be started.
   CONTROL-D wil terminate this shell and reboot the syste.
   [EMAIL="root@myname"]root@myname[/EMAIL]:~# 
 
 
I do not know enough about shell commands.  Is there anyway that I can install a graphics thing that will work, using the shell command?
 
Do youknow??  Thanks if you can offer any advice/help.  I'm reaching the point where I just feel like re-installing 9.04 but I had a big struggle the first timegetting it to read my 360 meg hard drive, I'm loathe to start again. Also, there ARE a few pictures on the hard drive I'd love to try and keep :(  I feel so dumb  :( :(

---

### Post by Spottydog on 2010-08-21
oopps sorry for an typos above - the keyboard on this other computer doesn't work very well!  Moning should, of course, read mounting

---

### Post by Sef on 2010-08-21
> Also, there ARE a few pictures on the hard drive I'd love to try and keep

Often you can access your hard drive through a Live CD.  Try running the one you have and save the pictures to a usb key or external hard drive.

> I'm reaching the point where I just feel like re-installing 9.04 but I had a big struggle the first time getting it to read my 360 meg hard drive, I'm loathe to start again

We have all been there. It's not easy to decide when to keep trying to fix a problem and when to reinstall.  

If you do reinstall 9.04, update to 9.10, then 10.04 before installing any proprietary drivers.  Updating with proprietary drivers often causes problems for many people.

> I feel so dumb

So have we all at times.

---

### Post by BobJam on 2010-08-21
@ Spottydog,

Not necessarily a solution to your woes, but see my thread at [http://ubuntuforums.org/showthread.php?p=9747996#post9747996](http://ubuntuforums.org/showthread.php?p=9747996#post9747996) .

---

### Post by QIII on 2010-08-21
> **Sef said:**
> If you do reinstall 9.04, update to 9.10, then 10.04 before installing any proprietary drivers.  Updating with proprietary drivers often causes problems for many people.

Thanks, Sef.  I asked him about whether he had the proprietary driver installed in one of my posts, but I really didn't make it clear to him why I was asking.  Thanks for adding the detail so he understands why the question was asked.

---

### Post by Spottydog on 2010-08-21
You guys are great and have been so kind to try and help with my problems>  I read with interest all your posts, Bobjam, re 10.04.
 
I've run 9.04 from the live CD. Unfortunately accessing the hard drive reveals none  of the pics or docs I had stored on there.  No matter - it showed that 9:04 was recognizing my large harddrive which was good news for me.  
 
I have downloaded v.10.04 and will try installing it from a USB stick.  I will test it out for a while and see how it works.  failing all else, I'll do what Bobjam did and go back a couple of versions and upgrade until at least 9.10.  I'll decide after I get to that point, whether I'm going to go up one more or stay put!
 
All your posts and advice have been great and I have t say, none of you made me feel like an imbecile or idiot and that's what's so great about these forums.  I love Linux - I have been using it more or less problem free for the past year - nothing too adventurous, just for day to day pc work, and I would never ever go back to windoze.  
 
Can't thank you enough for your help guys!  Oh, and btw, spottydog here is a she not a he!  hehehe  
 
:)

---

