---
title: "Installing Xp using Ubuntu?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Joe_Ib on 2010-02-09
Hello, I am new to Ubuntu and was wondering if there is a way to install Xp or another version of Ubuntu, using Ubuntu (I got a free laptop with only Ubuntu on it).

---

### Post by SteveHillier on 2010-02-09
Are you looking to dual boot your machine?
Are you looking to virtualisation?
Are you looking to run them side by side or one or the other?
Each of these requires a different solution.

---

### Post by Joe_Ib on 2010-02-09
I would like to be able to duel boot.

---

### Post by pricetech on 2010-02-09
Do you have a licensed copy of XP ??

---

### Post by Geoff918 on 2010-02-09
Depending on your hardware you could run XP in a VirtualBox (available in the repositories--at least the OpenSourceEdition). Or, you could probably wipe out the Ubuntu install by simply booting from the XP media. Are you interested in using Ubuntu, or just ignoring it. If you have no interest, you may as well just wipe the disk and install XP. (Just be sure to get any drivers that you'll need before doing so, one major weakness in XP currently is that the hardware support may be lacking in the default install by now).

---

### Post by Joe_Ib on 2010-02-09
I do not have a licensed disk for Xp or any other windows OS.  I believe as though the laptop I got may have some things wrong with it as there seem to be a few things that do not work very well.  I guess I am asking if there is a way to make sure that the laptop is clean of anything wrong.

---

### Post by DenysT on 2010-02-09
> **Joe_Ib said:**
> I do not have a licensed disk for Xp or any other windows OS.  I believe as though the laptop I got may have some things wrong with it as there seem to be a few things that do not work very well.  I guess I am asking if there is a way to make sure that the laptop is clean of anything wrong.

Installing XP won't help you find out if anything is wrong as it is dependent on OEM drivers, especially laptops. You would need to go to the manufacturer's support page and download all the drivers for XP if you had legal copy of XP to install. If Ubuntu installed you probably only need to find out what hardware is not working right and post back. Someone on the forum can point in you the right direction to get it working right.

---

### Post by Joe_Ib on 2010-02-09
It not that there is necessarily anything wrong.  Say this laptop is Key logged (not saying it is)  would I be able to get rid of any harmful things on my laptop by installing Ubuntu again?   

If so how do I go about doing this with only Ubuntu (nothing else is on this laptop) need any information on anything like drivers or something of that nature I do not know what it is so could you also inform me on how I can find out so I can make it more easier for others to help.

---

### Post by HappyFeet on 2010-02-09
Download the [Live CD]("http://www.ubuntu.com/getubuntu/download"), that will allow you to try ubuntu without installing it. If everything works OK, just press install. But remember, using a live cd is a lot slower than a real install.

---

### Post by marshmallow1304 on 2010-02-10
If you install from the LiveCD as HappyFeet suggests, you can select "Erase and use entire disk", which will result in a clean and fresh install.

---

### Post by Joe_Ib on 2010-02-10
Only one problem the laptop does not have a CD writer so I can not burn a CD with Ubuntu on it.  How might I go about installing a fresh version of Ubuntu with out a Cd (if that is even possible)

---

### Post by semperfizh on 2010-02-10
> **Joe_Ib said:**
> Only one problem the laptop does not have a CD writer so I can not burn a CD with Ubuntu on it.  How might I go about installing a fresh version of Ubuntu with out a Cd (if that is even possible)

Use an usb stick. For that, download ubuntu iso. Go to System -> Administration ->
USB Startup Disk Creator.  Follow instructions, i.e. put in the path of your
downloaded ubuntu iso. Then start. After that you should reboot and enter BIOS
Choose in BIOS the option to boot from an usb stick and voila!

PS. Format your usb stick if necessary

---

### Post by Joe_Ib on 2010-02-10
Will I have to do that every time I boot my laptop?

---

### Post by mwcrowley on 2010-02-10
No, once you change the BIOS setting to boot from USB it will always look for a usb to boot from until you change the setting.  Usually the BIOS has settings for a first, second, third, etc., to boot from.  Just remember to make the hard drive second, so when you reboot after the installation it will look to the hard drive when the usb is not plugged in.

---

### Post by Joe_Ib on 2010-02-10
Ok I am going to go buy a usb today then any size recommended like more then 4gb should be plenty right? and after i boot from usb could i then remove the usb?

---

### Post by semperfizh on 2010-02-10
> **Joe_Ib said:**
> Ok I am going to go buy a usb today then any size recommended like more then 4gb should be plenty right? and after i boot from usb could i then remove the usb?
 


First: check your BIOS if you can boot from usb at all! Normaly this is the case.
Second: you dont need more than 4gb, I use 2gb and its more than enough.
Third: When you start your machine with ubuntu usb, you will have options 
         to test it or to install it (and some others).
Forth: Once you installed ubuntu, you can reboot and change settings in BIOS 
          in the same way as before to boot primary from HD.
Fifth: Note that if you test ubuntu from usb stick, it is slower and
        needs long time to boot, so dont panic if nothing is happening in a first few
        moments

IMPORTANT: If you are testing the system from usb or installing and rebooting dont pull out your usb stick!
                   After final installation and reboot from hd you can remove usb.

If you need any more help, dont hesitate to ask us ;)

