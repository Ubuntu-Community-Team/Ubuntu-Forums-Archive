---
title: "Frustrated with WIFI"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Skorkeper on 2009-01-29
I just switched from using the windows 7 beta. I'm starting to regret the switch to Ubuntu 8.10.

I spent the day learning how to install a wireless driver that in windows would download itself. Is there a version of Linux that searches for the driver a person needs automatically? 

My problem is that I managed to install the drivers I needed for my wireless usb adapter and my ubuntu laptop sees my router. It sees all available networks but it wont connect to my router. I've disabled all encryption in the router to get it to connect and it just wont connect. It's quite frustrating. I need help!!!

---

### Post by jimrz on 2009-01-29
Would be best to post the info (make/model/chipset) of your adapter so that others who have got the same type working can assist you.

---

### Post by Temposs on 2009-01-29
For most wireless cards, Ubuntu works with them instantly. It's a fairly rare case that you need to install a wireless driver.

You should tell what model wifi card you have and also what model router you have, so that we can help you better.

---

### Post by Cope57 on 2009-01-29
For my hardware, openSUSE and Crunchbang worked flawlessly on the liveCD.
I decided to install BOTH onto my laptop. I am dual booting Linux, no Windows...

**Laptop** [openSUSE 11.1](http://opensuse.org) - Linux 2.6.27-9 x86_64 / [#!CRUNCHBANG](http://crunchbanglinux.org) - Linux 2.6.29

btw, Crunchbang Linux is Ubuntu based.

If you regret using Ubuntu, use another distribution.

[[IMG]http://img206.imageshack.us/img206/2472/dwbannernr8.png[/IMG]]("http://distrowatch.com")

---

### Post by Skorkeper on 2009-01-29
My adapter is a Netgear WG111T USB Adapter. I managed to get the driver loaded and it almost works. I just can't get it to make that connection.

---

### Post by Neural oD on 2009-01-29
what i found very useful is to disable your standard ethernet - usually eth0
to do this go to command line and type: sudo ifdown eth0
then check if the wireless works - seems to have worked for me

---

### Post by Neural oD on 2009-01-29
by the way - if u want the eth0 up again - just type: sudo ifup eth0
- hope this helps

---

### Post by random turnip on 2009-01-29
> **Temposs said:**
> For most wireless cards, Ubuntu works with them instantly. It's a fairly rare case that you need to install a wireless driver.

I beg to differ, ive had Ubuntu on 3 computers now, not a single one of them had an "ubuntu freindly" wireless card.

Dont get me wrong, i know its the fault of the hardware companies, not Linux, but its still a big problem, no use ignoring it, its driving a hell of a lot of people away from Linux.

---

### Post by Topsider on 2009-01-29
I believe I have found someone else who had the same card and issues and got it to work check this post out: [http://blog.blamires.co.uk/index.php/2007/01/27/wireless_woes_ubuntu_aamp_netgear_wg111t](http://blog.blamires.co.uk/index.php/2007/01/27/wireless_woes_ubuntu_aamp_netgear_wg111t)

---

### Post by mrbiggbrain on 2009-01-29
are you useing any closed source drivers?

---

### Post by Skorkeper on 2009-01-29
I'm using the windows driver

---

