---
title: "Core questions I guess?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by mbele3000 on 2010-01-04
Happy New Year All
 
  Running a intel dual core. Is it possible to install Ubuntu (32) on partition using one core,and WinXP (32) to another using the second core?

---

### Post by pritamps on 2010-01-04
Huh?

Since you can't boot both of them together anyway, I don't see how or why you should choose cores :confused:

---

### Post by tom.swartz07 on 2010-01-04
> **mbele3000 said:**
> Happy New Year All
 
  Running a intel dual core. Is it possible to install Ubuntu (32) on partition using one core,and WinXP (32) to another using the second core?

I think you are confusing the idea of CPU cores with Hard Drive Partitions.

Your CPU, an Intel Dual core, is designed using 2 traditional CPU's working in concert. This allows your computer to split up processing problems and thus allows your computer to 'work' faster.

If you want to install XP and Ubuntu on your computer, this is extremely easy to do. I would suggest visiting this site as you plan to use Ubuntu. It will help you clear up any questions or confusion about your system, and it will help you decide if Ubuntu is right for you! [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

If you want guides to install on your system, just let me know and we could point you to some excellent guides to get you started.


If you were to try Ubuntu on your system, I would highly recommend the 64bit version. There are practically NO problems with application compatibility and you receive a speed boost because it is designed to take advantage of your dual core x64 system.


If you have any other questions, please feel free to ask! We're here to help!

---

### Post by mbele3000 on 2010-01-04
Thank you all!

 Is there a way to install Xp via unetbootin on Ubuntu then? Sorry if this seems scattered or tangential.

---

### Post by switch10 on 2010-01-04
you can install XP on a virtual machine in Ubuntu.  I use VitrualBox it works great.

Check this out:  [http://www.linuxjournal.com/content/run-windows-xp-ubuntu-virtualbox](http://www.linuxjournal.com/content/run-windows-xp-ubuntu-virtualbox)

---

### Post by aviedw on 2010-01-04
This questions would make more sense if you were trying to run both Ubuntu and Windows Xp at the same time. Then i could see the possibility of running them on separate cores, but the only problem with that is that there always seems to have to be a dominate OS running and the other other would be in virtual world.

But this is an interesting concept.

---

### Post by tom.swartz07 on 2010-01-05
> **mbele3000 said:**
> Thank you all!

 Is there a way to install Xp via unetbootin on Ubuntu then? Sorry if this seems scattered or tangential.

If you have Ubuntu installed then you should have no problem running XP in virtualbox. The version in the software center is kind of gimped, so you should use the one from the virtualbox website. 

Hope this helps!

---

### Post by mbele3000 on 2010-01-05
1) RE: Aviedw  	
 "Re: Core questions I guess?
This questions would make more sense if you were trying to run both Ubuntu and Windows Xp at the same time"
    
   Yes I am How is that done? 64 to 32 ..... no seriously! 
   2 MR. tom.swartz07 so then why cant I get the 64 to work as 2 separate  
    
    (i.e. 64 divided by 2 = ummm 32)

 Running virtualbox I cant run applications (.exe) without 3D errors or administrative errors (wine or virtualbox). If I cant use virtualbox to access the motherboard or embedded functions? I paid for my copy of windows and well Linux is free right???  So there sre certin games by "bigfish" that are available in mac and in windows so why not linux or Ubuntu? Yet all the same games in mac and win are all intel based regardless of intel or amd! soooooo WHY THE PROBLEM!!!

---

### Post by Methuselah on 2010-01-05
> **mbele3000 said:**
> 1) RE: Aviedw  	
 "Re: Core questions I guess?
This questions would make more sense if you were trying to run both Ubuntu and Windows Xp at the same time"
    
   Yes I am How is that done? 64 to 32 ..... no seriously! 
   2 MR. tom.swartz07 so then why cant I get the 64 to work as 2 separate  
    
    (i.e. 64 divided by 2 = ummm 32)

 Running virtualbox I cant run applications (.exe) without 3D errors or administrative errors (wine or virtualbox). If I cant use virtualbox to access the motherboard or embedded functions? I paid for my copy of windows and well Linux is free right???  So there sre certin games by "bigfish" that are available in mac and in windows so why not linux or Ubuntu? Yet all the same games in mac and win are all intel based regardless of intel or amd! soooooo WHY THE PROBLEM!!!

The only way to run two operating systems at once is to use a 'virtualization' software.

VirtualBox is one such but operating systems running in virtual box will generally not have raw access to your actual hardware.
This is necessary, because the job of the OS is to control access to your hardware and they will generally not share it with another OS unless they are 'tricked' with a virtual machine.
3D acceleration is typicallly not available to the operating system that is running in the VM though VirtualBox has been making some efforts to make this happen.

