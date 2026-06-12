---
title: "BCM4306 Problem"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Keitarosan on 2007-05-29
I've been trying to use Wireless for a while, but I am unable to get it to work in Ubuntu 7.04. I have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03), and I have used this guide [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) to try and get it to work. After I did everything, Wireless was no longer an option in Network Settings, and it did not work. I uninstalled ndiswrapper, and restarted the guide to see if I did anything wrong. At step 13 I typed ndiswrapper -l, but it said bcmwl5 : invalid driver!

I tried installing bcmwl5a.inf, but it still says the same thing. I was just wondering if anyone had any ideas to fix this, or can tell me if I'm using the wrong drivers or something. I've looked through several topics, but can't figure it out.

---

### Post by Keitarosan on 2007-05-29
Any ideas?

---

### Post by bthessel on 2007-05-29
Any luck? I am having the exact same problem. I have had it working in the past on this same laptop in Dapper and upgraded to Feisty and it worked. Just did a fresh install of Feisty on it and now I can't get it to work.

---

### Post by jglen490 on 2007-05-29
I used [_this_]("http://ubuntuforums.org/showthread.php?t=250889") as my way ahead to get my Broadcom 4318 working.  Mine isn't not the same chip as yours and my distro is Kubuntu 6.06 LTS, but the principles should be the same.

I used the version of ndiswrapper that was on my install CD.  I also used the Win2K driver from the CD that came with my Buffalo card - copying both the .inf and the .sys files to my home directory.  The key that got mine to work, aside from starting fresh, was blacklisting the kernel module that Dapper wanted to install and actually removing that module (i.e., modprobe -r bcm43xx).  After that it was a matter of following the standard set of commands needed to associate ndiswrapper with the Windoze driver, setup the module entry, do a modprobe and a depmod as outlined in the link.  I then installed kwlan/wpa_supplicant so I could configure the communications between the wifi card and my router with WPA.

Worked great for me.  I have heard of some folks having problems with Feisty, and for others it's been smooth.  Try it and see what happens.

---

