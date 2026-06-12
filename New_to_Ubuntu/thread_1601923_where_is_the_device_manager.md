---
title: "where is the device manager?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by sallam on 2010-10-20
Greetings

I failed to find an equivalent to Windows device manager. Is there such device manager in ubuntu, to check my hardware and drivers?

---

### Post by psusi on 2010-10-20
There isn't one per se, but you can run lshw in a terminal for a list of your hardware.

---

### Post by LADmaticCA on 2010-10-20
> **psusi said:**
> There isn't one per se, but you can run lshw in a terminal for a list of your hardware.

That works.

There is also a gui tool in the software center you might find useful, called *hardinfo*.

---

### Post by Autodave on 2010-10-20
> **sallam said:**
> Greetings

I failed to find an equivalent to Windows device manager. Is there such device manager in ubuntu, to check my hardware and drivers?

In Synaptic, look for gnome-device-manager and install that.

---

### Post by sallam on 2010-10-21
that is all sooooooooooo weird!!!!!!!!!!!!!!
Why should anyone install an application for this basic thingie?
Why on earth didn't they make it a default in every copy of ubuntu used in this planet????????????

---

### Post by amjjawad on 2010-10-21
> **sallam said:**
> that is all sooooooooooo weird!!!!!!!!!!!!!!
Why should anyone install an application for this basic thingie?
Why on earth didn't they make it a default in every copy of ubuntu used in this planet????????????

Good point but there's always plan B.

Applications > Accessories > Terminal

```

lshw

```

Every OS is different than the other one. Linux is not Windows nor Windows is Linux.
If you ask me, Linux is a bit complicated than Windows. If you're a light user that do nothing but browsing, word processing, etc then you don't need to know much about these stuff. 
I know most of the users would like to know at least what's going on around them which is good.

I've used Windows for 10 years but I didn't learn as much as I learned in ONE MONTH with Linux (Ubuntu and others Distributions).

Trust me, when they said "Linux for Human Beings" they do mean it :)

---

### Post by mastablasta on 2010-10-21
also in Linux most drivers are part of Kernel. In windows Kernel is locked down and you need to load drivers separatelly.

---

### Post by Grenage on 2010-10-21
> **sallam said:**
> that is all sooooooooooo weird!!!!!!!!!!!!!!
Why should anyone install an application for this basic thingie?
Why on earth didn't they make it a default in every copy of ubuntu used in this planet????????????

It's not weird; Ubuntu is not a Windows clone.  A central panel for quickly viewing hardware devices and drivers would be useful.

---

### Post by beew on 2010-10-21
There is the gnome-device-manager from the repository, but it is more like a hardware listing tool than a hardware manager.

---

### Post by rburkartjo on 2010-10-21
sal there is a program called sysinfo it can be installed form the ubuntu software center

it will be installed under tools

also here is one to test you system called system testing it will be installed under system/adm again get it from the software center

---

### Post by beew on 2010-10-21
> **rburkartjo said:**
> sal there is a program called sysinfo it can be installed form the ubuntu software center

it will be installed under tools

also here is one to test you system called system testing it will be installed under system/adm again get it from the software center

Sysinfo appears to have a bug in Maverick, if you click "system" it will just close on you. Otherwise it is nice little app (but again it doesn't manage anything)

---

### Post by TBABill on 2010-10-21
What exactly are you trying to check? Do you just want to see a list of what hardware you have or are you trying to access each driver for each device? As stated the kernel takes care of your hardware so you go about making changes differently (such as editing a .conf file) for some items that do not have a GUI to control it. Not difficult, just different.

---

### Post by sallam on 2010-10-21
My Canon Pixma mp250 printer doesn't work under ubuntu. I wanted to check its driver.
I did install it manually, and it worked once, but no more..
It works fine under Win7..

---

### Post by sallam on 2010-10-21
what is "kernel" please?

---

### Post by ironic.demise on 2010-10-21
> **amjjawad said:**
> Good point but there's always plan B.
 
Applications > Accessories > Terminal
 
```

lshw

```
 
Every OS is different than the other one. Linux is not Windows nor Windows is Linux.
If you ask me, Linux is a bit complicated than Windows. If you're a light user that do nothing but browsing, word processing, etc then you don't need to know much about these stuff. 
I know most of the users would like to know at least what's going on around them which is good.
 
I've used Windows for 10 years but I didn't learn as much as I learned in ONE MONTH with Linux (Ubuntu and others Distributions).
 
Trust me, when they said "Linux for Human Beings" they do mean it :)
 +1
Pretty much the same story right her, I thought I was good at using Windows, but I can do a lot more in Ubuntu, atleast now I'm used to it.
 
I had my misconceptions about it too when I started, I thought I'd be able to use several of the CMD commands as near-enough direct ports... but I had to re-learn an entire command line method.
 
worth every second though.
 
Ubuntu doesn't really *need* a device manager... what would it be used for really.
If there's a problem with a device you check lshw, you look for drivers, and you troubleshoot.
 
I think a good command line user will be able to find and solve the problem in atleast half the time that the "device manager" does.

