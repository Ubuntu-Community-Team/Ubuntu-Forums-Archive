---
title: "Jaunty keeps freezing"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by NaeturVindur on 2009-09-20
I have recently done a full install of Ubuntu 9.04 because I got fed up with Vista (surprise!).  Everything seems to be working fine, except it keeps freezing on me.  There doesn't seem to be any rhyme or reason to when it freezes, everything just stops.  It started freezing after downloading and installing the ton of updates that would naturally come when just installing.  I don't know what I can tell you about what happens, everything justs stops.  There's nothing like a blue screen, no error message, nothing.  The mouse doesn't move, the system moniter stops scrolling.  More recently (this evening), there's been more time between freezes, and that was after I seriously messed around with the graphics drivers (with some help, I wasn't just hitting buttons and what not).

I have a little computer experience, but, as always with this subforum, I invite you to treat me like an idiot.  I know where to find the Terminal, and I know its useful to people who know what they're doing, but I don't know any of the language.

---

### Post by ankspo71 on 2009-09-20
Hi,

I'm not an expert, but I know a few things to consider. Does your computer get too hot? How much memory do you have? Do you see your processor get maxed out? and if so, is there any processes causing it?

The others here will probably want a little more info from you... like the above questions and your processor speed, type of graphics card, etc.
James.

---

### Post by NaeturVindur on 2009-09-21
I don't think that its getting too hot.  its a new computer (Asus N90sv-x1, no modifications), and the fans seems to be working fine.  I have plenty of memory (130 GB), and most of it's free.  When looking at the system monitor, it hardly seems to be doing much at all.  It is of course possible that just as it freezes, its using too much CPU, and it freezes before that even shows up on the monitor. (this part of the post took me 4 tries to post, btw.  I'm currently posting from a computer lab, as my comp has degraded so far that it can't even access the internet.  If i try to force it, it freezes.)

Through the time that i made the OP, and now, I've decided that the hardware is having the worst problems.  I'm certain Ubuntu is having some problems of its own, as I've had problems like these before.  however, i recently found that I'm having some identical problems now as when I had Vista installed.  Vista was also freezing and sometimes the display would go, showing a white screen with horizontal gray lines.  And now, with Jaunty, its doing the exact same thing.  Soon (today, if I have time), I'll be calling Asus, and probably having them fix it.  I'm just hoping that Karmic works 10x better with my computer, once it no longer has hardware errors.

---

### Post by ptn107 on 2009-09-21
Installing a newer kernel seems to solve *most* soft lock-ups in jaunty (the 2.6.28 Ubuntu versions got messed up somewhere).  The code below will install the latest kernel [2.6.31-10.34] from karmic (Ubuntu 9.10).  This one-liner will take care of everything.

