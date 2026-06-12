---
title: "Can Linux help me determine which piece of hardware is failing?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by agm. on 2010-06-28
Hi,

I had a problem [(here)](http://ubuntuforums.org/showthread.php?t=1518542) that I thought originally was a problem with my 9.04 distro due to an update.  After really trying to troubleshoot it over the last 2 days, I have come to think that it is a hardware problem.  I booted into the windows partition and though it lasted significantly longer (around 30 minutes), the computer eventually froze similarly as it did in the 9.04 distro.

So my question is:  What is the best way to attempt to identify the part that is failing?  I have a AMD64 computer that has 1 GB of Ram, but I don't know how to determine if it is the RAM, Chip, or Motherboard (or graphics card?) that is failing.

I personally think it might be the chip, but I am unsure and I do not know how to determine whether it is bad.  Any way to easily check this stuff in Linux?  Any suggestions on troubleshooting hardware components would be greatly appreciated!

Thanks for your help!

---

### Post by darkdragn on 2010-06-28
Well, if you want, you can edit the entries in your grub, deleting quiet and watch the scrolling, to see where it stops... It may just be a hard drive issue. See if you can boot from external media (usb drive, or cd). Or, i have seen in the past, a failing graphics card or wifi card freeze the os, when it goes to load the kernel modules. But if you remove quiet you should see something that will clue you off.

Good luck. (If everything works properly when booting from external media, i would confidently brand it as failing HDD)

---

### Post by philinux on 2010-06-28
> **agm. said:**
> Hi,

I had a problem [(here)](http://ubuntuforums.org/showthread.php?t=1518542) that I thought originally was a problem with my 9.04 distro due to an update.  After really trying to troubleshoot it over the last 2 days, I have come to think that it is a hardware problem.  I booted into the windows partition and though it lasted significantly longer (around 30 minutes), the computer eventually froze similarly as it did in the 9.04 distro.

So my question is:  What is the best way to attempt to identify the part that is failing?  I have a AMD64 computer that has 1 GB of Ram, but I don't know how to determine if it is the RAM, Chip, or Motherboard (or graphics card?) that is failing.

I personally think it might be the chip, but I am unsure and I do not know how to determine whether it is bad.  Any way to easily check this stuff in Linux?  Any suggestions on troubleshooting hardware components would be greatly appreciated!

Thanks for your help!

Well initially I would boot the livecd and run the mem test.

It takes a long time to run. Also look in /var/log/messages see if there are any disk read write errors.

Also take the case panel off and clean any dust out. Could be overheating.

---

### Post by CharlesA on 2010-06-28
You can run memtest86 to test the RAM, but judging from the symptoms, I would guess the machine is overheating.

Verify that all fans are running and that there isn't a load of dust causing heat to build up.

---

### Post by warfacegod on 2010-06-28
A good tool for testing your HDD is:

```
sudo apt-get install gsmartcontrol
```

If you have some hours to kill, I suggest the Extended Test.

---

### Post by agm. on 2010-06-28
Thanks for all the suggestions.  Right now, I will clean off the case as soon as I get home.  Unfortunately, I have tried to boot into live media, and it will not boot into a LiveCD.  

Right now, I won't have a lot of time to kill because the system will hang in less than 5 minutes, so I am trying to do things quickly to see if I can accurately determine the problem.

Ideally I want something that would log the CPU temperature from start-up and continue to log it every 10-20 seconds so that if the computer hangs, I can at least go back and see the logs of what the CPU core temp is reaching.  

There is something like this for windows like [SpeedFan](http://www.almico.com/speedfan.php), but I wasn't sure if there is something like this for Linux as well.  

Thanks again for your suggestions and keep them coming!

---

### Post by oldsoundguy on 2010-06-28
This is what I use cross platform:
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

It has a boatload of testing devices (all run from a Linux based (and somewhat crude) GUI.  But there is a lot of things there such as memory testing, stress tests for the cpu, drive tools as well as a gang of stuff for Windows repair.

it is self booting, so follow the instructions (make the thing on your work computer and haul it home, if allowed.)

---

### Post by agm. on 2010-06-29
Weirdly, I am thinking this is now not a hardware issue.  I am still trying to diagnose the problems, but I ran memtest86 and it passed (I ran it twice).  Additionally, I booted into the windows partition because of the SpeedFan to look at CPU temperatures and it actually now runs Windows for several hours without freezing and the CPU/GPU temperatures are somewhat reasonable at 50/60 C respectively (and constant).

Still trying to trouble shoot, but I'm leaning it more to be something with operating system again... I'm going to keep researching it!

Thanks for your help!

---

