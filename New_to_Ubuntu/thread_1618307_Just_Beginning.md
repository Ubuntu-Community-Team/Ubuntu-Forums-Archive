---
title: "Just Beginning"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by kaiser0792 on 2010-11-10
Hello to the Ubuntu Community. I am pleased to become a part of the community.

I am brand new to Ubuntu.  I installed Ubuntu v.10.10 last night and am running it via VMware Player so as to run it concurrently with Windows 7 on my PC.  I am beginning work on a computer engineering degree and my purpose for installing Ubuntu was to gain some experience with the Linux OS (of which currently I have none).

I have been informed that I will be programming in C++ and that it will have to be compiled on a Linux system, as that is what the University is currently running in their Programming Labs.  I have done some C++ (Windows) programming, but have never worked with Linux. I installed Ubuntu hoping to be able to work on projects on my home computer rather than living in the school's computer lab. 

The Ubuntu installation seems to be okay, but I have no access to peripherals, i.e., CD ROM Drive, sound card, or printer.  How do I load software, such as a C++ compiler that I have a disc for or play music? 

Thank You.

---

### Post by jimmycross on 2010-11-10
Hi there beginner,

I would like to follow your learning process through this forum, I think. I'm pretty new to the whole thing too. 

Starting with the forums was a good way to go- these people know the answers. Search for people who have asked questions that you want answers to. You can't really go wrong that way. 

As for software, look in your applications menu. There you'll find the "ubuntu software center" where you have free access to anything under the sun. 

Congrats on joining the world of open source. Cheers,

Jimmy

---

### Post by Goldfissh on 2010-11-10
You have to enable your peripherals through VMWare Player before you can access them in your virtual machine. Check the menus at the top, it should be in there somewhere :D

---

### Post by kaiser0792 on 2010-11-10
Thank You.

---

### Post by kaiser0792 on 2010-11-10
Thanks, Jimmy. Lets keep in touch. 2 heads are always better than one!

---

### Post by Goldfissh on 2010-11-10
I too am fairly new to Ubuntu and Linux as a whole. That said, it's surprising how much you find yourself picking up!

Keep reading, doing your research and trying things out for yourself. You'll pick it up in no time!

---

### Post by amjjawad on 2010-11-10
Hello and welcome everyone :)

Sorry, can't answer your question but I'd like to share this link with you:
[http://ubuntuforums.org/showpost.php?p=1983565](http://ubuntuforums.org/showpost.php?p=1983565)

Hope you'll find some useful stuff :)

As for your main question, you need to wait for someone who has more experience in VM.

Good luck!

---

### Post by kaiser0792 on 2010-11-10
Thank You

---

### Post by Goldfissh on 2010-11-10
> **amjjawad said:**
> Hello and welcome everyone :)

Sorry, can't answer your question but I'd like to share this link with you:
[http://ubuntuforums.org/showpost.php?p=1983565](http://ubuntuforums.org/showpost.php?p=1983565)

Hope you'll find some useful stuff :)

As for your main question, you need to wait for someone who has more experience in VM.

Good luck!

I think I might have already answered the main question :D

---

### Post by amjjawad on 2010-11-10
> **Goldfissh said:**
> I think I might have already answered the main question :D

And I hope it's right as I have never tried VM before :)

---

### Post by ShakeyJake on 2010-11-10
What are you using to run the VMs? In VirtualBox you select the VM, go to 'Settings' and then 'Storage'. Add a device to the IDE Controller section, and make it your CD drive, usually called 'Host Drive *NameOfYourCDDriveHere*'. Mine is 'Host Drive TSSTcorp CD DVDRW'.

---

### Post by kaiser0792 on 2010-11-10
Thanks to those that have offered help.

I checked my VMWare Player settings and it is set to recognize my CD ROM but still doesn't. 

My keyboard works fine, my mouse works fine.  My printer recognizes Ubuntu, but when I try to print, I get a page with some kind of header and then my printer shoots out several blank pages, but doesn't print the desired text.

Ubuntu is set to recognize my sound driver and CDROM, but neither is accessible. I need to be able to access my music from my main computer (Windows) and be able to play audio CD's and more importantly be able to load software from CD.

I'm at a loss.

---

### Post by onaridge on 2010-11-10
There is a Virtualization section under other discussions, devoted to that, where you may get more help. :-)

---

### Post by Mahngiel on 2010-11-10
> **kaiser0792 said:**
> 
I have been informed that I will be programming in C++ and that it will have to be compiled on a Linux system, as that is what the University is currently running in their Programming Labs.  I have done some C++ (Windows) programming, but have never worked with Linux. I installed Ubuntu hoping to be able to work on projects on my home computer rather than living in the school's computer lab. 


Check the repositories (Ubuntu Software Center or Synaptic Package Manager) for Eclipse.  It's a nifty IDE C++ compiler.

---

### Post by lkraemer on 2010-11-10
**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.

[B]
TYPICAL COMPILE STEPS: (from within your source directory)[/B]
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


LK

---