Copy/paste in a terminal (Applications -> Accessories -> Terminal; password will be required):
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/karmic.list && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list.d/karmic.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-headers-generic linux-image-2.6.31-10-generic linux-headers-2.6.31-10-generic linux-headers-2.6.31-10 -y && sudo rm /etc/apt/sources.list.d/karmic.list && sudo aptitude update
```

---

### Post by norm7446 on 2009-09-21
To me this sounds like you have a problem of some sort with your memory that is installed on your system, especially as you say that it is happening in Vista as well. If you have more than one stick of memory take one out and try and see if your system stays stable if not try it with the other stick out. If you have only one stick of memory, do you have a friend who might loan you a stick just to try and see if that solves your prob. Are you using on-board Graphics or have you got a G/Card installed, as depending on how your system is set up in the BIOS, this might also be your problem.   
 
But then again I might be wrong altogether. To me you are describing a memory issue.

---

### Post by gizmobay on 2009-09-21
Welcome to the club. There's a bunch of us having the same issue without a solution.

---

### Post by Perfect Storm on 2009-09-21
> **norm7446 said:**
> To me this sounds like you have a problem of some sort with your memory that is installed on your system, especially as you say that it is happening in Vista as well. If you have more than one stick of memory take one out and try and see if your system stays stable if not try it with the other stick out. If you have only one stick of memory, do you have a friend who might loan you a stick just to try and see if that solves your prob. Are you using on-board Graphics or have you got a G/Card installed, as depending on how your system is set up in the BIOS, this might also be your problem.   
 
But then again I might be wrong altogether. To me you are describing a memory issue.

I agree, sound like faulty memory. You can also run a memory test with the ubuntu CD, it may take awhile.

---

### Post by bodam on 2009-09-21
> **ptn107 said:**
> Installing a newer kernel seems to solve *most* soft lock-ups in jaunty (the 2.6.28 Ubuntu versions got messed up somewhere).  The code below will install the latest kernel [2.6.31-10.34] from karmic (Ubuntu 9.10).  This one-liner will take care of everything.

Copy/paste in a terminal (Applications -> Accessories -> Terminal; password will be required):
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/karmic.list && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list.d/karmic.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-headers-generic linux-image-2.6.31-10-generic linux-headers-2.6.31-10-generic linux-headers-2.6.31-10 -y && sudo rm /etc/apt/sources.list.d/karmic.list && sudo aptitude update && echo "done!"
```

I have similar lockups and tried your command but I keep getting:

bash: !": event not found

Any ideas?

---

### Post by sandyd on 2009-09-21
its time for memtest 86!
except that you have so much RAM (or is that hard disk space you were refering to? 130GB)

---

### Post by sandyd on 2009-09-21
> **bodam said:**
> I have similar lockups and tried your command but I keep getting:

bash: !": event not found

Any ideas?
should be
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/karmic.list && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list.d/karmic.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-headers-generic linux-image-2.6.31-10-generic linux-headers-2.6.31-10-generic linux-headers-2.6.31-10 -y && sudo rm /etc/apt/sources.list.d/karmic.list && sudo aptitude update && echo "done"[FONT=Verdana]
[/FONT]
```[FONT=Verdana]
do NOT use "!" in the commandline
[/FONT]

---

### Post by blackmail on 2009-09-21
If the memory is ok, and the graphics card is onboard, then please consider installing another card, oh and do you have Compiz enabled, if yes then please disable it, and also in if you right click on the desktop, and then go to Change desktop background, and in the last tab, you will find options related to the effects providing desktop appearance, please set it to none. Usually a desktop overloaded with effects is easly freezing during it's usage.

---

### Post by NaeturVindur on 2009-09-21
> **norm7446 said:**
> To me this sounds like you have a problem of some sort with your memory that is installed on your system, especially as you say that it is happening in Vista as well. If you have more than one stick of memory take one out and try and see if your system stays stable if not try it with the other stick out. If you have only one stick of memory, do you have a friend who might loan you a stick just to try and see if that solves your prob. Are you using on-board Graphics or have you got a G/Card installed, as depending on how your system is set up in the BIOS, this might also be your problem.   
 
But then again I might be wrong altogether. To me you are describing a memory issue.
I don't really understand what you mean by "memory stick"  I'm not nearly advanced enough to go into my computer and start tugging at stuff.  However, I do know that if I even open the case, I void my warranty, and I still have 36 months on that, and I'll probably have to use that soon.

> **Artificial Intelligence said:**
> I agree, sound like faulty memory. You can also run a memory test with the ubuntu CD, it may take awhile.
I'll stick to doing this, but how?  (I'm writing this without having looked at what the live CD has besides the install option.)
> **carlee said:**
> should be
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/karmic.list && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list.d/karmic.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-headers-generic linux-image-2.6.31-10-generic linux-headers-2.6.31-10-generic linux-headers-2.6.31-10 -y && sudo rm /etc/apt/sources.list.d/karmic.list && sudo aptitude update && echo "done"[FONT=Verdana]
[/FONT]
```[FONT=Verdana]
do NOT use "!" in the commandline
[/FONT]
I did this, we'll see if thing improve. Thanks.

