---
title: "Black Screen"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by billyfish010 on 2010-10-27
I have been using Ubuntu 10.04 for a number of weeks now and all has worked well, however, a fault has developed that is causing much frustration.

What happens almost every time I use Ubuntu is first the mouse freezes and then after a few seconds the screen goes black and I have no choice but to press the reset button to force the computer to reboot.
There is no particular time this happens it can happen after a couple of minutes or after a couple of hours.


Has anyone any idea what is causing the problem and how I could possibly fix it. I really don't want to have to do a complete reinstall since that would mean reinstalling several Windows programs into Wine.

Bill

---

### Post by bioterror on 2010-10-27
> **billyfish010 said:**
> I have been using Ubuntu 10.04 for a number of weeks now and all has worked well, however, a fault has developed that is causing much frustration.

What happens almost every time I use Ubuntu is first the mouse freezes and then after a few seconds the screen goes black and I have no choice but to press the reset button to force the computer to reboot.
There is no particular time this happens it can happen after a couple of minutes or after a couple of hours.


Has anyone any idea what is causing the problem and how I could possibly fix it. I really don't want to have to do a complete reinstall since that would mean reinstalling several Windows programs into Wine.

Bill

Okay, this sounds challenging.
Is it possible to keep terminal open and when you notice that the mouse freezes, you intantly alt+tab to the terminal and type "dmesg" without "".

I would like to know if the kernel outputs something.

---

### Post by billyfish010 on 2010-10-27
Hi Bioterror,

Many thanks for your reply I will try to do as you say but I normally get no warning when it is going to happen, the first I know about it is when the mouse stops moving I maybe should have also mentioned that the keyboard becomes inactive as well so I most probably will not be able to do as you suggest.

---

### Post by amjjawad on 2010-10-27
Does your screen turn to black or whatever you have on desktop turn to be gray and you can't do anything about it (frozen)? there's much difference between both cases.

---

### Post by billyfish010 on 2010-10-27
Hi amjjawad,

To clarify the mouse stops moving the keyboard stops working and after a few seconds the screen goes black leaving me with no choice but to press the reset button to restart the computer.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi amjjawad,

To clarify the mouse stops moving the keyboard stops working and after a few seconds the screen goes black leaving me with no choice but to press the reset button to restart the computer.

Hi :)

Would you please list your machine's specifications? how did you install Ubuntu? are you dual booting with Windows?
Any more details will be helpful :)

---

### Post by billyfish010 on 2010-10-27
Hi amjjawad,

Yes I am dual booting with windows 7, not sure what specs you want from my computer. I cant remember which motherboard is fitted but the CPU is an AMD965 4 core processor and I am using DDR3 memory. If you need more info on my computer I could find out more info. The Motherboard is a Gigabyte 880GM with USB 3.

---

### Post by Hatsune Miku on 2010-10-27
> **billyfish010 said:**
> Hi amjjawad,

Yes I am dual booting with windows 7, not sure what specs you want from my computer. I cant remember which motherboard is fitted but the CPU is an AMD965 4 core processor and I am using DDR3 memory. If you need more info on my computer I could find out more info.

Hey! And Welcome! This sounds like a X.org HerpAderp. Could you tell us your Graphics card type and (If any) Graphics drivers you installed. Along with you Desktop and/or Window Manager (GNOME, KDA, FLuxBOx, Rat Posion,etc)

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi amjjawad,

Yes I am dual booting with windows 7, not sure what specs you want from my computer. I cant remember which motherboard is fitted but the CPU is an AMD965 4 core processor and I am using DDR3 memory. If you need more info on my computer I could find out more info.

Hello billyfish,

Okay, in order to get as much help as possible, you need to provide information about your situation as much as possible.

To make it easier for you:
1- How did you install Ubuntu? Wubi? LiveCD/LiveUSB?
2- Do you still have your LiveCD or LiveUSB?
3- Are you facing the same issue with Windows?

Thanks!

---

### Post by billyfish010 on 2010-10-27
Hi amjjawad,

Installed with a live Cd.
No problem with Windows 7.
I still have the live CD.

Regards

Bill

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi amjjawad,

Installed with a live Cd.
No problem with Windows 7.

Regards

Bill


Great, thanks :)

Now, insert your LiveCD into your drive, reboot your machine and start the live session.
Try to use your machine while you're booting from the LiveCD. If the same problem will occur, then we could walk you through the next step.
If the problem did not occur, it means there might be something wrong with the installation. Partitioning issues perhaps or something else.

So, the best way to find out is to boot from the LiveCD :)

---

