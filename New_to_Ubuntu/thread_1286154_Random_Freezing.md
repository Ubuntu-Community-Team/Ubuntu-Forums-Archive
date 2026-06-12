---
title: "Random Freezing"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by gendoikari1 on 2009-10-08
I installed Xubuntu 9.04 on a Sony Vaio PCG-7A2L (1.86 GHz Intel Celeron dual core, 512 MB RAM), and it was working fine for the first few days. I wanted to download some packages via Synaptic (mostly for video game emulators) so I left the laptop running overnight. When I came back, it froze. I rebooted it, and it froze again a few seconds after I got to the desktop. I rebooted again, and I got the same problem, this time on the blue-green screen right before the login prompt. Also, for some reason, when I enter the GRUB menu, it says I have two kernels:
*Ubuntu 9.04 kernel 2.6.28.15-generic (something like that)
*Ubuntu 9.04 kernel 2.6.28.15-generic (Recovery Mode)
*Ubuntu 9.04 kernel 2.6.28.11-generic
*Ubuntu 9.04 kernel 2.6.28.11-generic (Recovery Mode)
*memtest86+

Is that bad? Anyway, it still freezes after I boot, and it says something about "Root or sudo privileges required" (which never happened before). Any help please?

---

### Post by QIII on 2009-10-08
That in itself is not bad.

You have your choice of loading either of the two kernels.  I like to keep one back just in case I run into problems with a new one.

Try using the older one (.11) and see what happens.

---

### Post by NoaHall on 2009-10-08
Right, the double kernels are normal. 

Try using the one you aren't booting into right now. If that doesn't work, press "e" on the selection.

---

### Post by gendoikari1 on 2009-10-08
> **QIII said:**
> That in itself is not bad.

You have your choice of loading either of the two kernels.  I like to keep one back just in case I run into problems with a new one.

Try using the older one (.11) and see what happens.
All right, I'll try the second one.

---

### Post by QIII on 2009-10-08
If that doesn't work, could you jot down the exact text of the message you get?

---

### Post by oldsoundguy on 2009-10-08
that is the "restore point" built into Ubuntu and other builds.  
That is NOT bad .. that is GOOD.

The grub menu also gives you the repair options .. another GOOD thing

As to your crash, could well be that you toasted something by leaving it on overnite without extra cooling.

Run your Ubuntu boot disk and run the memory test option to check THAT portion.

CPU problems can be tested by getting the Hirens boot disk (free on line) and running some of the many available stress tests on the CPU by booting with same.

---

### Post by QIII on 2009-10-08
> **oldsoundguy said:**
> 
As to your crash, could well be that you toasted something by leaving it on overnite without extra cooling.


I fear you may be on to a brutal truth with a laptop.  Let's hope the OP is not in that predicament.

---

### Post by gendoikari1 on 2009-10-08
> **QIII said:**
> I fear you may be on to a brutal truth with a laptop.  Let's hope the OP is not in that predicament.
Yeah, its a laptop. On the other hand, it never froze if I left it on overnight when it had XP (2005-a few days ago).

I booted into the -11 kernel, and it didn't freeze after a minute, which is good. Thanks!

---

### Post by QIII on 2009-10-08
OK.  Use that kernel for now.

You may want to cruise launchpad and see if there is an issue with your specific hardware and the newer kernel.

---

### Post by gendoikari1 on 2009-10-08
Well, the -11 kernel froze after several minutes, so it still isn't a permanent solution. Still, its better than a few seconds. I'm retrying the -15 kernel to see if anything changed.

---

### Post by NoaHall on 2009-10-08
Hm. What is this "freezing" ? Try booting the "recovery" mode of .15 

It should tell us more about the kernel panic I expect you are having.

---

### Post by Zoot7 on 2009-10-08
I'd a lot of problems with the 2.6.28-15 kernel under Jaunty. Sound didn't work and it used to randomly lock up on me after I upgraded to it, I also used to randomly get kernel panics upon shutdown. Based on the googling I did it seems the problems were related to the kernel itself rather than Ubuntu. I recently upgraded to 2.6.31 and everything is as it should be once again.
Anyway, 2.6.28-11 still worked okay after my fiasco with 2.6.28-15, so I'd say stick with that for now, if that works for you. ;)

---

### Post by gendoikari1 on 2009-10-08
> **NoaHall said:**
> Hm. What is this "freezing" ? Try booting the "recovery" mode of .15 