Also, I've disabled the special graphics (didn't even think of that, thanks)

Oh yeah, thats 130GB hard-drive. I have 4GB RAM. Intel Core 2 Duo.  Also the graphics card came with the comp, nVidia GeForce GT 130M.

---

### Post by Perfect Storm on 2009-09-22
> I'll stick to doing this, but how? (I'm writing this without having looked at what the live CD has besides the install option.)

Let you computer reboot with the Ubuntu CD. You'll be greeted with a bunch of options. There should be one that is called memory test or memtest.

---

### Post by patpaa on 2009-09-22
I've been having the same type of problems (freezes, lock-ups) with Jaunty and KDE. In my case, disabling the fancy desktop effects does the trick, it's been rock stable ever since. Unfortunately, the freezing returns when I try too play games requiring 3D, so it's most likely a graphics problem. After reading some other posts here, it seems like my old graphics card (Radeon 9600) doesn't work too well with the X server in 9.04.

---

### Post by blackmail on 2009-09-22
these are clearly graphics card problems. Please do an update to your graphics card, i mean buy a new one.

---

### Post by norm7446 on 2009-09-22
You could down load the ULTIMATE BOOT CD as that has 5 memory test programs on the disc.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Just download and burn the ISO in the usual way..

---

### Post by NaeturVindur on 2009-09-22
I did the memory test and updated the kernel.  The memory test found no errors.  also, the new kernel doesn't recognize my graphics card/driver, but it hasn't crashed yet (I haven't put it to any sort of test, so this may not have solved the problem)  Like I said, I don't want to do any modifications on this computer by myself, so as to not void my warranty (and I would most likely mess something critical up.  I have 0 experience working on the hardware of computers).  If I were to send my comp to Asus, or somewhere that can work on my computer within the warranty, what would y'all suggest.  Should I have them check to see if my graphics card is broken (which it probably is, now i know its not memory) and replace it with the same kind, or should I just have them put in a new kind?  If the new kind, which kind?

also, I have no capability to burn CD's, and my zip drives are tied up acting as memory back up, so i won't be getting those 5 mem. tests.

---

### Post by ibuclaw on 2009-09-22
> **NaeturVindur said:**
> I did the memory test and updated the kernel.  The memory test found no errors.  also, the new kernel doesn't recognize my graphics card/driver, but it hasn't crashed yet (I haven't put it to any sort of test, so this may not have solved the problem)  Like I said, I don't want to do any modifications on this computer by myself, so as to not void my warranty (and I would most likely mess something critical up.  I have 0 experience working on the hardware of computers).  If I were to send my comp to Asus, or somewhere that can work on my computer within the warranty, what would y'all suggest.  Should I have them check to see if my graphics card is broken (which it probably is, now i know its not memory) and replace it with the same kind, or should I just have them put in a new kind?  If the new kind, which kind?

also, I have no capability to burn CD's, and my zip drives are tied up acting as memory back up, so i won't be getting those 5 mem. tests.
If you get lockups again, try the following to reboot.
Hold down **Alt** + **PrintScreen** and press the following sequence with about 3-5 seconds between each key: **R E I S U B**

Then run the following:
```
tar -czf logs.tar.gz /var/log/dmesg* /var/log/messages* /var/log/kern.log* /var/log/debug*
lspci -vvv | gzip > lspci_vvv.gz

```
And upload the **logs.tar.gz** and **lspci_vvv.gz** files.

That should give enough info to so say what may be going wrong.

Regards
Iain

---

### Post by NaeturVindur on 2009-09-22
> **tinivole said:**
> If you get lockups again, try the following to reboot.
Hold down **Alt** + **PrintScreen** and press the following sequence with about 3-5 seconds between each key: **R E I S U B**

Then run the following:
```
tar -czf logs.tar.gz /var/log/dmesg* /var/log/messages* /var/log/kern.log* /var/log/debug*
lspci -vvv | gzip > lspci_vvv.gz

```And upload the **logs.tar.gz** and **lspci_vvv.gz** files.

That should give enough info to so say what may be going wrong.

Regards
Iain
I did the key command, and didn't see anything happen.  Am I supposed to do the REISUB **while** holding the Alt+Prt Sc or after?

Also, the files I got from the code are attached.

ETA: I have found a reliable means of freezing my computer: trying to view vid.s online, if that at all helps

ETA2:  Now that I have a reliable way to freeze my computer, I did as little test.  I have a zip drive that blinks when its in use, so it indicates whether its being mounted on its own.  I plugged it in before frezzing the comp, and the light flashed, and it got mounted.  I unmounted it and took it out.  then I froze the comp, and plugged in the zip drive.  No light.  So I now know its not just that the screen/graphics card isn't refreshing, but the system itself is freezing.

---

### Post by NaeturVindur on 2009-09-22
> **Don1500 said:**
> You do have a SWAP Partition right?
How big is your hard drive? Your swap partition should be at least 2X your memory. Make it a 2 gig and you should be OK, if not try 3 gig.
...oh.  is this right? my swap partition is hardly a MB bigger than my RAM

---

### Post by theozzlives on 2009-09-22
Just putting Ubuntu on most likely voided your warranty, at least Dell and Gateway feel that way.

---

### Post by SunnyRabbiera on 2009-09-22
Jaunty has been win some loose some for many, you may want to hold out a bit and try Karmic next month.

---

### Post by NaeturVindur on 2009-09-22
> **theozzlives said:**
> Just putting Ubuntu on most likely voided your warranty, at least Dell and Gateway feel that way.
there is nothing in the Asus warranty about changing software, they simply don't cover any of it.

---

### Post by ibuclaw on 2009-09-22
> **NaeturVindur said:**
> ...oh.  is this right? my swap partition is hardly a MB bigger than my RAM

Yes that is fine. If you have 2GBs+ I doubt Linux will even use the swap unless absolutely necessary (ie: you are running one, or multiple VMs, or you use the "hibernation" feature).

Yes, having a look at the logs it does indeed seem that it may be your wireless card drivers at fault here. In every instance of what happens right before you crash is the wireless is attempting to reconnect to the AP as it disconnected spuriously for whatever reason.
According to Launchpad, there is already a ticket open for this type of card in Karmic: [https://bugs.launchpad.net/linux/+bug/426130](https://bugs.launchpad.net/linux/+bug/426130)

Perhaps you should try turning the card off (either in BIOS or disable it in NetworkManager) and then connect to the net using an Ethernet cable to see if the issue persists. This will indeed confirm that it is the wireless network card at fault here.

> **NaeturVindur said:**
> I did the key command, and didn't see anything happen.  Am I supposed to do the REISUB **while** holding the Alt+Prt Sc or after?
**while** holding.

Regards
Iain

---

### Post by patpaa on 2009-09-23
> **SunnyRabbiera said:**
> Jaunty has been win some loose some for many, you may want to hold out a bit and try Karmic next month.

Until then, you might consider reverting to Hardy. That's what I had to do eventually. Jaunty was just to buggy.

---

### Post by theozzlives on 2009-09-23
> **NaeturVindur said:**
> there is nothing in the Asus warranty about changing software, they simply don't cover any of it.

It didn't say it in mine either. My power button and LEDs broke and they said I'd have to put Vista back on before they would help me. So I took out the HD and just sent it in. Included a note saying I had sensitive data on it. That's as far as I'd go with a computer under warranty, I won't even work on them professionally for fear of voiding the warranty.

---

### Post by trailerkn on 2009-09-23
I think the problem comes where the computer gets to hot.
try to take out the battery and just use the batterycabel. 

if its freezing again check if its hot.

In my Experience of Ubuntu, i think that the computer just cant handle it, i dont know.

---

### Post by NaeturVindur on 2009-09-23
> **tinivole said:**
> Yes that is fine. If you have 2GBs+ I doubt Linux will even use the swap unless absolutely necessary (ie: you are running one, or multiple VMs, or you use the "hibernation" feature).

Yes, having a look at the logs it does indeed seem that it may be your wireless card drivers at fault here. In every instance of what happens right before you crash is the wireless is attempting to reconnect to the AP as it disconnected spuriously for whatever reason.
According to Launchpad, there is already a ticket open for this type of card in Karmic: [https://bugs.launchpad.net/linux/+bug/426130](https://bugs.launchpad.net/linux/+bug/426130)

Perhaps you should try turning the card off (either in BIOS or disable it in NetworkManager) and then connect to the net using an Ethernet cable to see if the issue persists. This will indeed confirm that it is the wireless network card at fault here.


**while** holding.

Regards
Iain
I would love to use an ethernet cable (in fact, one is plugged in right now), and the system always check that first, and says "Wired Net disconnected." 
> **patpaa said:**
> Until then, you might consider reverting to Hardy. That's what I had to do eventually. Jaunty was just to buggy.
I tried Hardy once.  It doesn't support the drivers for my internet cards (neither wireless nor wired), and considering as how one of the things I use the comp for the most is the internet, that doesn't really help.

---

### Post by theozzlives on 2009-09-23
> **NaeturVindur said:**
> I would love to use an ethernet cable (in fact, one is plugged in right now), and the system always check that first, and says "Wired Net disconnected."  

If you right-click on Network Manager is "Enable Networking" checked?

---

### Post by tkoco on 2009-09-23
Having read the various messages about lockups, try this:

1) bigger swapspace to make sure that memory (RAM + swap) does not run out. Ubuntu (and other distros) supports multiple swapspaces. ```
man mkswap
```to get more info about swapfiles and swapspace.

2) if the video is built into the MB, try maxing out the BIOS settings for the video memory.
3) If the video card is old, try updating the card (as suggested) to a newer version with more on-board memory.
4) Check the heatsink of the CPU for dust build-up, especially on a laptop! If the CPU cannot cool itself quick enough, the system will either lockup or shutdown.
5) If you added more memory chips, did you get matched chips? Different manufacturers of RAM memory use different timing specs and identical sized chips can fight each other on the MB.

