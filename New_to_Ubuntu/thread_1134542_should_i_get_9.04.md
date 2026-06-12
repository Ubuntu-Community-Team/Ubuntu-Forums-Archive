---
title: "should i get 9.04?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by thesuperjman on 2009-04-23
i have 8.10 right now (which i noticed isnt on the download page anymore, any reason as to why?) should i get 9.04? or even switch from 8.10 to 8.04?

what are the main things i need to know?

---

### Post by Melk79 on 2009-04-23
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

That will give you the rundown.  I've been using the beta for the last three weeks and just did a clean install of 9.04.  I'm loving it.

---

### Post by Electron on 2009-04-23
on my part Jaunty perfomance better than 8.1, even recognized my wireless card with no problem.

---

### Post by alphacrucis2 on 2009-04-23
> **thesuperjman said:**
> i have 8.10 right now (which i noticed isnt on the download page anymore, any reason as to why?) should i get 9.04? or even switch from 8.10 to 8.04?

what are the main things i need to know?

If you are running an ATI graphics card using the fglrx driver and your card is one of those that ATI dropped support for when releasing the Catalyst 9.4 drivers, then you will be forced to use the open source driver with Jaunty. This means losing graphics functionality and performance (at least until we get better open source drivers for those older cards). Otherwise you should be fine with Jaunty.

---

### Post by jlhaslip on 2009-04-23
Just did an Upgrade from 8.10 to 9.04 and I am very disappointed in 9.04, to be honest. 
The entire system is lagging like I am running W98 on dial-up. Extremely slow responses from the mouse clicks, although the mouse moves and responds well, the clicks are taking forever to load pages or open applications.
I think I will be reverting to 8.10 and wait for the graphics or response fixes to occur. And, no, I am not using a blacklisted video chipset to the best of my knowledge. 
Simple things like backspacing to correct typos are timed using a Calendar. I haven't given up on Ubuntu, in fact, I love it, but this upgrade was not for me.

---

### Post by JK3mp on 2009-04-23
> **jlhaslip said:**
> Just did an Upgrade from 8.10 to 9.04 and I am very disappointed in 9.04, to be honest. 
The entire system is lagging like I am running W98 on dial-up. Extremely slow responses from the mouse clicks, although the mouse moves and responds well, the clicks are taking forever to load pages or open applications.
I think I will be reverting to 8.10 and wait for the graphics or response fixes to occur. And, no, I am not using a blacklisted video chipset to the best of my knowledge. 
Simple things like backspacing to correct typos are timed using a Calendar. I haven't given up on Ubuntu, in fact, I love it, but this upgrade was not for me.

sucks to hear that. Again thanking gods im gonna test it first to make sure b4 full install. As far as above posts from what i hear it'll be MAJOR better performance wise for majority. So just do as i am. Test it first then commit. :-)  .

---

### Post by albinootje on 2009-04-23
> **jlhaslip said:**
> I am not using a blacklisted video chipset to the best of my knowledge. 

What videocard is it ?
And does the command "dmesg" show any errors or problems ?

---

### Post by jlhaslip on 2009-04-23
See Below, thanks

---

### Post by jlhaslip on 2009-04-23
jim@jim-laptop:~$ dmesg | grep Intel
[    0.000000]   Intel GenuineIntel
[    0.825153] CPU0: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    0.912963] CPU1: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[   23.597583] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   23.651148] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   23.773111] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.773187] HDA Intel 0000:00:1b.0: setting latency timer to 64
jim@jim-laptop:~$ dmesg | grep error
jim@jim-laptop:~$ dmesg | grep warn
[ 7010.591612] warning: `proftpd' uses 32-bit capabilities (legacy support in use)
jim@jim-laptop:~$

---

### Post by albinootje on 2009-04-23
> **jlhaslip said:**
> 
[   23.597583] agpgart-intel 0000:00:00.0: Intel 945GM Chipset

Perhaps this is useful :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342923](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342923)
[https://lists.ubuntu.com/archives/universe-bugs/2009-March/062477.html](https://lists.ubuntu.com/archives/universe-bugs/2009-March/062477.html)

---

### Post by thesuperjman on 2009-04-23
> **jlhaslip said:**
> jim@jim-laptop:~$ dmesg | grep Intel
[    0.000000]   Intel GenuineIntel
[    0.825153] CPU0: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    0.912963] CPU1: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[   23.597583] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   23.651148] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   23.773111] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.773187] HDA Intel 0000:00:1b.0: setting latency timer to 64
jim@jim-laptop:~$ dmesg | grep error
jim@jim-laptop:~$ dmesg | grep warn
[ 7010.591612] warning: `proftpd' uses 32-bit capabilities (legacy support in use)
jim@jim-laptop:~$

