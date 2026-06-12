---
title: "Linux newbie, old machine, network not-work"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by xmfclick on 2007-02-28
Totally new to Linux, decided to dip a toe in. Zapped an old machine (Dell Dimension 266, 512MB RAM, 6GB HDD) and installed Ubuntu 6.06. Runs pretty slow, but runs, looks nice. However, it doesn't detect the Ethernet card (an old ISA card made by Genius; probably NE2000-compatible, but I have no documentation anymore). Being so new to Linux, I find the suggestions out there on how to get the card working somewhat opaque (e.g. TLDP: "build a new kernel with a whole range of drivers" -- WHAT???)

Can anyone point me to an Ubuntu-centric set of instructions that might help me get the darned thing working? (I understand that without a network connection I'm going to find it difficult to get Ubuntu up-to-date).

Many thanks in anticipation...

---

### Post by doobit on 2007-02-28
> **xmfclick said:**
> Totally new to Linux, decided to dip a toe in. Zapped an old machine (Dell Dimension 266, 512MB RAM, 6GB HDD) and installed Ubuntu 6.06. Runs pretty slow, but runs, looks nice. However, it doesn't detect the Ethernet card (an old ISA card made by Genius; probably NE2000-compatible, but I have no documentation anymore). Being so new to Linux, I find the suggestions out there on how to get the card working somewhat opaque (e.g. TLDP: "build a new kernel with a whole range of drivers" -- WHAT???)

Can anyone point me to an Ubuntu-centric set of instructions that might help me get the darned thing working? (I understand that without a network connection I'm going to find it difficult to get Ubuntu up-to-date).

Many thanks in anticipation...

I don't think you need to build a new kernel, however, since your network card is an ISA card, you may need a 2.4 kernel, actually. There are 2.4.xx kernels, headers and images  available by using Synaptic. Once you have downloaded and installed one, then you can select either kernel in Grub. I'm not sure how the 2.4.xx will work with some of your other software, however.

Are you sure the card is not being recognized at all? If you type ```
sudo ifconfig eth0 up
``` in a termnal, then type ```
sudo ifconfig
``` again, what do you get?

Also, if you have an available PCI slot, then you can get a PCI ethernet card for about $15.

---

### Post by xmfclick on 2007-02-28
> There are 2.4.xx kernels, headers and images available by using Synaptic. Once you have downloaded and installed one, then you can select either kernel in Grub
Ooooh. Now, when I said I was a Linux newbie, I *meant* newbie. What's a Synaptic? Who is Grub? How do I download a kernel/header/image if I can't get my network card working? (I'm on a Windows machine at the moment). 

Trouble with Linux is that people who understand how it works don't realise (or have forgotten) how difficult it is for those of us who don't! I really am after a simple guide. I had hoped one day to master this "Hang on a minute while I build a new kernel" stuff, but I'm feeling a little discouraged at the moment. 

BTW, the "sudo ifconfig" thing comes up with words along the lines of "What???" -- i.e. it definitely doesn't see the ethernet card.

---

### Post by doobit on 2007-02-28
> **xmfclick said:**
> Ooooh. Now, when I said I was a Linux newbie, I *meant* newbie. What's a Synaptic? Who is Grub? How do I download a kernel/header/image if I can't get my network card working? (I'm on a Windows machine at the moment). 

Trouble with Linux is that people who understand how it works don't realise (or have forgotten) how difficult it is for those of us who don't! I really am after a simple guide. I had hoped one day to master this "Hang on a minute while I build a new kernel" stuff, but I'm feeling a little discouraged at the moment. 

BTW, the "sudo ifconfig" thing comes up with words along the lines of "What???" -- i.e. it definitely doesn't see the ethernet card.

Sorry! The CDs should come with a manual! Anyway, Synaptic is under system in the menus. Synaptic is the program that list all of the possible software you can download and install in Ubuntu. You can search through thousands of programs with it, including kernels. The kernel is the part of the operating system that "drives" the computer and links parts of the hardware with parts of the software. Ubuntu comes with kernel version 2.6.xx which is for more modern hardware. Kernel 2.4.xx has drivers for older hardware, including legacy and ISA hardware. You don't need to compile it (that's downloading the source and making a custom kernel for your hardware) just use the one that's already available. Grub is the bootloader that tells your hardware where to find the kernel and how to start the boot process. When you have more thatn one kernel, they are both placed in a list so you can choose which one you want to use by hitting the Esc key when you boot up.

---

### Post by xmfclick on 2007-02-28
Ah, Synaptic -- that's the thing that lists all the packages I could install, then complains bitterly about missing dependencies no matter what I select, and won't actually let me do anything. Gotcha! I have heard about Dependency Hell in Linux, now I've experienced it for myself. 

I'm getting very frustrated here. I've wasted the last 2 hours trying to find a page I saw earlier that explains how to configure the system for ISA network cards. My system just doesn't see this card (ironically, Windows saw it automatically on first install, years ago). And, oddly (and differing from the on-line documentation) if I go to System>Administration>Network Settings, the dialog (a) only shows me a modem connection called ppp0, and (b) has no Add or Delete buttons, so I can't even add a connection manually. Back at the terminal, I've tried ifconfig but it only comes up with info on the local loopback interface. What can I do? HELP!!

BTW, I downloaded something called kernel-image-2.4.27-3-586tsc_2.4.27-10sarge5_i386.deb from the Debian site -- what would I do with it? (It's on my Windows PC at the moment.) Thanks!

---

### Post by Chappy7777 on 2007-02-28
xmfclick,

don't feel too bad, this is my 1st post in Ubuntu's forum, and I can't get the thing to type using larger letters. I tried the Sizes thing above and that didn't help. I think it assumes I know Linux. Wrong. Like you I am a complete newbie to Linux. I am a geek at Windows, but can't do anything much w/Linux. I had Xandros on my Linux designated PC for awhile, but I found it required me to lnow Linux. The funny part about this is that a year or so ago, when I decided to try Linux, Xandros was the Linux du jour. It was quickly replaced w/Ubuntu.

Anyhow, I am determined to learn how to use Ubuntu. I love the way it looks and I know it can be made to serve us, not the way it is now, me serving Ubuntu. Tomorrow I am going to buy a book called "Ubuntu for the Non-Geek". There are a number of good books out there on Linux, and I figure that is the only way I will be able to do this. Not that the forums aren't great, but it's too frustrating to be going thru what you are so adequately stating. 

So, spend a few bucks and grab a copy of "Moving to Ubuntu Linux". Take a look at Marcel Gagne's site, [www.marcelgagne.ca](www.marcelgagne.ca). Also, there are a number of sites that have Linux lessons for free. You can do that reading on M$oft. 

Main thing, don't take this as a personal assault. Linux is not easy, but if all these other folks can get the hang of it, so can we.

Hang in and God bless,

Chappy

---

### Post by Chappy7777 on 2007-02-28
Sorry, make that [www.marcelgagne.com](www.marcelgagne.com)

Chap

---

### Post by doobit on 2007-03-01
> **xmfclick said:**
> Ah, Synaptic -- that's the thing that lists all the packages I could install, then complains bitterly about missing dependencies no matter what I select, and won't actually let me do anything. Gotcha! I have heard about Dependency Hell in Linux, now I've experienced it for myself. 

I'm getting very frustrated here. I've wasted the last 2 hours trying to find a page I saw earlier that explains how to configure the system for ISA network cards. My system just doesn't see this card (ironically, Windows saw it automatically on first install, years ago). And, oddly (and differing from the on-line documentation) if I go to System>Administration>Network Settings, the dialog (a) only shows me a modem connection called ppp0, and (b) has no Add or Delete buttons, so I can't even add a connection manually. Back at the terminal, I've tried ifconfig but it only comes up with info on the local loopback interface. What can I do? HELP!!

BTW, I downloaded something called kernel-image-2.4.27-3-586tsc_2.4.27-10sarge5_i386.deb from the Debian site -- what would I do with it? (It's on my Windows PC at the moment.) Thanks!

You shouldn't be having any dependency issues if you are using Synaptic and have not changed anything since you installed Ubuntu. All of the dependencies (these are just other programs that the program you are trying to install need to operate) should be linked already and be in the install list and download automatically. Dependency hell only exists with rogue packages that you try to install from private download sites. Even those have ways of solving dependency issues. There are also no dependencies in installing a kernel that Synaptic will not resolve. I'm trying to point you in this direction because your previous information was that you needed a different kernel. It would make sense if the drivers are not open source for that card and you have to get them from the manufacturer and compile them into the kernel, but normally that is not the case for networks cards, especially older ones. 

Network cards normally are recognized right away with no issues, so I'm not sure what the problem is with yours, except that it's an ISA card, but even with that, there should not be this issue. If you use Synaptic to get a 2.4.26 kernel, for example, and just follow the on screen instructions to download and install it, then you should have a working system. You really shouldn't try anything with the other .deb that you downloaded.

Yes, Windows should have seen the card years ago because it's an old card. Linux will also see the card, but the more modern kernels may have been stripped of older drivers to keep them light. I'm not saying that this is the case with your card, it's just impossible for me to know exactly so we need to try things. So use Synaptic and get that 2.4.26 kernel. Use Synaptics search filter and enter linux-kernel 2.4.26 
There will be quite a few things in the list, but one of them should indicate that it's the thing you need to install the complete kernel and headers that you need.

---

### Post by xmfclick on 2007-03-01
Trouble is, it's a bit of a chicken-and-egg situation -- Ubuntu can't see the NIC ("sudo ifconfig eth0" returns "device not found"), but it needs the NIC in order to be able to download a kernel that might be able to see the NIC... 

Although, as I said, I did download a 2.4 kernel from the Debian site (a file called kernel-image-2.4.27-3-586tsc_2.4.27-10sarge5_i386.deb), which is now sitting on my Windows box. Thing is, I have absolutely no idea what to do with it. Is it of any use?

Anyway, I yanked the NIC out and rummaged around on the web and it looks like it's an NE2000-compatible. Unfortunately I haven't got any notes on what IRQ or address range it's set up to use, and I can't find any technical notes on the web. (I've sent a message to Genius, but they don't seem to make NICs any more.)

So the question is, how can I get Linux to find the NIC, even if it's by trial and error? I have the feeling that there's a config file somehwere (probably hiding under /etc ?) where I could try typing in some cryptic character string with an "ne" in it somewhere. Any thoughts?

~~~~~~~

BTW, the thing with Synaptic, I think, is that it needs a network connection in order to work properly -- which it doesn't (see above). Standalone it appears to be totally useless.

---

### Post by TheWildCat on 2007-03-01
I'm also a Linux Newbie.  Find, download, and install Puppy Linux, it works on most old computers although not as fancy.

The first Linux OS to be compatible with computer hardware and have to some sort of decent documentation will be the one that wins the Linux contest to be the de facto opensource Linux OS.  Right now it seems like all of the Linux programmers are just trying to get their own system working rather than cross-platform.  Which is fine since its freeware and more of a hobby.  

But if Ubuntu wants to be the Linux for "Humans" then it first must be an OS friendly to "Hardware and Documentation" rather than just having a cunning GUI and website.  I hate to be harsh here but I'm just really frustrated playing around with this OS.

---

### Post by doobit on 2007-03-01
> **xmfclick said:**
>  Any thoughts?

~~~~~~~

BTW, the thing with Synaptic, I think, is that it needs a network connection in order to work properly -- which it doesn't (see above). Standalone it appears to be totally useless.

I'm using 6.10 right now and I can't remember for sure if 6.06 had this, but in 6.10 you can enable Synaptic to look for files on the live CD. There are some things on the live CD that are not installed by default, and one of them may be a 2.4.26 kernel.
<edit>

OK, I'm going to suggest something that I thought about the first time, but it only just now came back to me. There is a distribution that is only 50MB in total size and is based on the 2.4.26 kernel. It's called DamnSmall Linux and it will run pretty well on your machine, and might already recognize your ISA NIC. Download and burn on with your Windows machine and try it out:

[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

---

### Post by xmfclick on 2007-03-01
Haha. I got the Official Fedora Companion from the library this afternoon, comes with a 2-CD install set, I'm giving that a try right now.

Thing I find frustrating with everything I've seen to do with Linux is that it's written from the point of view that either (a) you know what you're doing already, or (b) you barely know what a mouse is, but your Linux distro will install perfectly first time out. I've surfed around a lot and got the few books out that the library has, but I haven't seen anything that explains the structure of Linux, the installation procedure, networking etc. but aimed at a competent Windows hacker. I guess all the Linux-loving kiddies get taught this stuff at university and get the chance to ask real people when they run into problems. My problem is I don't know anyone who knows about Linux. 

Anyway, the Fedora installer is currently reformatting the hard disk, and I'll report back on whether Fedora finds the NIC. Later ...

---

### Post by bradford72 on 2007-03-01
xmfclick, i'm new with this linux deal too, but really...I mean REALLY like it now that i've got it to work a bit...so, here's a thought...what do you get when you go "System->Administration->Networking" from the menu bar at the top of the screen?

---

### Post by xmfclick on 2007-03-01
I get a tabbed dialog that shows a modem and nothing else. And, the buttons down the right-hand side of the dialog don't include Add or Delete -- unlike in the documentation -- so there's no way of adding a new network device.

---

### Post by doobit on 2007-03-01
> **xmfclick said:**
> Haha. I got the Official Fedora Companion from the library this afternoon, comes with a 2-CD install set, I'm giving that a try right now.

Thing I find frustrating with everything I've seen to do with Linux is that it's written from the point of view that either (a) you know what you're doing already, or (b) you barely know what a mouse is, but your Linux distro will install perfectly first time out. I've surfed around a lot and got the few books out that the library has, but I haven't seen anything that explains the structure of Linux, the installation procedure, networking etc. but aimed at a competent Windows hacker. I guess all the Linux-loving kiddies get taught this stuff at university and get the chance to ask real people when they run into problems. My problem is I don't know anyone who knows about Linux. 

Anyway, the Fedora installer is currently reformatting the hard disk, and I'll report back on whether Fedora finds the NIC. Later ...

OK, hold the fort! Don't install anything new yet! I just got home to try to see if the drivers for that card are on my Ubuntu machine and they are!
Do this in a terminal:
```
sudo modprobe ne
```
enter your password and see if you get any feedback in the terminal
If you get nothing or positive feedback that indicated the module loaded, the do:
```
sudo ifconfig eth0 up
``` 
then
ifconfig

---

### Post by xmfclick on 2007-03-01
> OK, hold the fort! Don't install anything new yet! 
Sorry, too late...

I tried "sudo ifconfig eth0 up" earlier and it came back with "device not found". But I didn't know about modprobe -- what is it, exactly?

Still Windows 1, Linux 0 :o(

> I just got home to try to see if the drivers for that card are on my Ubuntu machine and they are!
This may be a dumb question, but *how* do you know which are the drivers for that NIC? I mean, how (in Linux) do you tell what's a driver, and which card it's for?

~~~~~

[Latest update, 30 mins later ...] Fedora is up and running (noticeably faster than Ubuntu) and has found my network card. Dunno if it can actually connect to the Internet yet, as I have to replug the network cable (which is a job for tomorrow). So it's Windows 1, Fedora 1 (well, a half so far), Ubuntu 0. Sorry Ubuntu ...

Oh, and thanks to doobit for the pointer to damnsmalllinux -- I may have a play with that too, just for fun. Do you know if it can be set up as a dedicated Router/NAT box, or can you suggest another distro for that? (there used, a long time ago, to be something called the Linux Router Project, but I think it expired).

Anyway, thanks to everybody who has offered help and suggestions. I still wish there was some intermediate-level Intro to Linux book, or website ... hey, maybe *I* could do that! (once I've played a bit more).

---

### Post by doobit on 2007-03-01
> **xmfclick said:**
> Sorry, too late...

I tried "sudo ifconfig eth0 up" earlier and it came back with "device not found". But I didn't know about modprobe -- what is it, exactly?

Still Windows 1, Linux 0 :o(


This may be a dumb question, but *how* do you know which are the drivers for that NIC? I mean, how (in Linux) do you tell what's a driver, and which card it's for?

~~~~~

[Latest update, 30 mins later ...] Fedora is up and running (noticeably faster than Ubuntu) and has found my network card. Dunno if it can actually connect to the Internet yet, as I have to replug the network cable (which is a job for tomorrow). So it's Windows 1, Fedora 1 (well, a half so far), Ubuntu 0. Sorry Ubuntu ...

Oh, and thanks to doobit for the pointer to damnsmalllinux -- I may have a play with that too, just for fun. Do you know if it can be set up as a dedicated Router/NAT box, or can you suggest another distro for that? (there used, a long time ago, to be something called the Linux Router Priject, but I think it expired).

Anyway, thanks to everybody who has offered help and suggestions. I still wish there was some intermediate-level Intro to Linux book, or website ... hey, maybe *I* could do that! (once I've played a bit more).

modprobe just manually loads a driver from the modules directory. There are always a bunch of drivers in there that are not compiled into the kernel. I found that driver was for your card by searching Google Linux for the card name.
DamnSmall Linux is a blast. It's very fast on old machines. I had it on a 200MHZ Toshiba laptop for a while.

---

### Post by bradford72 on 2007-03-01
well, bummer...that's all I had....as for the new kernel that you downloaded...is it a "source code" kernel or a "binary" kernel?  If you got the source code, you'll have to compile it to create an image, burn the ISO image to a cd, and then boot from the image.  How is that done you ask?  I don't know, but I'll bet someone here does!

---

### Post by xmfclick on 2007-03-01
bradford72:
> as for the new kernel that you downloaded...is it a "source code" kernel or a "binary" kernel
It was an image. At least, I guess that's what **kernel-image-2.4.27-3-586tsc_2.4.27-10sarge5_i386.deb** would be. As you can tell from my question (i.e. "what do I do with it now I've downloaded it?") I haven't got much of a clue about anything Linux. So I'd have to burn it to a CD and then boot the CD, huh? Then what? Surely installing an application under Linux can't be as complicated as installing it under Windows? Don't you do it like you used to in DOS, i.e. use XCOPY? (which is what the new (old) .NET software installation system is, that is, basically XCOPY)? I must admit this whole "package" thing totally baffles me. For example, Ubuntu comes with a few apps that I'd really like to be able to run on my new Fedora system -- is it possible for me to install them from the Ubuntu disk? If so, how? If not, why not?

doobit:
Thanks for your help. I still don't understand, though -- **how** do you know that **ne** is the driver for the NE2000 card, and where does it live? Is there a file called ne sitting in a directory somewhere? Damn this is different from Windows..

---

### Post by doobit on 2007-03-02
> **xmfclick said:**
> bradford72:

It was an image. At least, I guess that's what **kernel-image-2.4.27-3-586tsc_2.4.27-10sarge5_i386.deb** would be. As you can tell from my question (i.e. "what do I do with it now I've downloaded it?") I haven't got much of a clue about anything Linux. So I'd have to burn it to a CD and then boot the CD, huh? Then what? Surely installing an application under Linux can't be as complicated as installing it under Windows? Don't you do it like you used to in DOS, i.e. use XCOPY? (which is what the new (old) .NET software installation system is, that is, basically XCOPY)? I must admit this whole "package" thing totally baffles me. For example, Ubuntu comes with a few apps that I'd really like to be able to run on my new Fedora system -- is it possible for me to install them from the Ubuntu disk? If so, how? If not, why not?

doobit:
Thanks for your help. I still don't understand, though -- **how** do you know that **ne** is the driver for the NE2000 card, and where does it live? Is there a file called ne sitting in a directory somewhere? Damn this is different from Windows..

The kernel is not an application, so you don't install it like one. Compiling from source can be a long and complicated process and I don't recommend it for beginners, especially when it's not necessary. Compiling is how you build a kernel that has all of the specific drivers for your hardware, and few of the others. Generic kernels have a huge collection of drivers and are designed to operate on as much hardware as possible. The developers try to strike a balance by not including drivers for older equipment in newer kernels. However, if you compile it yourself, then you can include whatever drivers you want. Also, many of the drivers that are not compiled into the generic kernel are placed in a directory  and can still be loaded manually using modprobe or insmod commands. The location is usually /lib/modules/
Here is a How To on the subject:  [http://www.faqs.org/docs/kernel/x45.html](http://www.faqs.org/docs/kernel/x45.html)

You can find a lot about Linux and the programs in Linux distributions by using the How To pages and the "Man" pages (manuals) on the internet. You can even access man pages in the terminal by typing man <the command you want info on>

I did a search on network cards with the chipset on your card and then the Linux drivers for it. When I used the terminal to try to load the module name, the terminal returned an error that told me the driver location, but that the device for the driver wasn't present (because I don't have the NIC you have). 

Linux is different from Windows, but similar in some ways! The names and locations are different, but the fact that stuff is organized in directories and files is the same.

---