---

### Post by HermanAB on 2010-10-21
Howdy,

If you want a 'Windows' experience, then you should install OpenSuse or Mandriva.  Those distros have wizards for everything and the kitchen sync.  If you can click a mouse, you *can* be a Linux Administrator, but just not with Ubuntu...

BTW, that is not a typo.  Kitchen sync is used to sync with your cell phone on Mandriva.

---

### Post by amjjawad on 2010-10-21
> **sallam said:**
> what is "kernel" please?

Highlight "kernel" - use your mouse, right click, choose **Search Google for "*kernel*"** and you'll understand :)

---

### Post by sallam on 2010-10-21
But I didn't understand, thats why I'm asking..

---

### Post by amjjawad on 2010-10-21
> **sallam said:**
> But I didn't understand, thats why I'm asking..

[Kernel]("http://en.wikipedia.org/wiki/Kernel_%28computing%29")

> In computing, the **kernel** is the central component of most computer operating systems;  it is a bridge between applications and the actual data processing done  at the hardware level. The kernel's responsibilities include managing  the system's resources (the communication between hardware and software components).


Okay, let me know what part that you didn't understand so that I'll explain it to you :)

---

### Post by sallam on 2010-10-21
Is it a software? is it part of the OS? or is it separate from the OS?

---

### Post by amjjawad on 2010-10-21
> **sallam said:**
> 
Is it a software? 

Yes, it's a Software.

> 
is it part of the OS? or is it separate from the OS?

It's the central part of the OS.

To understand Kernel, you need to understand what's the OS.

[OS (Operating System)]("http://en.wikipedia.org/wiki/Operating_system") is a software,  consisting of programs and data, that runs on computers and manages the  computer hardware and provides common services for efficient execution  of various application software

You can't use any computer without an OS. How would you for example watch a movie? listen to music? write a document? etc? you can't just go to the Hard Drive and open a file, you can't go to the RAM and load a file, etc.
All these operations are done by the OS and the kernel is the heart of the OS.

That's the simplest way I could put it :)

---

### Post by migs73 on 2010-10-21
> **amjjawad said:**
> Yes, it's a Software.


It's the central part of the OS.

To understand Kernel, you need to understand what's the OS.

[OS (Operating System)]("http://en.wikipedia.org/wiki/Operating_system") is a software,  consisting of programs and data, that runs on computers and manages the  computer hardware and provides common services for efficient execution  of various application software

You can't use any computer without an OS. How would you for example watch a movie? listen to music? write a document? etc? you can't just go to the Hard Drive and open a file, you can't go to the RAM and load a file, etc.
All these operations are done by the OS and the kernel is the heart of the OS.

That's the simplest way I could put it :)

Good descriptions amjjawad, now time for the (possibly) most linked site in all Linux forums;

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Sallam, please read this, it helps you understand why there are differences, and why they are good (not one OS is better than the other, just why them being different is good).
It helped me drop any preconceptions I had as to how things 'should be'.
:P

---

### Post by sallam on 2010-10-22
Many thanks Amjjawad for your excellent description. I now understand better.
Migs73, thanks for the link.. its a treasure to read.
In the first few lines, it says:
> As a simple example, consider driver upgrades: one typically upgrades a hardware driver on Windows by going to the manufacturer's website and downloading the new driver; whereas in Linux you upgrade the kernel.

This means that a single Linux download & upgrade will give you the newest drivers available for your machine, whereas in Windows you would have to surf to multiple sites and download all the upgrades individually.
So, does that mean that the kernel has all the drivers anyone needs? or is it a tailored download that has the driver for my machine?
And what if the kernel is missing a driver for a hardware I have? for example, a printer..
When I first connected my Canon mp250 printer, ubuntu offered many drivers, none of them are Canon. I had to download a driver and install it manually. It worked for a while, but now the printer doesn't print. It prints fine under Win7..
Should I have accepted ubuntu's offer to use one of the drivers it listed then during installation?

---

### Post by alphacrucis2 on 2010-10-22
Regarding the Pixma MP250. Looks like it should be supported:

[http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp]("http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp")

---

### Post by mcduck on 2010-10-22
> **sallam said:**
> that is all sooooooooooo weird!!!!!!!!!!!!!!
Why should anyone install an application for this basic thingie?
Why on earth didn't they make it a default in every copy of ubuntu used in this planet????????????

Because most people would never need to do such "basic thingie". (or understand what it tells to them, to be honest).

Simply seeing that your hardware works is usually enough to prove that the hardware is recognized and has working drivers. Unless things don't work correctly for you you would never need to check such stuff yourself. And for most of us things really *do* just work and all the hardware is recognized automatically.

(checking your hardware & drivers is pretty much an admin thing, not an user thing, and Linux already includes tools that give you the info. They just happen to be command-line tools like many other admin that aren't needed on daily use)

---

### Post by amjjawad on 2010-10-22
> **migs73 said:**
> Good descriptions amjjawad, now time for the (possibly) most linked site in all Linux forums;

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)



