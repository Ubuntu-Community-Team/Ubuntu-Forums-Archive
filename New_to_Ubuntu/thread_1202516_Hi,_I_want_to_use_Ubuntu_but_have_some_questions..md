---
title: "Hi, I want to use Ubuntu but have some questions."
date: 2009-07-02
forum: New to Ubuntu
---

### Post by shocktherapyXLI on 2009-07-02
I have a friend that only uses linux and who really like Ubuntu and I have messed around with their computer at their house and I would like to set up Ubuntu on my computer.  I just don't know which version to use the 32 bit or the 64 bit version.  I have Windows Vista Home Premium on my laptop now that I don't really want to use anymore and I don't really have the money to upgrade to Win7 when it comes out because I was laid off due to the bad economy.

I am using the 64 bit live cd right now testing and I beleive I remember seeing that my computer was an i686 Pentium Dual Core, so does that mean that I need the 64 bit or the 32 version?  My friend has told me that if I run through the installer I can dual boot my computer and written down how to do different things that I will need once it is installed like how to get flash and media codecs etc, but I never thought to aks about how to find out which version to use. Is there a way to find this out?  Thanks.

---

### Post by Michael.Godawski on 2009-07-02
hey,

well, the 32 bit version will always work, be it on a 64-bit capable system or on a normal 32 bit system. 

It all depends on the CPU. 

See here:

[LIST]
[*][https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
[/LIST]

---

### Post by austinpsycho on 2009-07-02
i686 suggests 32 bit ;)

---

### Post by cmost on 2009-07-02
Hello and welcome to the world of Linux.  You may choose either the 32Bit or 64Bit version of Ubuntu as your system can handle either (the fact that you've explored the 64Bit live CD is a testament to its compatibility with your system, otherwise it wouldn't have loaded.)  As an absolute beginner, however, I would recommend 32Bit to start as the 64Bit does have some considerations that might make things sticky for a newbie and the performance gains of a 64Bit system are more or less negligible on a system such as yours.

On a side note, you will be able to partition your laptop's hard disk to use both Windows Vista and Ubuntu simultaneously until you get to grips with Linux.

Finally, if you want a super duper easy to use variant of Ubuntu, please check out Linux Mint.  It's fully compatible with Ubuntu but contains a lot of newbie friendly features out of the box.  Check it out here:  [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

Good luck!

---

### Post by frunns on 2009-07-02
You can use either one. I've had problems with the 64bit version, so I'd say the 32bit one is a safe bet. Feel free to try it out though. Fairly specific stuff that can be troublesome as far as I know. :)

---

### Post by austinpsycho on 2009-07-02
though if that's the case; why does a live 64 bit cd work?  Does anybody know if the command line *arch* will return the actual architecture or the current running one?
anyway try it.. if it says i686; stick with the 32 bit version ;)

---

### Post by shocktherapyXLI on 2009-07-02
What would the difference be between the 64 bit and the 32 bit version?  Would the 64 bit get better performance?

I just use the computer for a home set-up really, I just want to be able to play music, use the internet, watch movies and home use really.  Does the 64 bit version run faster than the 32 bit version?

---

### Post by wojox on 2009-07-02
You could look in 

Control Panel > System and Maintenance > System

That should give you info on your laptop.

64 bit is better performance but you need to know if your laptop can handle it.

---

### Post by shocktherapyXLI on 2009-07-02
Oh and I was already using Firefox and Open Office and programs like that anyway so my friend was telling I might as well switch over, I don't play any games really on the computer so from what he was telling me I think this might be the perfect option for me.

---

### Post by shocktherapyXLI on 2009-07-02
> **austinpsycho said:**
> though if that's the case; why does a live 64 bit cd work?  Does anybody know if the command line *arch* will return the actual architecture or the current running one?
anyway try it.. if it says i686; stick with the 32 bit version ;)
That is what I am using right now is the 64 bit live CD and it is working, so does that mean if I install it that it will work too?   Sorry, if I am being a pain in the rear end, I just want to make sure I get the right one installed.  I've had to use my windows rescue disks a couple of times and it takes forever to get it set back up.. LOL