---

### Post by Joe_Ib on 2010-02-10
Could I get directions on how to check BIOS to see if I can start from USB please and thank you

---

### Post by pricetech on 2010-02-10
I can't point you to the USB Guide, but another option, since you don't have a burner, is to order the disk via ShipIt.

---

### Post by Joe_Ib on 2010-02-10
I would have to ask my parents if they could order it and I think they would say no.  I appreciate the advice though.

---

### Post by semperfizh on 2010-02-10
> **Joe_Ib said:**
> Could I get directions on how to check BIOS to see if I can start from USB please and thank you

You should find out which laptop model you have. Otherwise I cannot say.
You can of course always google for "boot from usb <your laptop model>"
Anyway, most modern computers support that option.

However you should test it, it is useful to know if you can boot from usb anyway

---

### Post by semperfizh on 2010-02-10
> **Joe_Ib said:**
> I would have to ask my parents if they could order it and I think they would say no.  I appreciate the advice though.

Ask parents? Why would they say 'no'? You can ask a friend if somebody can burn it
for you. 

PS. How old are you? Sorry if this question is too personal, I am just confused why 
your parents would be against it. You dont have to answer it though ;)

---

### Post by Joe_Ib on 2010-02-10
Okay thanks for the help.  Sorry for probably asking stupid questions haha.  Looking forward though to learning about Ubuntu and the Unix community.  One last thing I am what you could consider a first time computer user never have I touched one so how do i tell what type of Laptop I have?  


ps to answer your question I am 10 and my parents are already a little mad that I got this laptop even though it was free.

---

### Post by audiomick on 2010-02-10
Brand name is easy, it will be prominently printed on the case somewhere.
Usually there is a sticker on the bottom somewhere with the model number on it.

If you want to find out what the processor is, look at
system> administration> system monitor
on the first tab. You should be able to see that there.

If you want to see a bit more that that, you could open a terminal and do
```
lspci
```which will show you information about what is plugged into the PCI slots of the machine, things like the graphics card and the network card.

---

### Post by semperfizh on 2010-02-10
> **Joe_Ib said:**
> Okay thanks for the help.  Sorry for probably asking stupid questions haha.  Looking forward though to learning about Ubuntu and the Unix community.  One last thing I am what you could consider a first time computer user never have I touched one so how do i tell what type of Laptop I have?  


ps to answer your question I am 10 and my parents are already a little mad that I got this laptop even though it was free.

Ask the person who gave you the laptop. Since you have never used a pc
before, it would be the easiest way to ask a friend to burn an ubuntu LiveCD for you.

