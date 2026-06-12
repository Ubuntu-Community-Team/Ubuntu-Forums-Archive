---
title: "Restoring Ubuntu 2.6.27-11"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by voxmagna on 2010-06-02
Hi, I was travelling abroad with my netbook when a couple of apps wouldn't save their files. Although it might seem obvious now, my 4.5 Gb partition was out of space. 

So I find the synaptic package manager and try to remove what I thought were rarely used apps. No the Synaptic manager won't run because my HDD space only has 40Mbyte left!

So I put in my live CD which is on a memory stick and extend the HDD partition using the part tool. Everything seems ok on re-boot. Then after a second reboot there is a desktop background, mouse pointer and nothing else. 

Then I try to do *"sudo apt-get install ubuntu-desktop"* But I am stuffed because I only had access to wifi networks via a usb wifi stick.

So I try the command lines to enable wlan0 up, enter the essid and wep key. That seemed ok but after *sudo dhcpd wlano*, the reply was always that the network was sleeping.

I gave up until I could get back home and connect via my Ethernet link.

I enter ctrl/alt/F1 and login ok

....then *sudo apt-get install ubuntu-desktop*

There are a number of errors listed, I think the most important are:

Could not find platform independent libraries <prefix>
Could not find platform dependent libraries   <exec_prefix>

Consider setting $PYTHONHOME to <prefix> [:<exec_prefix]

Errors were encountered while processing:
/var/cache/apt/archives/gnome-applets_2.24.1-Oubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I need some help as I would rather restore the existing installation than start all over. Sudo apt-get isn't working for me and neither are the boot options to fix broken files.

Is there a way, even using the live CD, of booting Ubuntu into a minimal 'Safe Mode' desktop from where I can do recovery maintenance?

Thanks

---

### Post by cariboo on 2010-06-02
If you have no storage space left, clean up unused files instead of trying to re-install things. If you can boot in recovery mode, do that, at the menu choose drop to root prompt. Once at the prompt type:

```
sudo apt-get clean
```

the above command will remove archived packages that have been downloaded. Next type:

```
sudo apt-get autoremove
```

this command will remove any unneeded dependencies. This should free up a couple of hundred MB.

---