---

### Post by cirabisi2009 on 2009-07-02
[http://wubi-installer.org/](http://wubi-installer.org/)

check it out

---

### Post by verbal.kint on 2009-07-02
you will only get better performance on a 64bit machine with programs that are written specifically for 64bit OS.


I had 64bit installed a while ago but had a lot of trouble with getting flash working in 64bit firefox, ended up using 32bit firefox and when I upgraded ubuntu I just installed the 32bit version

Most programs will be written for 32bit so its only with the odd few programs that you will see a performance gain

---

### Post by Tyke91 on 2009-07-02
> **cirabisi2009 said:**
> [http://wubi-installer.org/](http://wubi-installer.org/)

check it out

why bother? 

Set up a dual boot and you will be fine :D

recommend 32 bit for beginners tho.

---

### Post by Idefix82 on 2009-07-02
> **shocktherapyXLI said:**
> That is what I am using right now is the 64 bit live CD and it is working, so does that mean if I install it that it will work too?

Yes.

I amazed how many people have recommended to use 32 bit without even enquiring how much RAM you have. One of the main differences between 32 and 64 bit is that a 32 bit system can only use about 3.2 GB of RAM. If you have more than that and if you are likely to run memory hungry programs then you are throwing away memory by using a 32 bit OS.

I don't think you should even look at Wubi either. Firstly, if you use a wubi install and Windows breaks down (and it will) then you won't be able to boot into Ubuntu either. Secondly, if you want to eventually delete Windows and use Ubuntu exclusively, you will have to reinstall.

@verbal.kint: installing firefox flash plugin on a 64 bit system is a matter of downloading one file and putting it into the right place. There is a 64 bit plugin available, so no need for 32 bit libraries or anything.

---

### Post by cmost on 2009-07-02
> **Idefix82 said:**
> Yes.

I amazed how many people have recommended to use 32 bit without even enquiring how much RAM you have. One of the main differences between 32 and 64 bit is that a 32 bit system can only use about 3.2 GB of RAM. If you have more than that and if you are likely to run memory hungry programs then you are throwing away memory by using a 32 bit OS.

I don't think you should even look at Wubi either. Firstly, if you use a wubi install and Windows breaks down (and it will) then you won't be able to boot into Ubuntu either. Secondly, if you want to eventually delete Windows and use Ubuntu exclusively, you will have to reinstall.

@verbal.kint: installing firefox flash plugin on a 64 bit system is a matter of downloading one file and putting it into the right place. There is a 64 bit plugin available, so no need for 32 bit libraries or anything.

Not true.  Unless something has changed recently, the stock server Ubuntu kernel (PAE enabled kernel) can allow any 32Bit edition of Ubuntu to address more than 3.2GB of RAM; up to 64GB in fact, due to 64 GB RAM option being enabled in the kernel.  If this isn't the case any longer, then one can still recompile the kernel to enable this option and thus utilize the full capacity of RAM.  Obviously this isn't something a newbie is likely to attempt but I'm just saying as a matter of clarification.

To use the PAE enabled Kernel, do this in a gnome-terminal:
$ sudo apt-get update
$ sudo apt-get install linux-headers-server linux-image-server linux-server

---

### Post by sadaruwan12 on 2009-07-02
Yo, Welcome to the free world of Ubuntu.

For starters use 32Bit it seems like you CPU does support 64Bit but just use 32bit that'll be more than enough for you. Believe me I know 'cos I've used both flavors 32bit and 64bit. 32bit is more user friendly when it comes to 64bit theres a very small chance of getting a performance hip but it can't be seen much clearly unless the program have been written specifically for 64bit. So stick with 32bit and use your entire hard disk and get ride of those gates that keeps you in.

---

### Post by credobyte on 2009-07-02
x64 will run a bit faster than x86. Lacks some apps but that's the way it 'should' be :p

---