And tell your parents that if you start working with Linux at that age, that
you will find a very good job later and earn a lot of money

Cheers, I am off now, have to go. Check on you later.

---

### Post by audiomick on 2010-02-10
What is it exactly that you think is not working properly? Maybe, if you describe it, someone can just tell you if they think that is normal behaviour or not.

---

### Post by Joe_Ib on 2010-02-10
I did the terminal command and could not even begin to understand anything that popped up.

Where in System Monitor does it say what type of laptop I have.  I see in this order


Ubuntu:
Release9.10 (karmic)
Kernel Linux 2.6.31-19-gerneric
GNOME 2.28.1

Hardware:
Memory: 2.7GiB
Processor0: AMD Turion(tm) x2 duel-core mobile rm-72
Precessor1: AMD Turion(tm) x2 duel-core mobile rm-72

System Status Available disk space: 262.2 GiB

---

### Post by Joe_Ib on 2010-02-10
There are some files that wont open when tried to open.  There are about 4 random square lines spaced though out the desktop.  Plus I just don't trust the person who gave me the laptop.

And I looked at CPU usage it seems to be at 64% at all times even when not doing anything other then looking at this forum.

---

### Post by audiomick on 2010-02-10
As I said, for the manufacturer of the laptop, there will be a brand on the case somewhere (unless it is old enough to have worn off) and there is nearly always a sticker on the bottom with the model number on it.

What you are seeing here is
> **Joe_Ib said:**
> 
Ubuntu:
Release9.10 (karmic)
Kernel Linux 2.6.31-19-gerneric
GNOME 2.28.1

Hardware:
Memory: 2.7GiB
Processor0: AMD Turion(tm) x2 duel-core mobile rm-72
Precessor1: AMD Turion(tm) x2 duel-core mobile rm-72

System Status Available disk space: 262.2 GiB
under "ubuntu"
the version of Ubuntu that is installed on the computer

Under "hardware"
"memory" is how much RAM you have. That is a memory that the system uses as it is working.

"processor" is the Central Processing Unit, CPU, which is the "brain" of the computer. Yours was made by the company AMD. There are two entries because the CPU has to cores, i.e. two processing units in the one chip. This is fairly common these days, and there are some that have 4 and are referred to as "quad core".

The entry for "system status available disk space" is telling you that you still have 262.2 Gigabytes of free space on your drive, which is a fair amount as long as you don't need to store stacks of movies or something.

All in all, that adds up to a quite useful computer that should do well for the next 3 or 4 years.

---

### Post by Joe_Ib on 2010-02-10
It is a HP laptop other then that couldn't tell you I looked for the stickers you said but i see non anywhere although there appears to have been some because there is some black sticky residue under the keyboard to the left and right of the mouse pad in the center.

---

### Post by audiomick on 2010-02-10
Ok.
The thing with the lines through the desktop sounds like there might be a problem there, but I would have to see it for sure.

The CPU usage sounds a bit high too...

As far as opening files goes, there are a lot of files on the system that the normal user can't open, and this is quite ok, because you don't want to be messing around with them.

If you just got the laptop, doing a fresh install might not be a bad idea. I would say ask the person who gave it to you if the system was installed fresh before you got it, but if you don't trust that person, maybe you don't want to ask that.

---

### Post by audiomick on 2010-02-10
HP is Hewlett Packard. It is possible that the stickers are all gone. Did you turn the laptop over and look on the underside?
The sticky marks around where the touchpad is are probably not the sticker with the model name. In that area, there are very often stickers that are effectively advertising showing which brand of CPU is in there, and often which version of windows was originally installed.

---

### Post by Joe_Ib on 2010-02-10
> **audiomick said:**
> Ok.
The thing with the lines through the desktop sounds like there might be a problem there, but I would have to see it for sure.

The CPU usage sounds a bit high too...

As far as opening files goes, there are a lot of files on the system that the normal user can't open, and this is quite ok, because you don't want to be messing around with them.