Hopefully this helps!

---

### Post by NaeturVindur on 2009-09-24
> **theozzlives said:**
> If you right-click on Network Manager is "Enable Networking" checked?
yup
> **tkoco said:**
> Having read the various messages about lockups, try this:

1) bigger swapspace to make sure that memory (RAM + swap) does not run out. Ubuntu (and other distros) supports multiple swapspaces. ```
man mkswap
```to get more info about swapfiles and swapspace.

2) if the video is built into the MB, try maxing out the BIOS settings for the video memory.
3) If the video card is old, try updating the card (as suggested) to a newer version with more on-board memory.
4) Check the heatsink of the CPU for dust build-up, especially on a laptop! If the CPU cannot cool itself quick enough, the system will either lockup or shutdown.
5) If you added more memory chips, did you get matched chips? Different manufacturers of RAM memory use different timing specs and identical sized chips can fight each other on the MB.

Hopefully this helps!
This comp is less than a year old, I have serious problems anything's out of date, and I have 0 mods of any kind to the hardware.  Also, I'm not willing to open anything, but I can take a vacuum or something to the air vents and openings.

---

### Post by Perfect Storm on 2009-09-24
Once a year I take an air compressor to clean my computer from dust and dirt. The same deal I do with the computers at my work.

---

### Post by NaeturVindur on 2009-09-24
the comp just freezed while using the ethernet (how I got ethernet running, if it was anything I did versus pure chance, I have no idea).  the subsequent bug reprots (or what appear to my eyes to be bug reports) are attached, if anyone care to looka at them.

