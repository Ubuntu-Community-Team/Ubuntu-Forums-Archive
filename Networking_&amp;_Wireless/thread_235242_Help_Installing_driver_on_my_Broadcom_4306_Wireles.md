---
title: "Help Installing driver on my Broadcom 4306 Wireless Card"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by aburd on 2006-08-12
Hi and thanks for reading this.

I've been attempting to use this instruction set for installing my card's driver:

[http://www.essayally.com/linux/laptopsetup-dv1000.php]("http://www.essayally.com/linux/laptopsetup-dv1000.php")

It appears pretty simple but I have run across a couple of problems. This first problem has come up when attempting to use ndiswrapper on my driver. I type in 

> sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

It then spits out:

> Installing bcmw15
couldn't copy /home/aburd/Desktop/bcmw15.inf at /usr/sbin/ndiswrapper line 135.


Now this is the official driver for the card. I have it sitting on my Desktop. Is the driver corrupt? It worked the first time I tried this before hitting problem 2, but now suddenly it hates this driver. 

Ok on to problem 2. Now I try typing this in terminal:

> sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo sed --in-place 's/RadioState|1/RadioState|0/g' $conffile
done

First it tells me there is no "-m" command and gives me a list of alternatives. Second, how am I supposed to enter this? As one lump or in bits? Or should I know which of the two apparently seperate commands to enter?

Thanks. I've been trying to get this thing working on and off for 2 weeks. Any help would be appreciated.

---

### Post by aburd on 2006-08-12
Also, this is an HP Pavilion zv5000 laptop. I'm not sure if that is relevant or not but I figured it would be good to give all info that could possibly be relevant.

---

### Post by woz on 2006-08-13
I have a zv5000 as well. I have tried lots of distros and have decided to go with Ubuntu. Once I see how you get the wireless sorted out I will install it for real. Up to now I have'nt come close in getting it sorted out.

---

### Post by 454redhawk on 2006-08-13
[http://www.ubuntuforums.org/showthread.php?t=201902]("http://www.ubuntuforums.org/showthread.php?t=201902")

---

### Post by aburd on 2006-08-13
@ 454redhawk:

Thank you very much for your help. I have hit a snag on that direction list as well. I am pretty new to linux (which may be obvious already), so please understand that my personal knowledge base is pretty low.

Ok so I tried the directions you gave me. They look very easy to use, but when I entered the code:

> sudo modprobe ndiswrapper


I get this:

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


How do I fix that? To be honest, I'm not even sure what that means. I thought modprobe was a function of ndiswrapper? Or is it a missing peice of ndiswrapper? 

Thanks.

---

### Post by aburd on 2006-08-14
So I managed to get through this tutorial [This tutorial]("http://www.essayally.com/linux/laptopsetup-dv1000.php") with the help of [AskMetafilter.]("http://ask.metafilter.com/mefi/44403")

But now I have another issue. Suddenly all of my WiFi options are gone from my Networking tool. Any idea how to get those back. You can see what I am talking about here:

[IMG]http://static.flickr.com/64/215471808_34ddf5793f.jpg?v=0[/IMG]

Anyone know how I can get my WiFi options back? Thanks!

---

### Post by Paul133 on 2006-09-05
Well, as far as the 4306 is concerned, the tutorial posted worked wonders for me, even with WEP, though I always keep the WEP key handy b/c the networks resets after power outages. As far as the sudo modprobe ndiswrapper error, I don't know what to say, other than that I'd try the tutorial again and see what u come up with. When I did it, I got the drivers, saved them, and then blacklisted bcm43x. Then I got the utils from the internet (because I plugged in an ethernet cable I had lying around). Are you sure you got the ndiswrapper-utils? Do you have internet access on your laptop? If not then,
Code:

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf


(make sure the .sys file is in there also, without it, it won't work)

and then run the following commands. Basically, just try the tutorial again and se what happens, but make sure to get the files.

---

### Post by toconeal on 2008-03-03
> **454redhawk said:**
> [http://www.ubuntuforums.org/showthread.php?t=201902]("http://www.ubuntuforums.org/showthread.php?t=201902")

I went through the tutorial and am still coming up with
inffile : invalid driver!

I have tried installing this ndiswrapper twice with the same results.  If anyone has any helpful bits of wisdom.  This is my first bout with gutsy 7.10 kernel 2.6.22-14 generic.  It is on a 2210us compaq dual boot, with a 4306 broadcom rev 3.  I have been messing with this thing for three days.  I have wore the google button off of my toolbar.........  Thanks

---

