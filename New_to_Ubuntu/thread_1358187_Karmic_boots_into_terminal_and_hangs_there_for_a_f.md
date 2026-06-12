---
title: "Karmic boots into terminal and hangs there for a few minutes"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-12-18
For the last couple of boot ups, karmic has been booting up into terminal prompting me for my login then a few minutes later, it continues to boot up normally.  However, I then get a black background wallpaper, again for a couple of minutes, then finally, my desktop appears.  I'm on a Toshiba Satellite A215-S7444 with 2Gb of RAM, AMD Turion 64 X2 Dual-Core, ATI Radeon X1200 series and I have lots of free disk space on my HDD.

-Yos

---

### Post by lidex on 2009-12-18
Try this in a terminal:
```
sudo gdmsetup
```

---

### Post by YosefKaro on 2009-12-18
> **lidex said:**
> Try this in a terminal:
```
sudo gdmsetup
```

Ok, then what?

-Yos

---

### Post by YosefKaro on 2009-12-18
...and I can't enable boot up logging with bootlogd.  I found out that this is a bug that has been hanging around for awhile unfortunately.  :(

-Yos

---

### Post by lidex on 2009-12-18
Did you go through the setup? Reboot after.

---

### Post by lidex on 2009-12-18
More here:
```
[http://ubuntuforums.org/showthread.php?t=1253012]("http://ubuntuforums.org/showthread.php?t=1253012")
[http://ubuntuforums.org/showthread.php?t=1213785]("http://ubuntuforums.org/showthread.php?t=1213785")
[http://ubuntuforums.org/showthread.php?t=1259121]("http://ubuntuforums.org/showthread.php?t=1259121")
```

---

### Post by zkriesse on 2009-12-18
Hmmm.....let me research this Yos....see what I can come up with.

---

### Post by ukripper on 2009-12-18
Before booting in, hold the shift key so that you can see selection of other kernel images listed there in grub list, and select the previous kernel from the list in that grub menu selection. See if you could boot into it without problem.

---

### Post by YosefKaro on 2009-12-18
First I need to turn back on "quiet splash" that someone had me set to "".  Where do I make this change?

-Yos

---

### Post by YosefKaro on 2009-12-18
Ok, I changed it back to "quiet splash" at /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and I booted up into an earlier kernel.  While I didn't get the terminal this time, my desktop still lagged for a couple of minutes.

-Yos

Making progress :)

---

### Post by ukripper on 2009-12-18
> **YosefKaro said:**
>  my desktop still lagged for a couple of minutes.



Please elaborate on this bit more. How it lagged? After login screen or before?

---

### Post by philinux on 2009-12-18
> **lidex said:**
> Did you go through the setup? Reboot after.

What setup, this is Karmic. There is no setup.

---

### Post by YosefKaro on 2009-12-18
Should I try uninstalling and re-installing grub2 following the grub2 guide [here]("http://ubuntuforums.org/showthread.php?t=1195275") ?

-Yos

ukripper, I use automatic log in.  The lag that I am still experiencing when booting into the earlier kernel comes after where the login would be.

---

### Post by YosefKaro on 2009-12-18
If it is any help, I've noticed that this problem only occurs when I do a cold boot, but when I restart, I don't have this problem.

-Yos

---

### Post by YosefKaro on 2009-12-19
Here is the output from dmesg: [http://pastebin.com/f56c95d37](http://pastebin.com/f56c95d37)

-Yos

---

### Post by YosefKaro on 2009-12-19
Someone suggested that I change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/default/grub to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=hpet" and then update grub.  I'll try to get back with the results the next time I boot up.

-Yos

---

### Post by YosefKaro on 2009-12-19
Well, that last step didn't help any. C'mon, any ideas?  I feel like I am having a monologue here.

-Yos

---

### Post by YosefKaro on 2009-12-19
I decided to switch from Grub2 back to Legacy and I have noticed a dramatic change in boot time; Legacy Grub is much better for me.  I still have that problem with my desktop lagging behind a bit after booting up but I can live with that.

-Yos

---

### Post by emc on 2009-12-29
I am experiencing this same issue.  Reverting to the earlier kernel .14 does seem to work but it would be something I would have to do each time I logged in as it seems to revert back to the newest kernel .16 each time. (Yes, Karmic is my version)  I have found that I am not able to use the internal wireless card however with this .14 log in method.  

Whether or not I am booting from cold start or a restart it always hangs at command line prompt for two minutes and then logs into the GUI.  

I have been all over the web trying to figure out a solution to this problem. One site suggested this is a bug over at launcher.net.  I submitted my issue to their system.  Here is the address to that particular site:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/434786](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/434786)

[Above Link]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/434786")

---

### Post by emc on 2009-12-29
If it helps, my username on that other site is Ken B (currently I am the last poster on that site at the bottom)  To make it easier, I am going to just copy and paste my post from there to here:



Symptoms similar to Chaghaboo describes.

System was fine after initial clean installation (complete format of hard drive) of Ubuntu 9.10. Installed on a Dell Inspiron 1501. After installation, I searched for hardware drivers within the Ubuntu GUI interface and installed the wireless drivers. [see below]

(Administration - Hardware Drivers - Broadcom STA wireless driver for the Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322- based hardware)