^^^^how do i get to this so i can show my computers info. i used to know but i forgot. so you say that there are some graphics bugs they're working out? because some of the games i've downloaded like nexuiz and tremulous won't work.

---

### Post by jlhaslip on 2009-04-23
Thanks, I'll search that second link information out.
The first link fails to load. White screen only. It is also linked in the second of your links and fails from there as well.
How to activate the UXA fix as found in the second link?

I'll try searching for 'enabling UXA' on this forum.

---

### Post by Cresho on 2009-04-23
Im dissapointed as well.  I may try the 64 bit version.  x works slow, audio is horrible.  video sync is fixed though.

---

### Post by jlhaslip on 2009-04-23
Fond the solution [here](https://wiki.ubuntu.com/X/UxaTesting) and modified the config file.
Works like it used to (or better, not sure).

Thanks for the assistance.

---

### Post by bm13084 on 2009-04-24
> **alphacrucis2 said:**
> If you are running an ATI graphics card using the fglrx driver and your card is one of those that ATI dropped support for when releasing the Catalyst 9.4 drivers, then you will be forced to use the open source driver with Jaunty. This means losing graphics functionality and performance (at least until we get better open source drivers for those older cards). Otherwise you should be fine with Jaunty.

so no compiz until this happens?  I tried following a tutorial on installing ati drivers... [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

didn't work... i screwed it up, i suppose

---

### Post by albinootje on 2009-04-24
> **thesuperjman said:**
> how do i get to this so i can show my computers info. 

Here's some examples to get more system info :
```

lspci
lsusb
cat /proc/cpuinfo
free -m
lshw -C video

```

---

### Post by mcurtiss1970 on 2009-04-24
I'll be going back to 8.04.2LTS after the usual 71/Legacy/Nvidia issues I had with 8.10

---

### Post by thesuperjman on 2009-04-24
is downgrading possible?^^^^ would i lose anything if i downgraded?

---

### Post by robertc36 on 2009-04-24
I have a boot time of 47 secs and everything worked flawlessly on my hp laptop, so more than happy.

---

### Post by jlhaslip on 2009-04-24
You won't lose anything if you backup your personal files onto a removal disk or Hard-drive.

---

### Post by pbpersson on 2009-04-24
On a related note.....as the OP stated, on the download page the world has a choice between:

Hardy Heron (oldy moldy)

Jaunty Jackalope (brand new and buggy)

Should there not be something in between?

OH - if I go to the master list and then go into a location, all the versions are there.  Never mind :redface:

---

### Post by thesuperjman on 2009-04-24
my intrepid is workin fine so far. it boots and runs flawlessly fast, i just had some problems when first startin up, theres still some little things im working on at the moment. im just curious if 8.04 is better than 8.10 or if it doesnt really matter.

---

### Post by pbpersson on 2009-04-25
Here is a list of [new features]("http://www.ubuntu.com/getubuntu/releasenotes/904overview") in version 9.04

---

### Post by rlogan on 2009-04-25
Here's my view for you !!

So far three machines running Jaunty all fresh installs from 9.04 Beta. Two machines are working 100%, the third gave a little grief. 

As to what I call a little grief is as follows. AWN seems to have a issue with detecting Compiz running but does not stop the system working just a silly error message. Disabled Compiz and AWN and then renabled them after a restart and all is working fine. PreviouslyI had to get the correct screen resolution of 1440x900 for my monitor, the video card worked at this resolution before but it is not listed as a resolution in the GFX card manual. End story was hand edited x.org file and all is a source of joy.

The last is a silly little issue which is a pain as Firefox 3.0.8 and 3.0.9 freeze up due to consuming a large amount of RAM up to 1.7Gb of 2.0Gb (thus the freeze). I have reinstalled flash but no joy, it is only one website but one that I like to use a lot.

All in all Jaunty is so much more responsive and runs like a joy, just one silly little issue on 1 out of 3 machines. Otherwise it is a gem.

I have one machine left to upgrade and have been reluctant to rush this one as it is my wifes machine and it has Atheros 5007 chipset for WIFI which has been up to and including Intrepid a pain to put it bluntly due to having to compile drivers each kernal update. Have tried the Live CD tonight on this machine and once the WPA key is entered it works out of the box. So the next day or two I will also update this from Intrepid.

All in all Jaunty is very nice, Job well done in my opinion to Ubuntu.

Cheers

Richard

---

