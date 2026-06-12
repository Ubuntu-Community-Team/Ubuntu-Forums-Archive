---
title: "EPSON LQ850 printing problems"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by TerrieG on 2009-12-14
I am new to Ubuntu. My son downloaded ubuntu 9.10 onto his old computer and gave it to me. I am not online (yet). I want to use my old EPSON LQ850 dot matrix printer to get started. I plugged it into what I think is the parallel port, downloaded the driver from linuxprint.org, used admin->printing->new and installed the driver. 
 
So now I seem to be able to communicate with the printer but not very well. 
 
It takes 1 minute to print 1 line of my file 
and
It prints each line twice
 
 
1. Do I need to re-install something like ghostscript?
 
2. Do I need to be logged in as root to re-install software? 
 
3. My son installed and I don't know yet if he has the root password. Is there a way for me to reset the root password? Or is there a standard root password for when you install Ubuntu 9.10 while online?
 
At first I thought I needed to install foomatic-rip, so I downloaded it and logged in as user, ran 
configure (which gave me warnings)
then
make and got fatal errors - ghostscript/iapi.h no such file
ghostscript/ierrors.h no such file
 
Then I started looking around and found footmatic-rip in /usr/bin
and foomatic in /etc when installation software seemed to be looking for it in /usr/local/etc.
 
So I think there are path problems. Like do I have to edit configure and somehow give it some paths? 
 
It's been a long time since I last was on a linux operating system and I know nothing about installing hardware and software.
 
I would appreciate any assistance.

---

### Post by cariboo on 2009-12-14
Make sure you have the paraport driver installed. T check, open an Applications-->Accessories-->Terminal and type:

```
dmesg | grep para
```

You should see something like this:

```
 dmesg | grep para
[   10.989466] ppdev: user-space parallel port driver
```

---

### Post by TerrieG on 2010-01-05
dmesg | grep para gives me
[###...#] ppdev user-space parallel port driver
and
[.....]  lp0: using parport0(interrupt-driven)
 
What else should I check?

---

### Post by timstewart on 2010-02-07
I have the same problem. The closest drivers I ever got to work were IBM Pro printer (or something like that), but the printing wasn't very fast (no bi-directional). I would really like to use the LQ-850 on a day to day basis but I have never got to the bottom of this one.

Could it be a bios parrallel port setting ? Maybe some legacy para drivers need loading?

---

### Post by TerrieG on 2010-06-15
I am back in pursuit of a solution to my original Epson LQ850 problem posted last December and would really like to get this working.  The newest version of Ubuntu 10.04 LTS now includes the printer driver  but.....  I read on linux open printing forum that it has to be built in to Ghostscript.  I have no idea what that means.  How would I recompile Ghostscript so that Epson LQ850 is built-in?  How does the compile know which drivers to include?  What is the purpose of a ppd vs a dev file?

And I see "timstewart" wants to know too.

---