It should tell us more about the kernel panic I expect you are having.
It just stops. Mouse stops, keyboard stops, anything on screen stops. 

I ran memtest86+, and it said there are no errors. I downloaded Hiren's BootCD, and ran the PC-Check utility. I made it run the Processor and Memory tests, but it froze (the clock and test stopped) when it tried to start the Memory test. The Processor test reported that everything was working, anyway.

I'm going to reboot into .15 Recovery Mode, and see what I can get from there. If nothing, then I'll try .11 Recovery Mode.

---

### Post by LinuxRocks9.04 on 2009-10-09
> **Zoot7 said:**
> I'd a lot of problems with the 2.6.28-15 kernel under Jaunty. Sound didn't work and it used to randomly lock up on me after I upgraded to it, I also used to randomly get kernel panics upon shutdown. Based on the googling I did it seems the problems were related to the kernel itself rather than Ubuntu. I recently upgraded to 2.6.31 and everything is as it should be once again.
Anyway, 2.6.28-11 still worked okay after my fiasco with 2.6.28-15, so I'd say stick with that for now, if that works for you. ;)
I had the same problem with the sound after upgrading to the -15 kernel in Jaunty. I recently upgraded to Karmic to check for bugs, and the sound was fixed. And about the problem, the freezing might be from errors with the kernel interacting with the distro version, because I have seen many posts about that. If you know how to, try upgrading the kernel and see if anything changes.

---

### Post by gendoikari1 on 2009-10-09
> **LinuxRocks9.04 said:**
> I had the same problem with the sound after upgrading to the -15 kernel in Jaunty. I recently upgraded to Karmic to check for bugs, and the sound was fixed. And about the problem, the freezing might be from errors with the kernel interacting with the distro version, because I have seen many posts about that. If you know how to, try upgrading the kernel and see if anything changes.
Sadly, I don't know how to. I have the 2.6.31.3 kernel (latest stable from kernel.org) in an archive, but that's it.

---

### Post by gendoikari1 on 2009-10-09
> **gendoikari1 said:**
> Sadly, I don't know how to. I have the 2.6.31.3 kernel (latest stable from kernel.org) in an archive, but that's it.No matter, I found the 2.6.31.3 kernel as a .deb package (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.3/)).

---

### Post by Zoot7 on 2009-10-09
Just bear in mind that upgrading the kernel to an entirely new version will require you to re-install your graphics driver if you're using either the ATi or nVidia driver already.

---

### Post by rogerp1 on 2009-10-10
I tried upgrading to the .31.3 kernel which seemed to stop the freezing problems I was having but I stopped getting jaunty updates and got Karmic ones which Borked my system.

How do I install the kernel and stop it updating to Karmic?

---

### Post by Zoot7 on 2009-10-10
> **rogerp1 said:**
> I tried upgrading to the .31.3 kernel which seemed to stop the freezing problems I was having but I stopped getting jaunty updates and got Karmic ones which Borked my system.

How do I install the kernel and stop it updating to Karmic?
You shouldn't be getting Karmic updates if you're using Jaunty. Did you add some karmic repositories or something?
Also bear in mind that any version of Ubuntu doesn't receive kernel updates - just patches eg. 2.6.28 -> 2.6.28-15. It's one of the reasons Ubuntu is as stable as it is.

The best way to install a new kernel I find is to do this:
Go Here:
**[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")**
Lets say for example you want to install 2.6.31-3
Go to the page for that kernel and download the following packages:
```
linux-headers-2.6.31-02063103_2.6.31-02063103_all.deb
linux-headers-2.6.31-02063103-generic_2.6.31-02063103_i386.deb
linux-image-2.6.31-02063103-generic_2.6.31-02063103_i386.deb
```

or for 64bit
```
linux-headers-2.6.31-02063103_2.6.31-02063103_all.deb
linux-headers-2.6.31-02063103-generic_2.6.31-02063103_amd64.deb	
linux-image-2.6.31-02063103-generic_2.6.31-02063103_amd64.deb
```

Then install them in the order they're listed above by using
```
sudo dpkg -i "packagename"
```

You'll be prompted to update grub's menu.lst during installing the last package - tell it to do so. Then reboot, and select the new kernel.

---

### Post by rogerp1 on 2009-10-11
Thanks Zoot, I think I added the mainline PPA as a repo

---

