---
title: "[SOLVED] Kernel question / updates for 9th Jan."
date: 2009-01-09
forum: New to Ubuntu
---

### Post by RedMartin on 2009-01-09
I'm using 8.04 and my Grub boot menu says that I'm using Kernel 2.6.24-21-generic.

Is this the latest version? I haven't seen a new entry on my Grub menu for ages when I used to see them fairly regularly.

If I do sudo dpkg -l linux-image-2.6.24-22-generic I get:

||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-image-2. 2.6.24-22.45   Linux kernel image for version 2.6.24 on x86

Am I all up to date? I had a 60mb update today including some new Kernel stuff and Nvidia bits and bobs yet nothing seems to have changed version wise.

So, has there been an update lately that should have changed my Grub list and is there anywhere within Ubuntu that I can find out what I updated on the last update?

Thank you.

---

### Post by nhasian on 2009-01-10
i typed in

```
uname -a
```

and this is what it said for me:

> Linux hpnhasian 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

seems i have a newer linux kernel 2.6.27-9

---

### Post by jfr1tz on 2009-01-10
the revisions differ because the topic starter runs ubuntu 8.04 and the responder runs 8.10(most likely as the kernel version matches the current one in 8.10). 

Normally your update manager will notify you if a newer kernel version is available.  From the console you can also look by using apt-cache show to see the current and available revisions.

you can also look [here]("http://packages.ubuntu.com/hardy/linux-image") for listed kernel packages for your current ubuntu version.

the current version in that list seems to be [this]("http://packages.ubuntu.com/hardy/linux-image-2.6.24-22-generic") one which seems to match your current version.

---

### Post by zvacet on 2009-01-10
Last Hardy kernel is 2.6.24-23 from last night update.Did you restart comp after updates? You can check your kernel version with 

```
uname -r
```

or 

```
uname -a
```

---

### Post by drs305 on 2009-01-10
> **RedMartin said:**
> 
So, has there been an update lately that should have changed my Grub list and is there anywhere within Ubuntu that I can find out what I updated on the last update?

In addition to downloading the most recent kernel, you may have to change your settings in grub's menu.lst to actually start *using* a newer kernel. Grub does not decide which kernels to download but its settings do determine which kernels are *displayed and used*.

One way to do this is to install StartUp-Manager and go to the 'Advanced' tab. There you can select whether grub automatically starts to use a new kernel once it is installed. You can also manually change the *installed* kernel to use by selecting that option on the main tab (Boot Options) of StartUp-Manager. 

With the introduction of a new kernel, your displayed menu.lst on boot will probably add the new kernel to the choice of options. StartUp-Manager also will allow you to choose how many kernel options you wish to see.

Of course, you can also manually edit menu.lst yourself, but StartUp-Manager's gui interface makes it harder to make mistakes.

For more information on StartUp-Manager (installing, available options, etc) see this link:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by zvacet on 2009-01-10
@ **RedMartin**

How many kernels do you have installed?You can remove all except last two (with higher number).You can do it from sinaptic by typing **linux-image** in search box.

---

### Post by RedMartin on 2009-01-10
Apologies for not replying sooner. After I posted this the forum went down. When I looked back this morning I couldn't find this thread and I assumed it hadn't made it before the down-time.

Anyhoo I did loads of Googling and eventually found out what was happening.

When installing the new kernel a dialog box opened. It asked me something about the grub menu.lst and did I want to keep the 'changed' version. As I had removed some old kernel entries and as this appeared to be the default option I clicked 'next'.

It appears that doing this prevent the grub list from being updated with the new kernel entry. That explains why I wasn't seeing the update.

I found this in Lauchpad after much Googling:[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/229656](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/229656)

> run ucfr --purge grub /var/run/grub/menu.lst

and then

>  sudo update-grub

This did the trick. My kernel list grew by two entries and I was happy.

As I understand it I should have chosen the option above what I thought was the default when that dialog box appeared. The option was along the lines of allowing the package manage to alter the menu.lst.

With regard to all this can I assume that now I am using the latest kernel I am also using the latest restricted gubbins which was downloaded yesterday as well or do I need to do something to get that running?

Nearly finally, when I remove some of the old kernel images do I also need to remove the headers too?

..and finally, thanks to you all for replying.

---