### Post by billyfish010 on 2010-10-27
Ok! will try it now and come back with any findings but it may take a while since while it always happens sometimes it takes an hour to happen and on other occasions it happens within minutes.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Ok! will try it now and come back with any findings but it may take a while since while it always happens sometimes it takes an hour to happen and on other occasions it happens within minutes.

I'm subscribed to this thread so whenever you come back and post, I'll be notified, not to mention I'm almost 24/7 online either here or doing something else.

Take my advice, keep testing it for hours, even if you have to do that for a day.
Let's see what will happen.

Good luck :)

---

### Post by billyfish010 on 2010-10-27
Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822")

I am now using the LiveCD and so far all is okay but I will keep you advised and I will take note of what I was doing when the computer crashed. This could be hard since in comparison with the normal system it is so slow, though not so it is a problem to use.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822")

I am now using the LiveCD and so far all is okay but I will keep you advised and I will take note of what I was doing when the computer crashed. This could be hard since in comparison with the normal system it is so slow, though not so it is a problem to use.


Yes, I know it's slow but keep in mind that this is the best and the first step to be taken :)

Take your time and hopefully we could find a solution to your issue :)

---

### Post by billyfish010 on 2010-10-27
Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Yes I take your point and will keep on using it but it may be worth mentioning that in this mode the graphics card is not using the drivers that it uses when it is fully installed on the hard drive.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Yes I take your point and will keep on using it but it may be worth mentioning that in this mode the graphics card is not using the drivers that it uses when it is fully installed on the hard drive.

What Graphics Card do you have? Nvidia?

---

### Post by billyfish010 on 2010-10-27
Yes I believe it is - why is that a problem because I use Ubuntu on another computer with an NVidia card with no problems and it is a dual boot with windows 7 ultimate as well.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Yes I believe it is - why is that a problem because I use Ubuntu on another computer with an NVidia card with no problems and it is a dual boot with windows 7 ultimate as well.

The whole idea of using the LiveCD is to make sure the machine will work fine before installing Ubuntu. Theoretically, after installing Ubuntu and update it for the first time, especially when you'll update the Kernel, some drivers issues should be fixed. Nvidia is very well-known but I have no clue why exactly it has some compatibility issue with Ubuntu.
As in your case, if the driver of your Graphics Card is the issue and if what you're saying is correct (the current driver is different from the one which is already installed), then a kernel update or other solutions could do the needful.

In my opinion, it doesn't make sense that your machine will work perfectly from the LiveCD and will not after installation.

Anyway, it's better to stop guessing and let's see what will happen :)

---

### Post by billyfish010 on 2010-10-27
Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

I only know it is different because when I first installed Ubuntu the hardware drivers icon appeared on the top bar after looking at it and reading what was there I installed the updated drivers for my NVidia card in Ubuntu but I don't think this is the problem since it has run for several weeks before the problem I have identified occurred.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

I only know it is different because when I first installed Ubuntu the hardware drivers icon appeared on the top bar after looking at it and reading what was there I installed the updated drivers for my NVidia card in Ubuntu but I don't think this is the problem since it has run for several weeks before the problem I have identified occurred.

Ok, good to know that.
Let's wait and see what will happen.

Are you posting/writing here from the Live Session? try to use that machine, don't leave it idle :)

---

### Post by billyfish010 on 2010-10-27
Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Yes I am and I am also using the machine for browsing the internet and switching between pages while waiting for it to happen and reading your replies. Speaking of replies many thanks for giving me your time it is appreciated and with luck we may resolve the issue since once I have full confidence in Ubuntu I am going to take Windows 7 of my four computers and just have Ubuntu installed on it's own.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Yes I am and I am also using the machine for browsing the internet and switching between pages while waiting for it to happen and reading your replies. 

Yes, that's great, thank you :)

> 
Speaking of replies many thanks for giving me your time it is appreciated and with luck we may resolve the issue since once I have full confidence in Ubuntu I am going to take Windows 7 of my four computers and just have Ubuntu installed on it's own.
The main reason why I'm using Ubuntu is this great forum. Honestly, what I've learned and still learning here was much better and faster than what I had learned in 10 years with Windows.
I'm learning new stuff every day and that's why I spend most of the time here. Solving others' problems is THE BEST source of experience. Of course reading more about Ubuntu and Linux is another great source.

You welcome and I'll be glad if you'll manage to fix your problem :)
I remember when I first posted here, I was so frustrated, confused, etc but I'm not anymore. It's not that I know everything but it's my belief that the more time I spend in learning, the better I'll be.

By the way, you'll find very useful stuff in my signature. I'm trying to maintain that facebook's page and I'm trying to update it on daily basis. You'll find some steps which in my humble opinion, these steps should be the first thing that anyone must do :)

Linux rules as always :D

---