If you just got the laptop, doing a fresh install might not be a bad idea. I would say ask the person who gave it to you if the system was installed fresh before you got it, but if you don't trust that person, maybe you don't want to ask that.

 I will best try to describe the lines.  It is just a box I can see the background picture through the lines and inside the box it just appears to be like a bulging on the picture were the lines are.  Kind of like a 3d effect when drawing.

---

### Post by Joe_Ib on 2010-02-10
the only sticker i found was a windows vista sticker that had a red x drawn on top of it. (assuming the previous owner did not like vista)

---

### Post by audiomick on 2010-02-10
> **Joe_Ib said:**
> I will best try to describe the lines.  It is just a box I can see the background picture through the lines and inside the box it just appears to be like a bulging on the picture were the lines are.  Kind of like a 3d effect when drawing.
That doesn't sound like something is broken. It sounds more like some effect is turned on, or a visual aid. There are some things that work like a magnifying glass and make the picture on the screen bigger.
I would really have to see it to say anything more definite than that. Maybe someone else will read this and recognize what it is from your description.

---

### Post by Joe_Ib on 2010-02-10
I guess to be honest my question was already answered now It is more so of me just figuring information out that might be useful and never hurts to know stuff.

If this is breaking rules of the forum sorry.  Just wanted to figure out the best way to make sure the laptop is clean of anything wrong and how I can go about doing this.  I plan to never use anything other then Ubuntu on it.  Will I run into any problems if all I have for a Os is Ubuntu (if Ubuntu counts as an OS).

---

### Post by audiomick on 2010-02-10
> **Joe_Ib said:**
> I guess to be honest my question was already answered now It is more so of me just figuring information out that might be useful and never hurts to know stuff.

If this is breaking rules of the forum sorry.  Just wanted to figure out the best way to make sure the laptop is clean of anything wrong and how I can go about doing this.  I plan to never use anything other then Ubuntu on it.  Will I run into any problems if all I have for a Os is Ubuntu (if Ubuntu counts as an OS).
No, you are not breaking any rules, that is what the forum is for.

Yes, Ubuntu is an OS, an Operating System, same as Windows and Mac OSX are.

The question of whether you will run into problems if you only have Ubuntu is not that easy to answer. Reality is, if you use a computer at all, you will run into problems one day, no matter what OS you are using. I would imagine that for a start you will only be using the computer for Internet and writing stuff. For that, Ubuntu is as good as any, and better for the internet because there is a far lower chance of picking up a virus or anything nasty like that on Ubuntu.

I would suggest you look at the threads for beginners at the top of this section of the forum.

Have fun with the computer.

---

### Post by Joe_Ib on 2010-02-10
So if I only have Ubuntu I can install any windows game on it and have the game run perfectly normal like it would on a Windows OS?

---

### Post by Surkow on 2010-02-10
> **Joe_Ib said:**
> So if I only have Ubuntu I can install any windows game on it and have the game run perfectly normal like it would on a Windows OS?

Windows games or programs will not natively run on Ubuntu. Depending on the games you want play you could use a program called Wine which will allow you the execute Windows programs in Ubuntu. I would not recommend you to try this if you have little or no experience with Ubuntu. So you cannot install Windows games on Ubuntu like you normally do on Windows. Linux has games of its own and most of them can be downloaded for free.

---

### Post by Joe_Ib on 2010-02-10
Thanks Surkow for the answer.

Does anyone know how I might go about installing a new version of Ubuntu?

I have a disc now and all I want to do is make sure I have a clean version of Ubuntu and I do not know how to re-install Ubuntu using the disc in Ubuntu.

---

### Post by audiomick on 2010-02-11
Hi Joe,
here is a link to the instructions for installing.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
read it through a couple of times before you start.

There is a link on there called "BootFromCD". Have a look at that too. It may be that your computer is set to boot from the CD, it may be that you will have to follow that link to make it do this. You will have to try it and see.

By the way, if you want to know why it is called "booting the computer", look here
[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

---

