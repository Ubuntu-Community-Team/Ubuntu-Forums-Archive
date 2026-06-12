---
title: "Ubuntu with nVidia Drivers"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by scorey1609 on 2009-02-16
I have a somewhat lengthy problem, hopefully I can summarize it as best as possible.

I tried installing Intrepid about 6-8 months ago when it first came out.  I had trouble installing my nVidia driver.  Doing so would render my x-server useless.  As soon as my bootup got to the GDM, the screen would go blank and my monitor would turn off.  I found countless other people who were having similar problems so I checked the forums and none of the solutions fixed the issue.  Some were having luck, others were not.

Admitting apathy, I rolled back to 8.04 Hardy Heron, installed the driver upon the first bootup as instructed and had no problems after that with Hardy.

A few weeks ago, I attempted a triple boot with XP, Hardy, and Windows 7.  I, however, accidentally deleted my Hardy partition in the process mistaking it for Ubuntu Studio which I intended to delete.

After several reinstalls of Hardy, I was able to get grub to recognize all 3 OS's that I was working with, but now both 8.10 and 8.04 mysteriously will not cooperate with the nVidia driver just as was happening before.  I've tried a clean sweep of the partition and several reinstalls and nothing works.  I've also tried installing the nVidia driver from root hub as some of the forms recommended with no success.

Please help, I'm running out of options and horribly sick of windows.  It just makes no sense that it wouldn't work from a fresh install.  I've installed Hardy several times on this computer and have NEVER had a single issue with the video drivers not working.  

I'm installing a 64 bit copy of Ubuntu 8.04 and using an nVidia gForce 7300 Video card.

Thanks!

---

### Post by bodhi.zazen on 2009-02-16
try installing nvidia-glx-new

or search synaptic for the nvidia driver.

If that fails you can use envy.

Once the driver is installed, run

```
gksu nvidia-settings
```

Envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

FYI Envy is in the repos, that link give you info.

---

### Post by error420 on 2009-02-16
> **bodhi.zazen said:**
> try installing nvidia-glx-new
If that fails you can use envy.
FYI Envy is in the repos, that link give you info.

What he said...Use synaptec package manager to get envy...it will automatically purge, get the latest and greatest nvidia drivers for you.

---

### Post by scorey1609 on 2009-02-18
I tried these things, the problem with these recommendations is that I have no issues installing the nVidia driver, I've done it several times and probably about a dozen different ways.  The problem is that the nVidia driver causes my x-server to not work.  Linux works fine with the generic drivers, but it's pointless to run Ubuntu with no graphics.  The safe startup option in grub allows me to repair the x-server, but it doesn't make my driver work, it replaces the xorg.conf file with the default one.

Any ideas why 8.04 would start doing this all of the sudden even though it used to work fine?

---

### Post by avtolle on 2009-02-18
Have you done any updates lately (thinking specifically about a kernel update)?

---

### Post by bodhi.zazen on 2009-02-18
When you install the nvidia driver, then run gksu nvidia settings

What are the error messages when X then fails ?

---

### Post by scorey1609 on 2009-02-18
> **avtolle said:**
> Have you done any updates lately (thinking specifically about a kernel update)?

No updates, I'm running on a fresh install.  every other time I installed from the CD, it gave me the option to install proprietary drivers, I did, restarted, and it worked fine.  Not so any more.

>  When you install the nvidia driver, then run gksu nvidia settings

What are the error messages when X then fails ? 

I run nvidia-settings and it says "ou do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.".  When I restart, I can't get back into the x server at all.

I have a feeling that when I am reinstalling linux, parts of the 8.10 install is still on the hard drive and it is recognizing some of the wrong files.  I'm going to get into windows and completely zero this drive and try it from absolute scratch... Thanks for your help so far... I know it can work, it's just a matter of how.

---

### Post by bodhi.zazen on 2009-02-19
No, when you install the root partitions is formated, so there are no partial files.

It sounds as if you need to install the nvidia drivers.

How did you install the nvidia driver ?

---

### Post by scorey1609 on 2009-02-19
> **bodhi.zazen said:**
> No, when you install the root partitions is formated, so there are no partial files.

It sounds as if you need to install the nvidia drivers.

How did you install the nvidia driver ?

I installing the nvidia driver that I downloaded off nVidia's website via root hub.  I installed it with the restricted drivers manager that comes up with the updates, I installed it by apt-get install nvidia-glx-new, I've installed it through selecting specific packages on Synaptic, and... I've installed it using envy.

I do know that it reformats the root hub, but sometimes when I run a fresh install, the restricted drivers manager shows that the drivers are already installed when synaptic disagrees, whenever that is the case, I reinstall the OS and that goes away and I'm able to actually install the driver.  A couple of months ago, it worked fine.  Now, that install process does not work.

Thanks again for your helping me.

---