### Post by billyfish010 on 2010-10-27
Wow! there is some info in there - I will be browsing it this afternoon and maybe I will learn a bit more about Ubuntu I have to say I am quite good with windows and can sort most problems myself but this is a whole new world and to be honest I am enjoying using Ubuntu. I have to say it is not yet as slick as Windows but it is only going to improve if people keep using it. I first started using Linux Os systems at the very start and have dabbled with it on and off for a number of years but the latest long term system is so far removed from how it all began. Incidentally I have several programs installed in Wine would this have any effect on Ubuntu. The programs are - Office 2007, Tunebite, DvdFab, imgburn, dvd shrink, Nero, Readon TV Player and lastly Quicktime. They all work okay.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Wow! there is some info in there - I will be browsing it this afternoon and maybe I will learn a bit more about Ubuntu

Yes, I made sure to add the basics that every beginner including myself might need. I made that page to help me so that I could access whatever I need from there. I'm a person who'd love to try new stuff and if you check my signature -My PC, you'll come to know how exactly I love to try new stuff :)
I could simply bookmark these important stuff but it's better to make it public so others might find it helpful too.

> 
but this is a whole new world and to be honest I am enjoying using Ubuntu. 

Ditto :)

> 
I have to say it is not yet as slick as Windows but it is only going to improve if people keep using it. I first started using Linux Os systems at the very start and have dabbled with it on and off for a number of years but the latest long term system is so far removed from how it all began. 

I've been with Ubuntu for a month or so and believe it or not, I've learned much more than I had in 10 years. This world is the best world and this path is the righteous one :)

[B]If Windows could open a new window for you, Linux could open DOORS and these doors for a better future.
[/B]

> 
Incidentally I have several programs installed in Wine would this have any effect on Ubuntu. The programs are - Office 2007, Tunebite, DvdFab, imgburn, dvd shrink, Nero, Readon TV Player and lastly Quicktime. They all work okay.

IMHO, I'd use Windows to run Native-Windows Programs or use the equivalent to such programs in Linux. But that's me.
I keep my XP just to use Photoshop and Office. Guess what? I'm unable to login to XP not because I have a problem but because Linux's Charm has taken my mind :)
Wine as I've heard is nice and useful tool but if you ask me, I prefer to use Windows to run programs made for Windows.

Oh, as for Nero, I love it for sure but I found a great program that might help you. K3b is a great program. You could find it in Synaptic Package Manager and install it.

Again, IMHO, I think there's no clone for Photoshop and Office. These two are really unique in my opinion :)

---

### Post by billyfish010 on 2010-10-27
Yes I have Photoshop CS5 and wouldn't part with it I may eventually try to load it into Ubuntu but I think it may be too new since it appears from what I have been able ascertain that Wine is only equivalent to Windows XP Pro. Of course I may be wrong but whenever I try to load in some programs I get a message advising me to update to a later version of Windows. By the way I have used Gimp a few times and I really like it.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Yes I have Photoshop CS5 and wouldn't part with it I may eventually try to load it into Ubuntu but I think it may be too new since it appears from what I have been able ascertain that Wine is only equivalent to Windows XP Pro. Of course I may be wrong but whenever I try to load in some programs I get a message advising me to update to a later version of Windows. By the way I have used Gimp a few times and I really like it.

Honestly I've never tried Wine and not willing to at the moment. Perhaps later :)

I tried GIMP but I still prefer Photoshop. My version is CS2.

---

### Post by billyfish010 on 2010-10-27
Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Just had a brief look at K3B and it looks interesting but before I can try it I will have to reboot but that will be in a few hours time. I am using the computer all the time and so far I am not getting the error should I carry on as I am or should I just reboot and see if the error happens on my normal program.

---

### Post by amjjawad on 2010-10-27
> **billyfish010 said:**
> Hi [amjjawad]("http://ubuntuforums.org/member.php?u=941822"),

Just had a brief look at K3B and it looks interesting but before I can try it I will have to reboot but that will be in a few hours time. I am using the computer all the time and so far I am not getting the error should I carry on as I am or should I just reboot and see if the error happens on my normal program.

As for K3B, try to install it later. While you're on the LiveCD, no changes will be made to your machine.

Yes, carry on, I suggest to keep using it. We're trying to produce the error that that might take some time :)

---

### Post by billyfish010 on 2010-10-27
Two programs I missed off from my Wine installation were Power DVD and Windows Commander. While browsing the files on my Ubuntu system I noticed a debug log but I don't know if it has any relevance to Ubuntu I have pasted it below.

[1023/124523:ERROR:o3d/core/cross/message_queue.cc(402)] Failed to send boolean response to client handle : Broken pipe

Like I said I haven't a clue what it means but there is about 100 of those and they are almost all identical with just the odd change in number.

Bill

---

