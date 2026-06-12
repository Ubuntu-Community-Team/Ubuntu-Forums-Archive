---
title: "How to get...basically everything to work"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by greenspeed on 2009-06-17
I tried ubuntu like a week ago and had an error 22 problem that resulted in my having to reformat and run ubuntu only.

I have a asus EEE pc 1000he that didn't come with a boot disk for xp home.  however I downloaded ubuntu and decided that since the error wasn't able to be fixed I was going to abandon the idea and not run a dual boot.

So here is my problem.  do i need a boot disk to run virtual box off of? is there a program that i can run an emulator of windows while using linux...i know there is some for macs.  And lastly how in the hell can i get romraider to download...i went to their site, downloaded the file, saving it to my desktop, and i keep getting an error while trying to install it.  I even tried in terminal, but sudo apt-get install romraider gets me a no package error

many thanks mates

---

### Post by Cheesemill on 2009-06-17
VirtualBox can be used to 'emulate' Windows whilst running Ubuntu, you will however need a Windows disc to install with. Bear in mind this has to be a full installation disc, the recovery discs that you get with most computers nowadays are locked to specific physical hardware which means they won't install onto the virtual machine that VirtualBox will give you.

---

### Post by cdwillis on 2009-06-17
Just install virtualbox and download an image of XP Home. You can use the key on the bottom of the 1000HE to install it within virtuablbox. Did you download Rom Raider as a Windows executable or what? If you look in the Synaptic Package Manager you might find it to install that way.

---

### Post by Cheesemill on 2009-06-17
RomRaider is a Java application, to run it you need to have Java installed. You can do this by typing the following into a terminal:
```
sudo apt-get update && sudo apt-get install sun-java6-jre
```(hit TAB then Enter to accept the license agreement)

You can then right-click on the file you downloaded and select 'Open with Sun Java 6 Runtime' to start the installation.

---

### Post by greenspeed on 2009-06-17
well i don't have a disk drive the only solution i could see if i could get a install of something like windows me or 98 off of mininova and flash it to my usb flash drive...as It would be easer than trying to inquire an xp disk...is my thought.

also when you download a program off a website what is the typical root file for installing with linux.  I know for windows it's .exe...thanks

---

### Post by Cheesemill on 2009-06-17
> **greenspeed said:**
> also when you download a program off a website what is the typical root file for installing with linux.  I know for windows it's .exe...thanks

Downloading files from websites is not the prefered way to install software in Ubuntu, it should only be done as a very last resort and **only if you know exactly what you're doing** (I've given you instructions for RomRaider because this is the only way to get it working).

See here for how to install applications in Ubuntu:[FONT=monospace]
[/FONT][http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)[FONT=monospace]
[/FONT]

---

### Post by greenspeed on 2009-06-17
here is a link i found for xp home sp2 idk if it's a valid one and if i should got with the diskette image or the other option

[http://www.allbootdisks.com/download/xphome.html](http://www.allbootdisks.com/download/xphome.html)

---

### Post by Cheesemill on 2009-06-17
That's just a boot disc you've found, it won't install Windows.
You need a full **legal** Windows install CD to install XP into VirtualBox.

---

### Post by greenspeed on 2009-06-17
where can i get a full install disk for xp home? or would it be easier to get full install of 98 off of mininova I only have to fun windows for ecu edit, and learning mode for my tuning of my subie...the rest i can run off of ubuntu and be fine.

also using the java install for romraide is that off of romraiders site or only after i've downloaded the package and I haven't extracted it yet?

---

### Post by cariboo on 2009-06-17
You shoud be able to purchase a copy of Windows XP Home from any reputable computer retailer for about $150CDN.

BTW if I see any links or mention of pirated copies of windows this complete thread will be jailed

---

### Post by Cheesemill on 2009-06-17
You can get a copy of XP Home either from Ebay or any computer shop.

As for RomRaider make sure you have installed Java first as stated in my above post, then download the RomRaider0.5.2-223-linux.jar file from their website (which is the file I think you already have), then right-click on it and run it with Java.

---

### Post by theozzlives on 2009-06-17
If you don't have an XP CD, the only legal thing I can think of is to see if Microsoft is still offering Windows 7 RC for download. It's an ISO file which will work with VirtualBox.

---

### Post by Cheesemill on 2009-06-17
> **theozzlives said:**
> If you don't have an XP CD, the only legal thing I can think of is to see if Microsoft is still offering Windows 7 RC for download. It's an ISO file which will work with VirtualBox.

I wouldn't want to try running Windows 7 in a VM on an EEE PC with an Atom processor :shock:

---

### Post by greenspeed on 2009-06-17
well i have java installed and flash installed but i am also getting this error message on youtube...

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/"). 						Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").

---

### Post by Cheesemill on 2009-06-17
How did you install Flash?

---

### Post by greenspeed on 2009-06-17
okay thanks a ton...romraider is installing as I type.

I'll keep the talk of illegal windows copies out of here, and lastly i was thinking of runnning 7 cause it is offered for free, but i am not going to run it on an atom until i find someone else that has done it.  as it is i had issues runnig a dual boot on my system and it was sweet while it lasted.