The problem with games not working everywhere is that each operating system 'speaks a different language' to programs that run in them so the programs have to be written specifically for each one.
What Wine tries to do is translate 'the language' that windows programs expect to what Ubuntu expects programs to ask for.
However this is a lot of work to implement (wine started 15 years ago!) so it still is not perfect and all games do not work.

In a 'dual boot' situation you do have two operating systems on your hard drive but you cannot run them both at once.
You have to choose which one to start as your machine boots up and have to shut down when you want to start the other one.
That is the inconvenient aspect of it.

Until more game makers start making their games available for linux dual booting (or sticking to windows only) will remain the best option for a while yet.

---

### Post by audiomick on 2010-01-05
> The only way to run two operating systems at once is to use a 'virtualization' software.


You can look at it this way.
Only one person can be the driver of a car. Virtualisation is is like putting another set of dummy controls in the back seat.
Something like Virtual box lets the real driver see what the guy in the back is doing with the controls so he, the real driver, can steer the car accordingly. The guy in the back thinks he is in control, but the guy in the driver's seat is doing the steering.

> why cant I get the 64 to work as 2 separate
(i.e. 64 divided by 2 = ummm 32)
I only have a superficial understanding of this, but good enough to paint a picture. You know that computers deal with digital numbers.

The 64 refers to the size of the buffers that the system works with. A buffer is the temporary memory the the numbers that the computer works with are stored in whilst the computer is working with them.

A 4 bit number has 4 positions, each of which can be a 1 or a 0, e.g. 1011, which is the same as eleven. There is an article about the binary system here
[http://en.wikipedia.org/wiki/Binary_numeral_system](http://en.wikipedia.org/wiki/Binary_numeral_system)
if you're interested.

A 32 bit system deals with numbers which have 32 positions, a 64 bit system with numbers with 64 positions.

To try and make two 32 bit systems because half of 64 is 32 is a bit like saying you could make two idiots out of one genius because his brain is twice as big...:)

As far as the dual core thing goes, it is not the case that two cores @ 32 bits = 64, but rather that the cpu has "two brains", each of which has a 64 bit architecture. There are mechanisms which allow you to specify that, for instance, one program is allowed to monopolize one of the cores. I think, but am not sure, that you can specify that a system in a virtualisation can have a core to itself, leaving the other one for the host system. However, you can still only have one driver.

---

### Post by mbele3000 on 2010-01-05
I remember with the Mac Power PC you could use both windows and mac apps at the same time? The reason that Linux is "better" in my opinion is that it can convert files much easier

---

### Post by audiomick on 2010-01-05
> **mbele3000 said:**
> I remember with the Mac Power PC you could use both windows and mac apps at the same time?
That _must_ have been either something like wine, a virtualisation, or programs, of which there are a large number, that have been compiled to run on both systems. Without a wine equivalent or a virtualisation, you must have a version of the program for the OS that you are using. For instance, open office runs on windows or linux, and, as far as I know, mac. The program looks practically identical when it is running, but it is a different version for each operating system.


>  The reason that Linux is "better" in my opinion is that it can convert files much easier


That may well be one reason, although I don't know exactly what you mean. There are very many reasons why people prefer Linux. Many have to do with being able to do with the computer what you want, rather than what the seller of the OS thinks you should want. One of the main reasons for me is that when you have a problem, you don't get told to consult your system administrator. There are some things that just don't work, but even then, if the user were capable of programming a solution, he could do so perfectly legally and with access to everything he needs to know to program what he needs. This is not the case with "some other operating systems" :)

---

### Post by 3rdalbum on 2010-01-05
> **mbele3000 said:**
> I remember with the Mac Power PC you could use both windows and mac apps at the same time?

Not with PowerPC, unless you used Virtual PC (which was emulation).

If you want to run Windows and Ubuntu simultaneously, then install Ubuntu and then install Virtualbox. Install Windows within Virtualbox.

You don't need to "assign a core" to Virtualbox or Windows any more than you need to assign a core to your web browser. It's done in the background.

Also, 64-bit doesn't equal two 32-bit processors. Let's use an analogy. The country I live in uses four-digit postcodes. If there were 10,000 suburbs/towns here, then they'd need to change to five-digit postcodes. This doesn't make the mail arrive quicker, it just allows more people to have an address. That's all 64-bit is - there are more digits available in memory addresses, so you can have more memory.

---

### Post by audiomick on 2010-01-05
> **3rdalbum said:**
> 
You don't need to "assign a core" to Virtualbox or Windows any more than you need to assign a core to your web browser. It's done in the background.


True.:)
As I said, I believe there are mechanisms for this, but for most people it is better to just let the system get on with things.

---