---

### Post by quinnten83 on 2009-09-24
I've had these lockups on my main computer ever since 7.10. 
There is no reason or exact time for the lock-ups. They're completely random. With Jaunty it has gotten better, but it still happens. There still is no solution in sight, I don't know if they even know what is causing it. Someone once said something about mouse input. 
I noticed in my case it happens a lot when I'm using scale in compiz, while listening to rhythmbox and surfing the net with firefox. But since this is what I ALWAYS do, I can't say that it's that combination that causes it.
Indeed when I turn off desktop effects, the lock-ups never happen.
But I can't, and refuse to live without scale!!!

---

### Post by ibuclaw on 2009-09-24
Hmm... It could be the motherboard that is locking the system up.

Attached is a generic data mining script.
The only prerequesite is for you to install iasl:
```
sudo apt-get install iasl
```
It's based off the one NVIDIA uses, but has NV specific bits removed and adds a few things that may be of greater interest.

I will see what I can take out of it that is of interest, but admittedly we probably won't come to a resolution on this issue any time within the near future.

All information produced off it should be enough for you to file a bug report on your motherboard.
And if it isn't then I can send you to the right page to produce the information required.

Regards
Iain

---

### Post by bodam on 2009-09-24
> **carlee said:**
> should be
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.d/karmic.list && sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list.d/karmic.list && sudo aptitude update && sudo aptitude install linux-firmware linux-generic linux-image-generic linux-headers-generic linux-image-2.6.31-10-generic linux-headers-2.6.31-10-generic linux-headers-2.6.31-10 -y && sudo rm /etc/apt/sources.list.d/karmic.list && sudo aptitude update && echo "done"[FONT=Verdana]
[/FONT]
```[FONT=Verdana]
do NOT use "!" in the commandline
[/FONT]

That did it.  I'm now running the new kernel and the system seems rock solid but now I have another issue.  After upgrading now my nVidia drivers do not work and the generic drivers are somewhat annoying.  Is there an upgraded nVidia driver?  How would I install it?

---

### Post by NaeturVindur on 2009-09-24
> **bodam said:**
> That did it.  I'm now running the new kernel and the system seems rock solid but now I have another issue.  After upgrading now my nVidia drivers do not work and the generic drivers are somewhat annoying.  Is there an upgraded nVidia driver?  How would I install it?
I had the same exact problem, it just didn't really bother me.  Who makes the ubuntu drivers haven't really focused on the newer nVidia cards.

---

### Post by Goveynetcom on 2009-09-24
> **carlee said:**
> its time for memtest 86!
except that you have so much RAM (or is that hard disk space you were refering to? 130GB)

Exactly what I was thinking,

MEMTEST86

[http://www.memtest86.com/](http://www.memtest86.com/)

Just download and burn ISO.

---

### Post by bodam on 2009-09-24
> **NaeturVindur said:**
> I had the same exact problem, it just didn't really bother me.  Who makes the ubuntu drivers haven't really focused on the newer nVidia cards.

I'm glad it's not just me but it is annoying since it's my _only_ complaint with the system.  It does everything else like a dream.  It's like having that cool shiny new car with a dent in the driver's door.....

---

### Post by tkoco on 2009-09-24
Might be the video card driver rather than the kernel. I have a system where the video driver eats the memory like candy while video intensive apps are running. I'll have to upgrade the video card to fix the problem.
> **bodam said:**
> That did it.  I'm now running the new kernel and the system seems rock solid but now I have another issue.  After upgrading now my nVidia drivers do not work and the generic drivers are somewhat annoying.  Is there an upgraded nVidia driver?  How would I install it?

---

### Post by NaeturVindur on 2009-09-25
> **tkoco said:**
> Might be the video card driver rather than the kernel. I have a system where the video driver eats the memory like candy while video intensive apps are running. I'll have to upgrade the video card to fix the problem.
the problem can be seen as both, kernel and driver not working with each other.

also, I've dome the memtest86, no errors.

---