Next, I used the update manager to perform the recommended updates. After updates the system suggests a restart to finalize installation of said updates. This is where the problem of hanging at the command line for 1.5 to 2 minutes takes place. I am able to do startx and log into the system GUI immediately but without wireless option. However, if I do this I *still* will be logged into the GUI by the system after the 1.5 to 2 minutes. This happens while I am already within the GUI! I will see the screen flash black - then a circular mouse image spinning - then the Ubuntu desktop with wireless keyring prompt - everything working properly at that point. The next time I shut the computer down or restart the computer, the command line prompt comes back with a 1.5 minute to 2 minute delay before going into the GUI. It is worth noting that this command line prompt can sit without any keyboard input and move into the GUI by itself after the 1.5 to 2 minutes have surpassed.

I have recreated this bug now three times. I was relieved to find this forum suggesting this is a bug and not something I am doing wrong.

Questions:

Is there currently a known fix for this bug?

If no fix is available, is there a work around?

My current workaround thought is that I simply not install the recommended updates. It is NOT until I install the recommended updates that this bug begins.

I am a new Ubuntu / Linux user loving the education! I am excited about this open source project and hopefully my experiences somehow will influence someone with more knowledge to fix this problem. I am a new computer science student at IPFW in Fort Wayne, Indiana! Hopefully within a couple years I am able to contribute more to this project.

Long live Open Source!

---

### Post by emc on 2009-12-29
If it helps, my username on that other site is Ken B (currently I am the last poster on that site at the bottom)  To make it easier, I am going to just copy and paste my post from there to here:



Symptoms similar to Chaghaboo describes.

System was fine after initial clean installation (complete format of hard drive) of Ubuntu 9.10. Installed on a Dell Inspiron 1501. After installation, I searched for hardware drivers within the Ubuntu GUI interface and installed the wireless drivers. [see below]

(Administration - Hardware Drivers - Broadcom STA wireless driver for the Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322- based hardware)

Next, I used the update manager to perform the recommended updates. After updates the system suggests a restart to finalize installation of said updates. This is where the problem of hanging at the command line for 1.5 to 2 minutes takes place. I am able to do startx and log into the system GUI immediately but without wireless option. However, if I do this I *still* will be logged into the GUI by the system after the 1.5 to 2 minutes. This happens while I am already within the GUI! I will see the screen flash black - then a circular mouse image spinning - then the Ubuntu desktop with wireless keyring prompt - everything working properly at that point. The next time I shut the computer down or restart the computer, the command line prompt comes back with a 1.5 minute to 2 minute delay before going into the GUI. It is worth noting that this command line prompt can sit without any keyboard input and move into the GUI by itself after the 1.5 to 2 minutes have surpassed.

I have recreated this bug now three times. I was relieved to find this forum suggesting this is a bug and not something I am doing wrong.

Questions:

Is there currently a known fix for this bug?

If no fix is available, is there a work around?

My current workaround thought is that I simply not install the recommended updates. It is NOT until I install the recommended updates that this bug begins.

I am a new Ubuntu / Linux user loving the education! I am excited about this open source project and hopefully my experiences somehow will influence someone with more knowledge to fix this problem. I am a new computer science student at IPFW in Fort Wayne, Indiana! Hopefully within a couple years I am able to contribute more to this project.

Long live Open Source!

---

### Post by harold1 on 2009-12-29
Yeh, my recommended driver didn't work until I installed the previous two first in order. I think it's like you can't install sp3 before sp1 and 2 in Windows. I sure like the power in Unix, Ubuntu 9.10 64 bit that is.  The logic is a bit different, ie. it's logical. I can only seem to add files to a backup folder on the hard drive first and then burn the whole thing, as each time I add anything it erases everything before and sets to read only. Maybe that was what was happening in Dos also, but I couldn't make sense of the Windows setup the way it keeps you blind. How can the C: drive be under the Desktop and the Desktop under the C: drive, for instance?
That sort of comes to the whole world system, run by a few sociopaths who don't have the manpower or the brainpower.  I think we have to take back control and be responsible for our own destiny and Linux is just one example of a better new world order being built behind the scenes. Well I only left out one thing. Intuition is the secret to life. There now you know all that I do.
"The only real valuable thing is intuition."
Einstein

---

### Post by emc on 2009-12-29
Ok update on my situation!  

I believe I have found the REAL problem!  Broadcom STA driver for the wireless card is causing all of my boot hang issues...  Once I install these drivers, then my restart and cold start of this computer will hang at a command prompt for a couple minutes before then going into the GUI.

I am running this internet connection off of auto eth0 currently and when I restart I am not landing at the command prompt.  I am getting a regular restart with GUI and quickly :)  

Question now is what to do about this wireless card issue?  If I install the drivers [Broadcom STA wireless drivers - These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware] I will hang at command prompt for two minutes before auto redirecting to the GUI.  IF I do not install the wireless driver I will not have wireless access :(  

Any help or suggestions would be greatly appreciated.  Thank you!
 -

---

### Post by lidex on 2009-12-29
Run this command in a terminal:
```
dmesg | less
```

Now scroll through the output to see if any clues to what is going on when the hang occurs.

---