since my system came with a product key to it for home xp would windows send me a install disk for it if I contacted them?

---

### Post by greenspeed on 2009-06-17
> **Cheesemill said:**
> How did you install Flash?

sudo apt-get update i tried 

then off their website then right clicked and install using gdebi install package...

---

### Post by Cheesemill on 2009-06-17
> **greenspeed said:**
> since my system came with a product key to it for home xp would windows send me a install disk for it if I contacted them?

That's not up to Microsoft, you'd have to contact you computer manufacturer and ask them.
You will only have an OEM license for XP so you could only install it on the physical hardware, the license agreement won't let you install it in VirtualBox.

---

### Post by greenspeed on 2009-06-17
alright and romraider is up and running...we're all good there...do you know of a burning software like ecuedit that is supported by linux? also a program to read trouble codes that's linux based.  if so i won't have to ever run windows and worry about virtual box emulation

---

### Post by Cheesemill on 2009-06-17
They look like highly specialised pieces of software to me, I don't think you'll be able to find any Linux equivalents.
You could try running them under Wine but I've no idea if you'll have any success with that.

---

### Post by greenspeed on 2009-06-17
is wine a style of windows emulation software?

---

### Post by Cheesemill on 2009-06-17
**W**ine **I**s **N**ot an **E**mulator

WINE is a translation layer that lets you run some Windows programs natively under Linux without having to have a copy of Windows. Some apps will run perfectly whereas others won't even run their installers. Check out the homepage at [http://www.winehq.org](http://www.winehq.org) for more info, there's also a Wine section on these forums if you need more help.

Anyway good luck with your Ubuntu experience, I'm signing off for the night (got to get up for work in 4 hours) 8-[

---

### Post by greenspeed on 2009-06-17
thanks for the help i'm ganna try wine and see where it gets me

---

### Post by H2SO_four on 2009-06-17
> **Cheesemill said:**
> I wouldn't want to try running Windows 7 in a VM on an EEE PC with an Atom processor :shock:

+1, It runs just barely ok in my computer, I couldn't imagine it on a EEE PC :(

---

### Post by greenspeed on 2009-06-18
well i've encountered another problem.  I went to do some logging and i can't get the driver to install...it's a windows based driver but they make a linux version of the software you can log with...this is romraider...well with the wizard running it gives me an install failed warning everytime i try to install it using wine, since it's an exe extension and i can't run it in ubunut

---

### Post by greenspeed on 2009-06-18
well I've decided to try windows 7 running in a VM set up...i'll let you all know how it goes if i get it to work...my super fast atom processor and my 1gb of ram will make that os run like a honda boy from the cops...there might be a lot of smoke and a show, but it might not get me anywhere...

results to come in like 30 hours when this download completes

---

### Post by H2SO_four on 2009-06-18
> **greenspeed said:**
> well I've decided to try windows 7 running in a VM set up...i'll let you all know how it goes if i get it to work...my super fast atom processor and my 1gb of ram will make that os run like a honda boy from the cops...there might be a lot of smoke and a show, but it might not get me anywhere...

results to come in like 30 hours when this download completes

It might run as well as a civic that needs a new clutch.  Lots of noise, but you aren't going anywhere fast.

---

### Post by greenspeed on 2009-06-18
I'm just curious if my chances of it running the best would be using a dual boot or running the vm...as it is i just reformated so i have nothing on my comp.

---

### Post by Cheesemill on 2009-06-18
If you can get an XP recovery disc from Asus (or use the Windows 7 RC) then I'd dual boot if I were you.

The specialist applications that you want to run make heavy use of the serial or USB ports if I'm right, this is an area where VM's and WINE aren't perfect.

I don't think I'd want to risk flashing my cars ECU with either of those solutions so I'd definitely go dual-boot if you have the disc space.

---

### Post by greenspeed on 2009-06-20
I've got 150gb of free space...so once 7 finishes it's download...the wireless where i am sucks, I'm going to  run windows as a main, then use my flash drive with ubuntu to re install and do the dual boot i have to agree with you cheesemill on the issue that i need full working windows os for my flashing and stuff for my car

---

### Post by greenspeed on 2009-06-23
Still working on downloading 7...it's impossible when the wireless is terrible and I have no wired connection available!

---

### Post by presence1960 on 2009-06-23
> **greenspeed said:**
> here is a link i found for xp home sp2 idk if it's a valid one and if i should got with the diskette image or the other option

[http://www.allbootdisks.com/download/xphome.html](http://www.allbootdisks.com/download/xphome.html)

lolololol!!  my side hurts now from laughing.

---

### Post by hitman_dreams on 2009-08-11
Have you tried looking on NASIOC or other Subie forums for some of the info on romraider and such? I would suggest looking there, I'm in the process of getting romraider for my car as we speak. Read Unibomers FAQ at NASIOC for engine management under open source...if you are having trouble with Ubuntu, re-evaluate if you should really be doing this all together. Research, research, and research some more.

---

