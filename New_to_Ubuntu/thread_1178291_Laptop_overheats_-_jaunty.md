---
title: "Laptop overheats - jaunty"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-06-04
I know this has been repeatedly posted, but I thought I would bring some of it together. I do not have a solution for this, but there are a few promising ideas in bug reports.

Basically, what seems to be happening is that the fan on laptops takes too long to spin up and even when it does so, it is not at a high enough speed to cool down the CPU. So, the CPU stays hot and eventually the laptop shuts down (this has happened to me multiple times).

A possible [solution]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173/comments/22") is to keep the fan speed at a high setting and leave it like that.

This seems a little drastic, and I have no idea how it may affect the fan in the long run.

The various bug reports (which seem similar) are:

[https://bugs.launchpad.net/ubuntu/+bug/361123](https://bugs.launchpad.net/ubuntu/+bug/361123)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)
[https://bugs.launchpad.net/ubuntu/+bug/375285](https://bugs.launchpad.net/ubuntu/+bug/375285)

There are also a number of threads on this issue in the forum:
[http://ubuntuforums.org/showthread.php?t=1129135](http://ubuntuforums.org/showthread.php?t=1129135)
[http://ubuntuforums.org/showthread.php?t=1135358](http://ubuntuforums.org/showthread.php?t=1135358)
[http://ubuntuforums.org/showthread.php?t=1130450](http://ubuntuforums.org/showthread.php?t=1130450)
[http://ubuntuforums.org/showthread.php?t=1175054](http://ubuntuforums.org/showthread.php?t=1175054)
[http://ubuntuforums.org/showthread.php?t=1149565](http://ubuntuforums.org/showthread.php?t=1149565)
[http://ubuntuforums.org/showthread.php?t=1175692](http://ubuntuforums.org/showthread.php?t=1175692)
[http://ubuntuforums.org/showthread.php?t=1136575](http://ubuntuforums.org/showthread.php?t=1136575)
[http://ubuntuforums.org/showthread.php?p=7285275](http://ubuntuforums.org/showthread.php?p=7285275)

I'm sure there are more threads and also situations where people are blaming other components, however, this is a good sample I believe.

This old [guide]("http://ubuntuforums.org/showthread.php?t=597998") for CPU Frequency Scaling has been suggested, but since it appears that the problem is with the fan, setting the CPU to a lower speed may solve the problem, but it is not an effective overall solution.

There is another suggested [fix]("http://ubuntuforums.org/showthread.php?t=1036051") but I am unsure what it does, although it is supposed to help!

In conclusion I was wondering if there was any conclusive answer to this, or if anyone was working towards one.

---

### Post by chezzo on 2009-06-05
I'm not sure that there might not be two problems involved-

When I first installed Jaunty, although my CPU scaling was set at "ondemand" my CPU seemed to be stuck at its maximum rate (1.87 GHz) so, following [this thread]("http://wwww.ubuntuforums.org/showthread.php?p=7285275") I installed the package *powernowd*, which fixed this issue.

However, my laptop still gets hot and I basically have to keep on "powersave" mode using the CPU scaling monitor to prevent it from burning up too much (I haven't actually experienced any shutdowns but that may be because of putting it in powersave when it starts feeling too hot). I hadn't noticed before, but the fan definitely does seem to just stay on its lowest setting all the time, so I think you must be right that there is a fan issue. This would also explain why people with many different types of processor are all having the same problem.

Some people have also been complaining that their pc starts up in "performance" mode by default - which suggests a third problem, unless this is also fixed by installing *powernowd*.

Hoping for a fix very soon!

---

### Post by abhiroopb on 2009-06-05
I installed it as well, will update on how it worked....

Does it require any configuration?

---

### Post by chezzo on 2009-06-05
No, think I may have restarted but that was it.

---

### Post by abhiroopb on 2009-06-05
Hopefully this will partly sort the issue, but I think the main thing seems to be the fan issue.

---

### Post by jijin on 2009-06-05
Having the same issue here. Nothing in /proc/apci/fan/ btw.

---

### Post by abhiroopb on 2009-06-05
Yes I don't have anything in that folder either. But I think thats because we don't have thinkpad_acpi installed.

---

### Post by CylnZ on 2009-06-05
Cynical current comment: If you have an Intel 965 chipset, without a controllable bios fan you're screwed for right now.

Sadly, I have 2 laptops with 965s. Both running 9.04, both having been cleaned, have dsdts 0,0,0 errors both undervolted, both have to have 4 inch desk fans blowing across them to stay cool.

---

### Post by abhiroopb on 2009-06-05
How do you know if you have that chipset?

The strange thing is, is that it is suggested that the Fan isn't switching off enough. At least on my laptop the fan does seem to be running quite fast (its quite loud at least). When I keep my laptop raised off the desk the temperature is hot, but not unbearable. The CPU temp fluctuates between 42C to start and then stays between 60C and 78C (critical is apparently 85C). HD temp starts at 28C and moves upto about 53-55C (critical is at 60C).

So, I'm nearing the borderline and scared of the damage its doing to my computer, other than that its fine really!

---

### Post by grungedoobie on 2009-06-05
I have an ancient Toshiba laptop running XUbuntu on it.  It's a 366Mhz with 512MB RAM and an 80GB HDD.  I have a wireless adapter for it and use it for music, games, light surfing, e-mail and a number of other odd things like diagnosing the neighbors internet connection to restoring thumb drives.

It also had a major heat issue.  The only thing I could come up with to solve the problem was to install the "toshset" utilities and then add the fan on command to "crontab".  Now, every 5 minutes cron tells the fan to turn on full speed.  A number of things can tell the fan to turn down or off, but relief is never more than 5 minutes away.

I'll write down the instructions for doing so and post back if there's any interest in going this route.

It's better to have a whirring fan than a popping CPU, right?


The Grunge.  :)


After-Word: Keeping your hardware cool will help it last longer and run more efficiently.

---

### Post by skintythe1andonly on 2009-06-06
Fr me it appears to be the hard-drive. The CPU sensors dont appear to be running too hot but the GPU is running hotter than Intrepid. I can feel the heat coming from directly under the hard-drive. This heat is then blown back onto the GPU before going out through the vent. The CPU is on the other side I think (HP dv2000). When I run 
```
sudo hddtemp /dev/sda
```
I get the following reply

```
skint@skint-laptop:~$ sudo hddtemp /dev/sda
[sudo] password for skint: 
WARNING: Drive /dev/sda doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sda: FUJITSU MHW2120BH:  no sensor
skint@skint-laptop:~$
``` 

even though according to this website [http://www.almico.com/forumharddisks.php?man=65]("http://www.almico.com/forumharddisks.php?man=65"), there is a sensor there. 

Anybody else having this issue? or is it just me?

---

### Post by chezzo on 2009-06-06
> **CylnZ said:**
> Cynical current comment: If you have an Intel 965 chipset, without a controllable bios fan you're screwed for right now.

I'm pretty sure mine's a 945 chipset - it's an intel core solo T1350

> **skintythe1andonly said:**
> Fr me it appears to be the hard-drive.... Anybody else having this issue? or is it just me?

I don't know where the various components in my laptop are located, so I've no idea if the hot patch under my left hand is the hard drive or the cpu... But running that command gives me
```
/dev/sda: Hitachi HTS541080G9SA00: 37°C
```

As I said though, I'm pretty sure it's the CPU which is overheating, since the problem is reduced when I limit it to powersave mode.

---

### Post by abhiroopb on 2009-06-06
Could you please provide the fan command that you wrote.

Also I can check to see how fast my fan is running and if it can run any faster. It seems to me as though the fan is running quite fast, but then again my HD and my CPU are quite hot.

Can the nVidia card be causing a problem?

---

### Post by Harpie Queen on 2009-06-06
This isn't really a great permanent solution but I hope it will help. I had problems with my old laptop, which sadly passed away earlier this year (hard drive gave up, not worth replacing). When I was sitting down and using it I split my legs quite far, and made contact only with the very edge of the bottom of the laptop. When I was running it on a surface I put a dvd packet under one corner of it to boost airflow. It never crashed due to overheating again. It did not have enough space under the laptop, because someone else was rough and broke the bit that held it up from the surface. try and keep your legs as far from the fan as possible. 

OK, it's not a perfect solution, but it'll do the job until issues can be resolved with more permanence.

---

### Post by abhiroopb on 2009-06-06
Thats what I'm doing right now.

I have a bunch of poker chips on each rubber feet to raise the laptop and boost airflow.

---

### Post by alexcckll on 2009-06-06
I'm on a Thinkpad R61i, remedy until SOMEONE gets their finger out and resolves this laptop-killing incident is to run my laptop atop an Akasa cooler.

A couple of nice big desktop fans blasting away at the base.. that after giving the fan and vents a good go over with compressed air...

FOR GOODNESS' SAKE CANONICAL, GET YOUR ARSES IN GEAR OVER THIS!!!!

---

### Post by abhiroopb on 2009-06-06
Calm down :P...I'm sure they're doing the best they can!

---

### Post by skintythe1andonly on 2009-06-07
> **Harpie Queen said:**
> This isn't really a great permanent solution but I hope it will help. I had problems with my old laptop, which sadly passed away earlier this year (hard drive gave up, not worth replacing). When I was sitting down and using it I split my legs quite far, and made contact only with the very edge of the bottom of the laptop. When I was running it on a surface I put a dvd packet under one corner of it to boost airflow. It never crashed due to overheating again. It did not have enough space under the laptop, because someone else was rough and broke the bit that held it up from the surface. try and keep your legs as far from the fan as possible. 

OK, it's not a perfect solution, but it'll do the job until issues can be resolved with more permanence.


I bought a 9 cell hp battery which props up the back of the laptop. I think its whats saving mine at the moment. I think I am going to have to change to another distro that supports ext4 until this is resolved as my home is formatted to this. Any suggestions?

---

### Post by cyberspheres on 2009-06-07
Hi all,

I also seem to be having this problem. My laptop is a Toshiba Satellite A200 1GB. At maximum usage the CPU temperature reaches 78C (on Windows it never gets past 70C) and the machine shuts down. Sometimes it even refuses to boot for several minutes after the shutdown. I can force it to do so by cooling the machine with e.g. a bag full of ice.

I can also confirm it looks like a Ubuntu problem (i.e. not a hardware problem), because I dual boot with Windows Vista and the laptop runs fine there. Furthermore, the heatsink was cleaned and the thermal paste replaced less than a month ago.

I am just puzzled over one detail. Previously, I was under the impression that fan speed on laptops was controlled exclusively by the BIOS based on temperature readings. Apparently this isn't the case, otherwise there wouldn't be a way to override the fan speed, as someone suggested, and it also wouldn't make sense that my laptop runs fine on Windows.

However, to the best of my knowledge, there is no kernel support for controlling the fan on my laptop -- either through the toshiba_acpi or the omnibook modules. How is it possible, then, that the Linux kernel somehow messes up with the fan control to the point that my laptop overheats?

---

### Post by CylnZ on 2009-06-08
> **abhiroopb said:**
> How do you know if you have that chipset?

@abhiroopb I use ```
sudo lshw | grep Memory
```so, mine comes back:
```
  product: Mobile PM965/GM965/GL960 Memory Controller Hub
             product: Mobile GM965/GL960 Integrated Graphics Controller
             product: Mobile GM965/GL960 Integrated Graphics Controller

```since I have, (unfortunately) integrated graphics on this little Acer 5620-6830.

---

### Post by alexcckll on 2009-06-08
> **CylnZ said:**
> Cynical current comment: If you have an Intel 965 chipset, without a controllable bios fan you're screwed for right now.

Sadly, I have 2 laptops with 965s. Both running 9.04, both having been cleaned, have dsdts 0,0,0 errors both undervolted, both have to have 4 inch desk fans blowing across them to stay cool.
Annoying - just checked...

alex@ubuntu:~$ sudo lshw | grep Memory
          description: System Memory
          product: Mobile PM965/GM965/GL960 Memory Controller Hub

Running a 965 here... has this been logged?

---

### Post by alexcckll on 2009-06-09
Oh - had a look around.. and this might suggest that people running Thinkpad R61is are having a heat issue as well - 

[http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=3409](http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=3409)

Seems to be down to the GPU possibly..

Maybe something to investigate?  Is this down to the Intel 965 chipset?

---

### Post by kblcuk on 2009-06-09
> **alexcckll said:**
> 
Maybe something to investigate?  Is this down to the Intel 965 chipset?

Hm... Dunno, but my HP tx2000 has an nvidia chipset (Nvidia C51M), and overheats, whereas my work laptop is intel-based (Intel GM45, I think, but I'm not sure), and doesn't have that problem. Both run Jaunty with latest updates.

---

### Post by CylnZ on 2009-06-10
> **alexcckll said:**
> Annoying - just checked...

alex@ubuntu:~$ sudo lshw | grep Memory
          description: System Memory
          product: Mobile PM965/GM965/GL960 Memory Controller Hub

Running a 965 here... has this been logged?

you mean submitted to launchpad? If so, yep.
Not a lot they can do about it since intel has never released its code. There was a whole linux dev site about it that has mostly died waiting for intel.

here's the bugrep: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)

---

### Post by merlin666 on 2009-06-12
I have an emachines M6811 (mobile athlon 3400) and think I have a similar problem. I have used Ubuntu for several years, but after upgrading to the last jaunty kernel my computer crashes within a few minutes. This is a dual boot system and runs fine with XP, right now converting an avi to dvd at a core temp of 75C. 

I had some issues with this last year, related to the power cycle of the cpu, and the way it crashes in ubuntu is very similar. Some suggestions on how to control this would be much appreciated. I am not even sure if I can do anything at all with my current install as it only lasts for a few minutes before the crash.

---

### Post by mike.thorton on 2009-06-15
Hello community, as I was checking this thread frequently, it seems that the bug still exist and no fix or workaround is issued.

I decided to share my temps here (HP 6510b/4GB RAM/Core 2 Duo, Intel x3100):

CPU: 49 °C
HDD: 52 °C
other temps (around 10 sensors) in average of 50 °C

It's a Powersave state. When the browser is opened (with flash) it turns to 70°C and I must switch off the computer for a while as it is hot as hell. It also damaged my laptop's battery :(

I'm thinking about an upgrade to Karmic. What do you people think? I know it's not a good idea, but I can't keep this state. Or maybe I'll switch the distribution - which one would you suggest?

---

### Post by kblcuk on 2009-06-15
I've installed Fedora 11 recently. It has some annoying features as well, but at least it doens't melt down my laptop.

It's been about 1,5 month since the original bug was reported, and no action taken what so ever. Annoying.

---

### Post by abhiroopb on 2009-06-15
Seems to be a lot of activity on this bug report. I would suggest everyone have a look at it...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)

---

### Post by kblcuk on 2009-06-16
Yep, one participant of the discussion in that bug report noted, that on Hardy this bug appeared right after an update to a newer kernel (2.6.24.something, the same that Jaunty runs on).
Fedora has an even newer version (2.6.30), and no heat issue.
Might it be so that kernel update will fix this?
Can anyone skilled enough to update kernel by himself test it?
I, unfortunately, don't have a laptop to test now, since the one that had that problem runs Fedora now and belogns to my girlfriend - don't think she'll be happy with that I'm playing with her laptop again... :)

---

### Post by Hated On Mostly on 2009-06-16
> **kblcuk said:**
> Yep, one participant of the discussion in that bug report noted, that on Hardy this bug appeared right after an update to a newer kernel (2.6.24.something, the same that Jaunty runs on).
Fedora has an even newer version (2.6.30), and no heat issue.
Might it be so that kernel update will fix this?
Can anyone skilled enough to update kernel by himself test it?
I, unfortunately, don't have a laptop to test now, since the one that had that problem runs Fedora now and belogns to my girlfriend - don't think she'll be happy with that I'm playing with her laptop again... :)

If you want to see if using 2.6.30 will fix the issues in Ubuntu, follow the following guide, but use the 2.6.30 packages instead:

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

---

### Post by abhiroopb on 2009-06-16
> **Hated On Mostly said:**
> If you want to see if using 2.6.30 will fix the issues in Ubuntu, follow the following guide, but use the 2.6.30 packages instead:

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

Thanks a lot for this, very simple method. Will take a while before I can figure out if it is working on it.

here is the updated guide for the 2.6.30 kernel: [http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

Few questions:

1. Is it bad to install a kernel like this?
2. How should this be updated? Is it each time an update is released, or will it update automatically?
3. If it won't update automatically is there a PPA I can add to my sources.list that updates to the newest kernel?

I also got this error:
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]

---

### Post by Hated On Mostly on 2009-06-16
> **abhiroopb said:**
> Thanks a lot for this, very simple method. Will take a while before I can figure out if it is working on it.

here is the updated guide for the 2.6.30 kernel: [http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

Few questions:

1. Is it bad to install a kernel like this?
2. How should this be updated? Is it each time an update is released, or will it update automatically?
3. If it won't update automatically is there a PPA I can add to my sources.list that updates to the newest kernel?

I also got this error:
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
..........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]

A solution to this was posted in the comments, but due to language barriers it might be confusing.

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/#comment-1702](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/#comment-1702)

[http://doraki.net/396](http://doraki.net/396) (Korean)

[http://babelfish.yahoo.com/translate_url?doit=done&tt=url&intl=1&fr=bf-home&trurl=http%3A%2F%2Fdoraki.net%2F396&lp=ko_en&btnTrUrl=Translate](http://babelfish.yahoo.com/translate_url?doit=done&tt=url&intl=1&fr=bf-home&trurl=http%3A%2F%2Fdoraki.net%2F396&lp=ko_en&btnTrUrl=Translate) (english babelfish translation)


Maybe uninstalling the proprietary driver for nvidia or ati cards temporarily will allow you to install it? I have an Intel card so I haven't seen this problem.

Another method maybe to add the koala karmic repositories to your third party software sources and just install the kernel update packages it shows in the update manager (don't select anything else or do an upgrade). I tried that before in intrepid (added jaunty repositories) and it installed very smoothly. If it can't install properly synaptic should tell you and stop the install. I am not sure if Karmic Koala is using 2.6.30 final yet, but eventually it will and right now it is certainly using one of the release candidates which might fix the problem.

Make sure you backup your stuff before doing any of this. I have never had any problems playing with my system, but maybe I got lucky and I was always backed up. Of course if something does go wrong updating your system, your data will still be there, but you may not be able to boot to a GUI.

---

### Post by abhiroopb on 2009-06-16
Tried everything but the nvidia problem wouldn't go away.

Thanks for the help, but I guess I'll have to wait until this update is added to jaunty

---

### Post by Hated On Mostly on 2009-06-19
> **abhiroopb said:**
> Tried everything but the nvidia problem wouldn't go away.

Thanks for the help, but I guess I'll have to wait until this update is added to jaunty


In the meantime, you might want to try out the live CD of Karmic Koala Alpha 2 which was released recently and see if the problem persists. Alpha 2 uses linux kernel v2.6.30

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

---

### Post by Shivendu on 2009-06-19
Hi,
Just got the Ubuntu free DVD by courier

Thanks a lot everyone.

Now I will start installing and start coming up with some challenges.

---

### Post by chezzo on 2009-06-21
The recent update to kernel 2.6.28-13 seems to have fixed the problem for me!

---

### Post by emeraldgirl08 on 2009-06-23
One thing I noticed in my IBM Thinkpad T30 is after installing Jaunty my CPU usage would spike and stay in the high 90's!!!

I found that turning off the wireless would alleviate this problem- but come on! 

**Who's going to leave their wireless off??!!!**

Thinking that a program using wireless was causing the spike in CPU that lead to high temps I:

system>>preferences>>startup applications
and unticked check for new hardware drivers, remote desktop, and update notifier. I figure I could do these manually anyway.

Result: I don't see any more spikes and high temps right now. I know this isn't going to solve everyones case but give it a shot if you want.

---

### Post by CylnZ on 2009-06-23
> **abhiroopb said:**
> Seems to be a lot of activity on this bug report. I would suggest everyone have a look at it...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)

Heh, I'm listed about 1/2 way down the page, lol.


If you're still having nvidia troubles add this repo:

```
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main #NVIDIA Pre-compiled
deb-src http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main #NVIDIA Pre-compiled
```

after you add all the repositories and do sudo apt-get update, you will get errors with various public keys in those errors.

Just do the following for each of those errors:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com [COLOR=Red]**<key>**[/COLOR]

---

### Post by dschulz on 2009-06-24
I reported a similar problem in launchpad a few weeks ago.
I'm still looking for a solution.



*"CPU fan doesn't get triggered even at high temps"*
[https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/375132]("https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/375132")

---

### Post by philcamlin on 2009-06-24
my laptop works and the fans go alot :popcorn:

---

### Post by hewart on 2009-06-28
Hi everyone

Still with the heat issue. Updates haven't fixed it for me yet.

In my case the fan works properly, as it does on windows. The only problem are the higher temps, it doesn't shut down though.

I suggest two candidates:
- GPU: perhaps the driver doesn't work properly
- Wifi: touched the wifi card and goes very very hot

---

### Post by merlin666 on 2009-06-28
> **chezzo said:**
> The recent update to kernel 2.6.28-13 seems to have fixed the problem for me!

I booted cold and it ran long enough to get this new kernel (previously I had a crash before the update even started). Running for about 10h around 50C now - this may have fixed the issue for me as well.

---

### Post by Jitterro on 2009-07-03
Hi. I recently updated to 9.04 on my Acer Aspire 5100-5023 and I'm experiencing this bug as well. Even with kernel 2.6.28-13 my laptop's cpu scaling function doesn't seem to be working properly (it stays at full speed no matter what the amount of load on the cpu) and the temperatures climb to nearly 80c. The only fix I've found so far is to scale back the cpu manually to 800mhz, but obviously this is a less than ideal solution.

I'm going to go add a +1 to the bug report as well.


Went ahead and tried the new kernel install (2.6.30-020630) to fix this issue and it seemed to ameliorate the problem somewhat, but my laptop still runs hotter than it did in Hardy or Intrepid. Hopefully the bug will be patched soon.

---

### Post by Manthis on 2009-07-04
Hi,

I'm encountering the same problem too with my Dell XPS M1210. The average heat is around 60°C but sometimes increases dramatically. I think it might be a GPU issue but not sure about it.

I tried the Fedora Core 10, just before switching to Jaunty and I had the same issue.

Scared about my laptop's health...

I'm gonna investigate the problem...

---

### Post by Digitallysick on 2009-07-04
My lenovo Y410 has the issue. But here is what happens, If I turn on the notebook and don't let it sleep or suspend its fine, the fan runs, But, once It wakes up from suspend, or sleep. The fan doesn't kick back on as it should, and it overheats. 

So if I hibernate , or sleep, I have to do a full reboot, just pressing power and resuming messes me up, once I resume, i reboot, and all is well. 

Something for me, isn't kicking the fan or heat/fan sensors back on after suspend

---

### Post by skintythe1andonly on 2009-07-07
Hi I came across something strange when going through powertop trying to see if it was one application that was causing the excessive heat```
Wakeups-from-idle per second : 175.2    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  38.2% (100.6)       <interrupt> : eth0 
  16.4% ( 43.2)      <kernel IPI> : Rescheduling interrupts 
  15.9% ( 41.9)       firefox-3.5 : futex_wait (hrtimer_wakeup) 
  10.9% ( 28.6)       <interrupt> : extra timer interrupt 
   4.0% ( 10.5)       <interrupt> : pata_amd 
   3.2% (  8.4)       <interrupt> : PS/2 keyboard/mouse/touchpad
   2.4% (  6.4)       <interrupt> : eth1
   2.3% (  6.0)    wpa_supplicant : wl_add_timer (wl_timer)
   2.2% (  5.8)     <kernel core> : hrtimer_start (tick_sched_timer)
   1.0% (  2.7)       compiz.real : schedule_hrtimeout_range (hrtimer_wakeup)
   0.7% (  1.8)       <interrupt> : sata_nv, mmc0

```

what is interesting is that eth0 is my ethernet port yet currently i am connected to my router through my wireless card eth1. This is possibly what is causing the heating

---

### Post by juustomuna on 2009-07-25
I have HP NX8220 laptop with ATI Radeon Mobility X600, which overheated. I solved with this:

Install these packages from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

libdrm2_2.4.12+git20090717.9aed44be-0ubuntu0sarvatt~jaunty_i386.deb
libdrm-radeon1_2.4.12+git20090717.9aed44be-0ubuntu0sarvatt~jaunty_i386.deb
xserver-xorg-video-ati_6.12.99+git20090723.2afc46fa-0ubuntu0sarvatt~jaunty_i386.deb
xserver-xorg-video-radeon_6.12.99+git20090723.2afc46fa-0ubuntu0sarvatt~jaunty_i386.deb

sudo dpkg -i libdrm*.deb xserver*.deb

Also, make sure that you have this in your /etc/X11/xorg.conf:

Section "Device"
        Identifier "Configured Video Device"
        Driver "radeon"
        Option "ClockGating" "true"
        Option "DynamicPM" "true"
EndSection


----------------

Also I was using Spotify, where I had to use (in winecfg) ALSA and emulation. Changed that to OSS and Full HW accelleration.

- Juusto Muna

---

### Post by merlin666 on 2009-07-26
I guess I was overly optimistic. The heating issue continues, but I have installed the temperature gauge and may be getting some more information (Emachines M6811 with mobility radeon and amd 3400 processor). For one, when I boot cold the laptop seems to be stable around 65, but if I need to reboot and the computer is already warm the temperature can raise quickly into a zone where it can not cool down anymore. With only firefox running and trying to load a java-heavy site, the temperature rapidly climbed above 90 degrees, and it shut down at 99.

---

### Post by abhiroopb on 2009-08-13
So, I've got an update...

Most of the time my HD temperature stays at around 49C - 53C (max is 60C I think). It should be slightly lower I guess but this isn't too bad.

My CPU temp is what causes me headaches! Its usually around 55C - 65C. If I'm doing anything remotely processor intensive then it goes upto 78C and the process starts to stutter. For example, I was playing counter-strike and it played fine for about 10 minutes after which the processor temp hits 78C and the game started slowing down.

---

### Post by abhiroopb on 2009-08-13
So, I've got an update...

Most of the time my HD temperature stays at around 49C - 53C (max is 60C I think). It should be slightly lower I guess but this isn't too bad.

My CPU temp is what causes me headaches! Its usually around 55C - 65C. If I'm doing anything remotely processor intensive then it goes upto 78C and the process starts to stutter. For example, I was playing counter-strike and it played fine for about 10 minutes after which the processor temp hits 78C and the game started slowing down.

---

### Post by merlin666 on 2009-08-13
> **abhiroopb said:**
> So, I've got an update...

Most of the time my HD temperature stays at around 49C - 53C (max is 60C I think). It should be slightly lower I guess but this isn't too bad.

My CPU temp is what causes me headaches! Its usually around 55C - 65C. If I'm doing anything remotely processor intensive then it goes upto 78C and the process starts to stutter. For example, I was playing counter-strike and it played fine for about 10 minutes after which the processor temp hits 78C and the game started slowing down.

I had the same issue with my 4.5 years old laptop. I finally decided to blow some compressed air into the fan vents. A small cloud of dust emerged and the fan had a good spin. Now, my laptop runs around 33 - 35C and goes up to over 50 only on multimedia apps or java websites.

---

### Post by abhiroopb on 2009-08-14
Its actually become a lot better. I used a vacuum cleaner for my fan vent and it has gotten a LOT better! Thanks for that.

---

### Post by Payo on 2009-10-22
Upgrading to 9.10 Karmic (beta) has solved my overheating problem.

---

### Post by swoody on 2009-10-22
As others have mentioned, I would first make sure overheating issues aren't hardware related (i.e. - Clean out that dang laptop!) Using a can of compressed air paired with a strong vacuum at the other end of your CPU vents should do wonders. If you are brave enough, there are Service Manuals available online for different laptop makes/models, a Google search should tell you if there's one available for you. When I first encountered overheating with my laptop I took it apart and cleaned all the dust, lint, etc. that had accumulated inside the fan housing and *especially* inside the CPU heatsink itself. While a simple blow/suck may be able to dislodge some of the crud, there's really no substitute for opening up your laptop case and really being able to get at it. I also replaced my original thermal paste with a dab of MX-2, and it has worked wonders. I now run Folding@Home 24/7 on my laptop which keeps my CPU usage at 100%, and it barely gets warm enough to kick on the fans every few mins.

(Please note: Laptops can be very difficult to take apart and put back together successfully. If you are not comfortable with this idea, please don't attempt it yourself, but I'm sure you can find a friend or a local computer shop who will be able to handle it.)

Another issue to keep in mind is to *NOT* use your laptop on your lap, or any other soft surface. Besides blocking the air vents on the bottom of the case, this also introduces loads of lint and fabric fiber into the computer. I would recommend at least using some hard surface between your laptop and a soft surface. A simple keyboard drawer, or a spare piece of wood will do fine in a pinch :)

---

### Post by StephenDennis on 2010-01-01
I have a T500 Thinkpad with an ATI Radeon PCIE card.  I have been running Ubuntu on it for 18 months.  I recently upgraded to Jaunty and have been experiencing very high temperatures near the center of the system.  

The contents of /proc/acpi/ibm/thermal would show something like
<pre>temperatures:    42 44 36 70 33 -128 30 -128 41 47 42 -128 -128 -128 -128 -128</pre>
with the fourth value being very high.

I found that manually setting the fan to 'disengaged' kept the system relatively cool...
<pre>temperatures:    42 44 36 51 33 -128 30 -128 41 47 42 -128 -128 -128 -128 -128</pre>

Still not perfect.  With more experimentation I found the following solution which 
required both items to work very effectively:

In the bios on the machine there are settings for thermal managment.  I set them to Balanced instead of Maximum Performance.  I also installed the FGLRX driver.

Now the machine stays cool under all circumstances with readings like this.
temperatures:    41 44 36 44 33 -128 30 -128 41 47 41 -128 -128 -128 -128 -128
and does so without excessive fan cycling.

I believe that there is something about the free ati radeon driver that causes the video
chip to overheat.

---