Thanks a lot, mate and thanks even more for that link :)
I've noticed many other people were posting the same link but I didn't really bother to read it because I know that Linux is not Windows nor Windows is Linux. Apparently, I was wrong :) that article is MORE than amazing and I LOVE it :)
Many thanks!

I guess EVERYONE should read it even though they know the difference already.

---

### Post by migs73 on 2010-10-22
> **amjjawad said:**
> Thanks a lot, mate and thanks even more for that link :)
I've noticed many other people were posting the same link but I didn't really bother to read it because I know that Linux is not Windows nor Windows is Linux. Apparently, I was wrong :) that article is MORE than amazing and I LOVE it :)
Many thanks!

I guess EVERYONE should read it even though they know the difference already.

Yes, it should be the first step in everyones switch from MS to Linux.
It wouldn't stop the questions (people need answers)but might change how they are asked ;)

---

### Post by amjjawad on 2010-10-22
> **sallam said:**
> Many thanks Amjjawad for your excellent description. I now understand better.


Glad to hear that and you welcome :)

> 
Migs73, thanks for the link.. its a treasure to read.


Oh yes, it's a treasure indeed.

> 
So, does that mean that the kernel has all the drivers anyone needs? or is it a tailored download that has the driver for my machine?
And what if the kernel is missing a driver for a hardware I have? for example, a printer..

There's one basic rule that everyone must be aware of.
[B]There's no perfect OS, period.
[/B]If you search google, yahoo or any other search engine and read more and more about Operating Systems, you'll come to know that there's no perfect OS. If that OS does exist, then everyone will use it.

With that said, you need to know my friend that Linux or even Windows can't recognize ALL the hardware in this world. It's common sense :)
Thus, if you have Windows, you search for the driver (as mentioned in that link migs73 has posted) and if you have Linux (Ubuntu) then when you update the Kernel, more drivers will be installed.
Sometimes, you won't find what you exactly are looking for. For example, your printer couldn't be recognized. But guess what? sometimes, it could be a simple mistake either by the user (don't get me wrong), by the OS or the printer (or any other hardware) - as mentioned before, nothing is prefect - and that mistake will lead to unrecognized hardware. 

Allow me to share this experience with you.
I installed last month some Linux Distributions like OpenSUSE. It couldn't recognize my Wireless Adapter while Ubuntu did. It doesn't mean Ubuntu is better and it doesn't mean OpenSUSE is bad. Again, no OS is prefect :)

As of now, I have everything recognized, thanks to Ubuntu.
Guess what? and I'm not trying to mock Windows 7 but that's the truth. When I installed Windows 7, it could not recognize my Audio, my Wireless Adapter and some other devices I forgot what were these. Spent an hour or less to find the drivers and fix the issues.

Point is: If we're going to include all the drivers for all the hardwares, then perhaps we need to purchase a Hard Disk with an OS installed because it would be much easier than download or even install perhaps 20GB OS :)
It's just an example and nothing is real :)


> 
When I first connected my Canon mp250 printer, ubuntu offered many drivers, none of them are Canon. I had to download a driver and install it manually. It worked for a while, but now the printer doesn't print. It prints fine under Win7..

Once you install Ubuntu, it offers you some updates. After a while, it will update the kernel but I'm talking about 10.04. I don't have 10.10 yet.

If you update the Kernel, perhaps your problem will be solved.
I see alphacrucis2 has posted a link for you :)

Don't panic, sometimes a simple restart to your machine could fix everything. It doesn't mean Ubuntu is bad but computers will never work with errors, that's just not possible. Ubuntu couldn't recognize your printer is not an error or a disadvantage in Ubuntu. Not trying to defend Ubuntu but after 10 years with Windows and 2 months or less with Ubuntu, I really don't want to use Windows anymore. By time, you'll understand what I mean :)

 
> 
Should I have accepted ubuntu's offer to use one of the drivers it listed then during installation?
I don't know, perhaps it will work, perhaps it won't. Either to check that link posted previously for the driver or update the kernel. Most likely the Update Manager will pop up asking you to update your system.

---

### Post by amjjawad on 2010-10-22
> **migs73 said:**
> Yes, it should be the first step in everyones switch from MS to Linux.
It wouldn't stop the questions (people need answers)but might change how they are asked ;)

I undeniably second that :)

---

### Post by migs73 on 2010-10-22
> **amjjawad said:**
> 
[B]There's no perfect OS, period.
[/B]. 


+1 to that. People ask me if Ubuntu is better than windows (I used to have Vista so I could genuinely say yes) and I tell them it is just as prone to problems but this forum is more helpful than having your own IT guy, and it's a damn site cheaper.:P

---

### Post by amjjawad on 2010-10-22
> **migs73 said:**
> this forum is more helpful than having your own IT guy, and it's a damn site cheaper.:P

+100 to that :)
What I've learned in few days here, I couldn't learn it in 10 years and sadly those 10 years I spent with Windows. If just the time could go back, I won't think twice to use Linux for my whole life :D

Okay Windows lovers, don't hate me, Windows isn't that bad but Linux is great :)

---

