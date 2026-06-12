---
title: "Intermittent internet problem sporadically affects only installed Ubuntu"
date: 2019-08-24
forum: Networking &amp; Wireless
---

### Post by dora5 on 2019-08-24
I am using Ubuntu 18.04.   Internet connection is hard wired using a cable. 

The internet is sporadically not working.

I can ping our router, but cannot ping google.com nor 8.8.8.8 and 8.8.4.4, which are Google's server IP addresses.   In other words, a fix aimed at DNS won't fix it.

In Windows 7 on the same computer, I can connect to the Internet without a hitch on the same computer.

If I boot up the same computer with Ubuntu Live USB, it connects to the internet without a hitch.

I only recently installed Ubuntu and hadn't set it up, so I reinstalled Ubuntu.  It worked fine for a couple of hours and now back to the same thing.  While it was working I configured Ubuntu and installed things.   I installed basic post Ubuntu install things that are installed on my computer at home.   And none of it was installed before I ran into this problem and reinstalled Ubuntu.  

Checking network settings doesn't show anything wrong.  It is set to do everything automatically and connects to the right router, obviously since I can ping the router.   

I've disabled and enabled the wired connection three times.  Didn't help.

Ubuntu has a slightly different IP address than Windows - 192.168.1.7 instead of 1.4, but I believe that is normal.

What would be causing this and how do I fix it?

Ifconfig isn't working because it tells me it isn't installed and you can't install in Ubuntu if the Internet doesn't work (you really need to change that).   

Thanks!

Yours,
Dora Smith

---

### Post by dora5 on 2019-08-24
Solved it.  It appears the router is having dotty issues, perhaps on account of a bad port.  I ran lshw -C network and lspci | grep-i network and among other things, learned the name of my ethernet device.   

Then I looked up how to renew my lease.

sudo dhclient -r eno1
sudo dichlient eno1

Where eno1 is the device name of my ethernet adapter and it will be different on yours.   

Other handy commands

sudo service networking restart and
sudo service network-manager restart

After these, the dhclient last, as posts said that is what works, I can ping google, so I'm guessing my Internet is BACK.    :)

---

### Post by him610 on 2019-08-25
Congratulations for resolving your issue yourself!

---

