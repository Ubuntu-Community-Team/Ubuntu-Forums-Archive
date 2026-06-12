---
title: "COMPLETELY new to changing my OS."
date: 2011-01-07
forum: New to Ubuntu
---

### Post by antiprice666 on 2011-01-07
First off, I am just starting my switch from Window (using XP home edition) to Linux so I am apologizing ahead of time for any misuse of terminology or what not.  
     My first computer was a commodor vic 20 and have been monkeying around with them as a hobby for quite some time.  Don't know how relevant this is but just wanted to let whomever know my background.
     I am just starting my research for the switch and am getting my feet wet by teaching myself to dual boot.  My goal is to ditch Windows completely.
     It appears that the distro (just learned that one) I choose should be based on my hardware configuration and how I plan to use my OS which leads to my first question...What distro should I use?
     I built my rig last year.  Here it is.
   
    MSI 790fx-gd70 
    AMD Phenom IIx3 720 64 bit (black box)
    ATI Radeon HD4800
    4 gigs DDR3 ram (dont have model or brand handy)

     I would prefer to use a 64 bit distro but I am coming to understand that some software is buggy in 64 bit so I am not tied to using 64 bit.  
     At the moment my computer is basically just a desktop for home use.  I built it for gaming and my goal is to get as much out of it (performance wise) as possible.  I have stopped gaming but will probably go back to it to test my system.   However I would like to use my computer for more then just gaming.  Maybe get into building a server and start hosting.  I just figured this would be the best way for me to "break into" the whole Linux thing.
     Sorry if I am reposting a thread but I tried using the search and couldn't get answers that were specific to my questions.  Thanx in advance to any answers given to this thread.

---

### Post by bowens44 on 2011-01-07
> 
     I would prefer to use a 64 bit distro but I am coming to understand that some software is buggy in 64 bit so I am not tied to using 64 bit.  




This is a commonly repeated myth. 64 bit is just as stable as 32 bit. There may be one or two exceptions but I haven't encountered them. Use the 64 bit you won't be sorry. 

Of course you should probably start by booting from the live cd to see how it performs.

---

### Post by hansolo4949 on 2011-01-07
Yes, you should use 64-bit. I use it on my laptop, and I haven't had one problem with it, except that it can't run 32 bit programs. I would go for Ubuntu 10.10 maverick Meercat, and if you're not sure, just put it on a cd, and liveboot it. please not it will run much faster when it's installe on your computer. Considering your specs, it should FLY on yours.

Hope that helps!

hansolo4949

---

### Post by wyliecoyoteuk on 2011-01-07
Definitely test it with a live CD, or better still, a Live USB install, which will be faster.

Instructions for making a live boot USB stick here:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And good luck!

---

### Post by antiprice666 on 2011-01-08
thank you 8^)

---

### Post by 3rdalbum on 2011-01-08
> **antiprice666 said:**
> 
     It appears that the distro (just learned that one) I choose should be based on my hardware configuration

Not really so much. If you've got limited system resources, then choose something lightweight. If your machine is average or powerful, then you can go with anything.

> I would prefer to use a 64 bit distro but I am coming to understand that some software is buggy in 64 bit so I am not tied to using 64 bit.

Not buggy - it's the same code, just with a bigger address space. On Windows there can be compatibility problems. On Linux there aren't. Go 64-bit.

---

### Post by oldos2er on 2011-01-08
> **hansolo4949 said:**
> Yes, you should use 64-bit. I use it on my laptop, and I haven't had one problem with it, except that it can't run 32 bit programs. 

Install ia32-libs to run 32-bit apps on 64-bit Ubuntu.

---

### Post by akand074 on 2011-01-08
You should be able to run just about any distribution. I would recommend you start with Ubuntu, it's probably the best distribution for people who are new to GNU/Linux based OS. Use the 64 bit version, definitely.

---

### Post by sandyd on 2011-01-08
You should be able to run almost any linux distro with those specs.

The only issue may be with the ATI card; If your experiencing issues with AMD's drivers and find the default drivers slow, check out [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

If your installing 64-bit, check out the link in my sig (adobe flash tools) or lovinglinux's Flash-AID extensions for firefox

---

### Post by antiprice666 on 2011-01-10
Thanks so much for the replys.  Next question is how big of a USB stick do I need?  I have a couple but they are small.  Have no problem getting one just need to know how big. (insert off color joke here)..lol

I may be getting ahead of myself but how much ram does Ubuntu recognize?  My MB will support 16 gigs but my current OS (Windows XP) only recognizes 3.5 gigs.  Just curious...

---

### Post by jmszr on 2011-01-10
antiprice666,

You  _can_ install to a 2GB usb, but I'd recommend 4GB to allow room for application installation and any data you may wish to save. Here is another link pertaining to installing Ubuntu to a flashdrive with persistence (allows saving of settings, new applications, and data): [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/) .

As far as RAM :"The Linux kernel used by 64-bit Ubuntu can theoretically recognize up to 17.2 billion GB of physical memory, but this is subject in practice to hardware limitations. Current AMD64 implementations allow for up to 256TB of physical memory. Current Intel 64 implementations allow for up to 1TB of physical memory." In practical terms, you should be good-to-go.

Hope that helps.

Edit: +1 for 64-bit

---

