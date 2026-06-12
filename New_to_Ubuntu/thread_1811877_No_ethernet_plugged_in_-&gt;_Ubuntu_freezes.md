---
title: "No ethernet plugged in -&gt; Ubuntu freezes"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by b1gag3 on 2011-07-25
Hi there,

I got an issue. This problem was already postet here: [http://ubuntuforums.org/showthread.php?t=1805746&page=7](http://ubuntuforums.org/showthread.php?t=1805746&page=7)
But let me explain; I got a Acer Aspire One Netbook and running ubuntu 11.04 and windows 7 on it. I installed ubuntu with a usbstick and wireless lan. Don't know its maybe a reason. The netbook uses a shared memory graphic card: ATI HD 6250. 
Now the problem, everytime I try to login without a plugged ethernet cable unbuntu freezes after 5-10seconds. If I login with a plugged cable and unplug it afterwards. ubuntu freezes after 3-60 seconds. If the wireless lan is turned off nothing happens. If its turned on after login, you got 3-60 seconds till ubuntu freezes.
I tried to update the kernel to followed versions: 2.6.38-8, 2.6.38-10, 2.6.38-11.47. Currently ubuntu is running with 2.6.38-11.47.

I'll attach a zip file with two syslogs. One with booting without cable and the otherone while unplug it while logged in.

If you need more information just ask. Any help is appreciated

b1gag3

---

### Post by Noncon on 2011-07-25
Any option in the BIOS to turn off the LAN port?  Most desktop units have this option, not sure about notebooks. 

KJ

---

### Post by b1gag3 on 2011-07-25
no just an option for boot on lan.

---

### Post by ajgreeny on 2011-07-25
You could try editing your */etc/network/interfaces* file, if it is like mine,  and commenting out the **lo auto** line
```
# auto lo
iface lo inet loopback
```just in case it is the network seeking but failing that is causing the problem.  If it is no help, just change it back.

---

### Post by b1gag3 on 2011-07-25
I tried, but ubuntu freezes again after log in. :/

---

### Post by anewguy on 2011-07-25
Okay, first off let me say I didn't come up with this information - I'm just passing it along.

There have been 2 similar threads in the last week, once exactly like yours.

The first thing to do is boot with the LAN cable plugged in, then when you click your userid but before you enter your password, look on the bottom line for "Sessions".  Click this and choose Ubuntu Classic.  This will set your default login to the Classic (Gnome) desktop, and not to the new (Unity) delivered in 11.04.

Now you should be able to shutdown, unplug the LAN cable, the power up and boot fine without the cable.  This is a work-around more than a fix.  

One of the posters in the other thread deleted their newer kernels and supposedly went back 2 kernels releases - I'm not sure how you could do that if it's a fresh install.  Supposedly a later kernel update will fix the problem.

There are many threads about this on the net, including launchpad bug reports.

Until such time as a kernel update or driver update is delivered which allows people to boot into Unity without these hangs, you may want to consider just staying either with 10.04 - the latest long term support release, or maybe 10.10.  I know 11.04 delivers more than just Unity, but since it isn't a long term support release, any patches that might be needed and apply are probably being release for 10.04 and 10.10 as well (some will be product release specific and thereby not apply to those releases).

---

### Post by b1gag3 on 2011-07-26
Thank you for your detailed answer.

I should just change the default "Session" to Ubuntu Classic, then not sign in and reboot? Or should I log in and then shutdown? Because I'm at the moment not able to try your workaround... But I know, that I even cann't sign with Ubuntu Classic without plugged ethernet cable.

Yes I read some of these threads and tried the solutions/work-arounds. At some launchpad-reports I read about kernel-releases that should fix the problem, so I already up- and downgraded it a lot. But nothing works so far :/ For the moment I'll try to use 11.04, maybe some one got an idea. But if this takes too much time, I'll downgrade to 10.04. 

Thank you.

Edit: Maybe a solution is found here [http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)
> **zzarko said:**
> **1. Freezing after login (with unplugged network cable)**. This is caused by wireless driver. Easy fix is to make network boot as a first option in BIOS (hold F2 after reboot).

---

### Post by anewguy on 2011-07-26
Plug cable in, boot Ubuntu, select userid, select session type as Ubuntu Classic, enter password, let Ubuntu come the rest of the way up to your desktop.  Then shutdown, unplug the cable and leave it unplugged and reboot Ubuntu, just log in, and see what happens.

As I expressed in the other post but it was ignored, there are also some video cards and drivers that can cause this problem until options are put on the boot line.  But for now, just get the above to work.  We can try video driver stuff afterword to see if it allows you to boot to Unity with no cable.

---

### Post by b1gag3 on 2011-07-26
Hi anewguy,

thanks a lot for the hint but I guess I got a solution. In my last post I quoted a part of **zzarko'**s [**Acer Aspire One 722 Ubuntu 11.04 fixes**]("http://ubuntuforums.org/showthread.php?t=1811178"). Just changing the boot options seems to resolve the problem. At my first login firefox got no internet access but I was able to sign in and load unity. A reboot later everything works. Cross the fingers that it lasts :)

Again thanks a lot for your help.

b1gag3 | Chris

---

### Post by anewguy on 2011-07-26
> **b1gag3 said:**
> Hi anewguy,

thanks a lot for the hint but I guess I got a solution. In my last post I quoted a part of **zzarko'**s [**Acer Aspire One 722 Ubuntu 11.04 fixes**]("http://ubuntuforums.org/showthread.php?t=1811178"). Just changing the boot options seems to resolve the problem. At my first login firefox got no internet access but I was able to sign in and load unity. A reboot later everything works. Cross the fingers that it lasts :)

Again thanks a lot for your help.

b1gag3 | Chris

Glad you found a solution that worked for you!  I know someone suggested this same option in the other thread but it was ignored.

Good work!
Dave;)

---

### Post by Wim Sturkenboom on 2011-07-27
Great to hear. I've followed this thread to see what came out.

Please mark your thread as solved using the thread tools just above the first post.

---

### Post by b1gag3 on 2011-07-27
Done :)

---

