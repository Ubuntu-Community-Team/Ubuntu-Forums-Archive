---
title: "How can I uninstall / rollback the most recent update?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by skitter on 2011-07-15
I was prompted to install a host of updates last night, and one (or more?) have rendered my system unusable unless I boot to low graphics recovery mode (failsafex).  The problem I'm seeing when I boot normally is the video rate is unbearably slow (~5 FPS and worse when moving windows).    I suspect the problem maybe related to the SandyBridge chipset my laptop uses. Prior to the update 3d acceleration didn't work, and now 2d is also broken.     I tried selecting 'previous version of linux' and then selecting 2.6.38-8-generic-pae, but still have the same terrible video performance.      I previously installed a CPU usage monitor and see the load staying below 0.2.  The CPU is a core I5 and there is 4 GB RAM in the machine.  I'm running 11.04 with Unity and Compiz.  Any suggestions regarding how to fix this / roll back to the old version are appreciated.

---

### Post by akand074 on 2011-07-15
I'm not sure if it's possible to rollback an update. But I believe you can roll back individual packages using Synaptic Package Manager. Unless someone knows of a better way, you can possibly check out your Update Manager log and roll back the packages it updated if possible. Best I can do for you.

---

### Post by mikewhatever on 2011-07-15
'Rollback' is a Windows concept similar to 'power toys', 'control panel', 'system restore', 'internet explorer' and 'windows registry'. It doesn't exist on Linux, but even if it did, do you know which one of the updates you want rolled back?.
You can use the recovery mode to fine out what was updated:
```
tail -n25 /var/log/apt/history.log
```

---

### Post by CatKiller on 2011-07-15
Once you've worked out which package it was that caused your problem you can force the version of that package to the one that worked and then lock that package to that version so that you won't get further updates. If you find that a future version has fixed whatever your problem is you can unlock the package to get it upgrading normally.

---

### Post by skitter on 2011-07-15
How foolish of me to assume that I could ask a question on the 'Absolute Beginner Talk' forum and not receive a lecture as a reply. Thanks for the feedback any how Mike.

---

### Post by mikewhatever on 2011-07-15
> **skitter said:**
> How foolish of me to assume that I could ask a question on the 'Absolute Beginner Talk' forum and not receive a lecture as a reply. Thanks for the feedback any how Mike.

What, you mean the two lines, 41 words and 203 characters long, lecture? Well, don't mention it.:p

---

### Post by apoorvumang on 2011-07-15
Same problem here, also on a sandy bridge arch. chipset!!

Did the above solutions work for you skitter?

Here's the link to my thread about the problem - [http://ubuntuforums.org/showthread.php?t=1805018](http://ubuntuforums.org/showthread.php?t=1805018)

---

### Post by corncob on 2011-07-15
> **skitter said:**
> 
   I tried selecting 'previous version of linux' and then selecting 2.6.38-8-generic-pae, but still have the same terrible video performance.   .

My wife upgraded her Toshiba laptop to 11.04 by mistake and the same thing happened to her.  I too selected 'previous version of linux' but not the pae kernel which I deleted as she only has 4 gigs of RAM. I don't want to give a lecture here but I did run
```
sudo update-grub
```
and reset the default boot up version with Startup Manager.

---

### Post by apoorvumang on 2011-07-15
I found why I got this problem: I had xorg-edgers in my repository. 
sudo ppa-purge xorg-edgers did the job for me.

---

### Post by dFlyer on 2011-07-15
> **skitter said:**
> I was prompted to install a host of updates last night, and one (or more?) have rendered my system unusable unless I boot to low graphics recovery mode (failsafex).  The problem I'm seeing when I boot normally is the video rate is unbearably slow (~5 FPS and worse when moving windows).    I suspect the problem maybe related to the SandyBridge chipset my laptop uses. Prior to the update 3d acceleration didn't work, and now 2d is also broken.     I tried selecting 'previous version of linux' and then selecting 2.6.38-8-generic-pae, but still have the same terrible video performance.      I previously installed a CPU usage monitor and see the load staying below 0.2.  The CPU is a core I5 and there is 4 GB RAM in the machine.  I'm running 11.04 with Unity and Compiz.  Any suggestions regarding how to fix this / roll back to the old version are appreciated.

If you know which package broke your system, and that package has the old package still on your system in /var/cache/apt/archives you can use:

sudo dpkg -i "packagename" without the quotes to revert back to the old package.

---

### Post by skitter on 2011-07-15
Thanks everyone for the replies and suggestions.

dFlyer- I wish I knew exactly which package caused the problem, but I'm afraid I'm not (yet) sure. My initial plan was to revert the system back to the state it was in before the problem, and then install the updates one at a time untill I found the culprit.

The mention of xorg-edgers does ring a bell. Back before I gave up on getting 3d acceleration to work, I added them (apparently improperly).  So far, I haven't had any luck removing them.  I've tried this:

```

sudo ppa-purge xorg-edgers
sudo: ppa-purge: command not found

```

and this:
```

sudo apt-get remove xorg-edgers
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package xorg-edgers

```


A quick look at var/lib/apt/list shows me this.
```

/var/lib/apt/lists$ ls -l
...
-rw-r--r-- 1 root root   255825 2011-07-14 10:24 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_natty_main_binary-i386_Packages
-rw-r--r-- 1 root root   122012 2011-07-14 10:24 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_natty_main_source_Sources
-rw-r--r-- 1 root root     9745 2011-07-14 10:24 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_natty_Release
-rw-r--r-- 1 root root      316 2011-07-14 10:25 ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_natty_Release.gpg
...

```


Can someone offer some advice regaring how I should cleanup (remove) the  xorg package so I can test if it's causing the issue?

---

### Post by dcsoldschool53 on 2011-07-15
If you need to find out which packages were updated, in Synaptic package manager Click file > history. Search for the date of your last update, then click the plus sign next to it. When it opens, click the label with your month, day, year.
This will tell you, what updates you had received, and.there is a screen shot that will show you how it looks. You now have a list of your updates to help you troubleshoot the problem. You can either remove them through Synaptic or the terminal, or reinstall old versions```
sudo dpkg -i "packagename"
```Example```
sudo dpkg -i evolution-common_2.28.3-0ubuntu10.2
```to get the old one back.

---

### Post by dcsoldschool53 on 2011-07-15
To removed an unwanted program```
sudo dpkg -r "packages-name"
```or```
sudo apt-get remove "package-name"
``` in the terminal.

---

### Post by skitter on 2011-07-15
FIXED!

Thanks for all the help everyone. 

It turns out that edgers was causing the grief.  I had trouble removing it because ppa-purge wasn't installed (and I don't know exactly what I'm doing yet...).  I installed ppa-purge via Ubuntu software center, and then was able to run sudo ppa-purge xorg-edgers in a terminal. A reboot later, and the system was back to the way it was before the update. 

Thanks again all.

---

