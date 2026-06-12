---
title: "I need help!"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Lighthugger on 2010-02-22
Hello,

First of all I need to preface this with I am way out of my league and have zero familiarity with Kubuntu. Having said that I figure out things fast if given good direction. Secondly-At this point I am tempted to just go back to Win7 as that WAS what was on my box before I tried to duel-boot. Evidentialy I over-wrote that?

I can't get Win7 back at all but I do have a Win7 boot disc and everytime I try to boot it from dvd /cd I get the GRUB and fires right into Kubuntu, so fidlleing around with it I finally figured out GParted (sorta) but now on boot the only thing I get is 

Grub loading.
error: No such partition
grub rescue _  <-----Where underscore is a blinking cursor.

 At this point I have NO idea what I need to do.
I have seen that all the things that were holding me to Windows for the most part can be done on Kubuntu and so ideally (well ideally I'd like to duel boot but if it's this much of a issue I may pass) maybe I can just go with Ubuntu because I need to learn it.

Can anyone help me here? 

I'd really like to use my box again!

Lighty

---

### Post by Temposs on 2010-02-22
OK, your description is a bit confusing, but, let's try...

1) What happens when you boot your system now, with no CD/DVD trying to boot?

2) Am I correct in believing that you have a GParted LiveCD as well as a Windows Install CD, and you can't figure out how to get either one to boot? It seems like you haven't set the CD/DVD drive as your first boot device in your BIOS. Do you know how to check this?

3) It's really simple to set your system to dual boot. First you install Windows over everything. Second you install Ubuntu, and during the install process, you choose to have Ubuntu make a new partition only using the remaining disk space, and not the entire disk space. That's one of the three options during the install process.

---

### Post by brons2 on 2010-02-22
Sounds like you overwrote windows, if it was dual booted, GRUB would give you a menu that had options to boot either Ubuntu (Kubuntu in your case) or Windows.

---

### Post by bug67 on 2010-02-22
Sounds *exactly* like what happened to me:

[http://ubuntuforums.org/showthread.php?t=1401351](http://ubuntuforums.org/showthread.php?t=1401351)

If you used a Live-CD to run gparted and erase the Linux partition, you probably need to reset the Windows Master Boot Record in order to get Windows to boot again.  Either that or do a full Linux or full Windows install.  I had to re-install Linux so I could boot into Windows so I could back up everything.  Then, I wound up just reinstalling Win 7 because, frankly, I have a separate machine I run Linux on just fine.  I didn't really need it on the failed experiment machine.  :)

---

### Post by d3v1150m471c on 2010-02-22
If you hold down shift after you clear the bios screen it will give you OS booting options. windows 7 should be listed. Have you tried this?

---

### Post by Lighthugger on 2010-02-22
> **Temposs said:**
> OK, your description is a bit confusing, but, let's try...

1) What happens when you boot your system now, with no CD/DVD trying to boot?

---It gives me the Grub No partition error above.
> 
2) Am I correct in believing that you have a GParted LiveCD as well as a Windows Install CD, and you can't figure out how to get either one to boot?

---I do have both and a Kubuntu disk, but I have gone into BIOS and set boot order to DVD/CD, and tried multiple times to go into boot order (F11 at start-up) and boot from CD/DVD but in every case I get GRUB loader>boot to Kubuntu which has me log in. Currently this no longer happens because I fiddled with the partitions with GParted and now all I get is the above No Valid Partiion error. and Grub Rescue prompt.
> 
 It seems like you haven't set the CD/DVD drive as your first boot device in your BIOS. Do you know how to check this? 

---I have.
> 
3) It's really simple to set your system to dual boot. First you install Windows over everything. Second you install Ubuntu, and during the install process, you choose to have Ubuntu make a new partition only using the remaining disk space, and not the entire disk space. That's one of the three options during the install process.

---

### Post by Lighthugger on 2010-02-22
> **brons2 said:**
> Sounds like you overwrote windows, if it was dual booted, GRUB would give you a menu that had options to boot either Ubuntu (Kubuntu in your case) or Windows.

Yeah I am pretty sure I prolly did. I have been able to go into boot options and I get like 4 different options to boot Kubuntu and 2 different options to boot memtest.

---

### Post by Lighthugger on 2010-02-22
> **bug67 said:**
> Sounds *exactly* like what happened to me:

[http://ubuntuforums.org/showthread.php?t=1401351](http://ubuntuforums.org/showthread.php?t=1401351)

If you used a Live-CD to run gparted and erase the Linux partition, you probably need to reset the Windows Master Boot Record in order to get Windows to boot again.  Either that or do a full Linux or full Windows install.  I had to re-install Linux so I could boot into Windows so I could back up everything.  Then, I wound up just reinstalling Win 7 because, frankly, I have a separate machine I run Linux on just fine.  I didn't really need it on the failed experiment machine.  :)

Wow I don't understand half of what you said here. lol

---

### Post by Lighthugger on 2010-02-22
> **d3v1150m471c said:**
> If you hold down shift after you clear the bios screen it will give you OS booting options. windows 7 should be listed. Have you tried this?

Ok I get this...MOSTLY...what do you mean by CLEAR Bios, I am assuming you do not mean delete BIOS (not sure if you even can.

---

### Post by arashiko28 on 2010-02-22
[QUOTE]> **Lighthugger said:**
> 
---I do have both and a Kubuntu disk, but I have gone into BIOS and set boot order to DVD/CD, and tried multiple times to go into boot order (F11 at start-up) and boot from CD/DVD but in every case I get GRUB loader>boot to Kubuntu which has me log in. Currently this no longer happens because I fiddled with the partitions with GParted and now all I get is the above No Valid Partiion error. and Grub Rescue prompt.

When you set your bios to boot from your CD/DVD drive, you don't need to press anything, just insert the disk and reboot, after the bios screen passes, you'll see the Kubuntu installer screen where you choose live CD or inmediate installation.

If you still want to go with double boot:
1. You should install first windows and create the partition for it and leaving unpartitioned the size you want to give to Kubuntu.
2. When you change disks, go for live session, that way you can use internet if any doubt comes while installing.
On the top of the installation window you'll see a bar showing your disk and it's partitions, that will give you the area you already designated for Windows. 
3. So with that in mind, choose manual installation and proceed to the next screen.
You will see the windows partition and the unpartitioned space. 
4. Choose the unpartitioned area and create first swap partition, if you're planning on doing stuff like hibernation give it the double of your actual RAM i.e.: RAM 2GB - SWAP 4GB...
5. The rest divide it as you wish, remember assigning /home to that partition.

Hope this will be of any help for you.

---

### Post by Lighthugger on 2010-02-22
> **arashiko28 said:**
> > 

When you set your bios to boot from your CD/DVD drive, you don't need to press anything, just insert the disk and reboot, after the bios screen passes, you'll see the Kubuntu installer screen where you choose live CD or inmediate installation.

[QUOTE]
********
Currently if I let my box boot from CD/DVD I get this and nothing else.

Grub loading.
error: No such partition
grub rescue _


I can't do anything past that.
**********


If you still want to go with double boot:
1. You should install first windows and create the partition for it and leaving unpartitioned the size you want to give to Kubuntu.
2. When you change disks, go for live session, that way you can use internet if any doubt comes while installing.
On the top of the installation window you'll see a bar showing your disk and it's partitions, that will give you the area you already designated for Windows. 
3. So with that in mind, choose manual installation and proceed to the next screen.
You will see the windows partition and the unpartitioned space. 
4. Choose the unpartitioned area and create first swap partition, if you're planning on doing stuff like hibernation give it the double of your actual RAM i.e.: RAM 2GB - SWAP 4GB...
5. The rest divide it as you wish, remember assigning /home to that partition.

Hope this will be of any help for you.

---

### Post by Lighthugger on 2010-02-22
Not sure how these Forums operate but I responded, Not sure anyone can clarify for me?

---

### Post by bug67 on 2010-02-22
> **Lighthugger said:**
> Wow I don't understand half of what you said here. lol

That's too bad because I'm betting all you need to do is reset your Windows Master Boot Record and you'll be able to boot into windows again.  Worth a try anyhow.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If that fails or you are unable for some reason to follow the linked instructions, You need to decide how important the data that's on your Windows partition is.  If it's important, you'll either need to follow the instructions from the above link or reinstall grub/Linux so you can boot into something.

If it's NOT important, well, you can really do anything you want.  Either reinstall Windows or reinstall Linux.  If you're going for a duel boot, install Windows first then Linux.

---

### Post by Lighthugger on 2010-02-22
> **bug67 said:**
> That's too bad because I'm betting all you need to do is reset your Windows Master Boot Record and you'll be able to boot into windows again.  Worth a try anyhow.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If that fails or you are unable for some reason to follow the linked instructions, You need to decide how important the data that's on your Windows partition is.  If it's important, you'll either need to follow the instructions from the above link or reinstall grub/Linux so you can boot into something.

If it's NOT important, well, you can really do anything you want.  Either reinstall Windows or reinstall Linux.  If you're going for a duel boot, install Windows first then Linux.

To be honest, it would be GREAT if I was able to find my Windows. There is really nothing important on the disc so ultimatly I can do anything except it won't boot anything at all.

I will definatlly try the link you left. Somthing is better then nothing. :)

---

### Post by Lighthugger on 2010-02-22
> **bug67 said:**
> That's too bad because I'm betting all you need to do is reset your Windows Master Boot Record and you'll be able to boot into windows again.  Worth a try anyhow.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If that fails or you are unable for some reason to follow the linked instructions, You need to decide how important the data that's on your Windows partition is.  If it's important, you'll either need to follow the instructions from the above link or reinstall grub/Linux so you can boot into something.

If it's NOT important, well, you can really do anything you want.  Either reinstall Windows or reinstall Linux.  If you're going for a duel boot, install Windows first then Linux.

So I went to your link here and first thing off it says at such and such screen do this. I don't get that screen at all. The ONLY screens I get are BIOS if I prompt it, F11 again if I prompt it, and a completly black screen with the error:

Grub Loading.
Error: No Such partition
Grub Rescue_

Can't load Windows, can't load Ubuntu, I can put in GParted Disc but that's it. My Partion is NTFS but I am not sure that helps anyone.

---

### Post by mechro on 2010-02-22
Does the Gparted CD boot?

---

### Post by Dracona on 2010-02-22
I havent used Win 7, but if its like most of there other install cds, when you go to boot from the install cd, it will ask you if you want to boot from cd. this is a timed ( 5-8sec, somewhere in there ) question. if you dont hit any key within set time, then it will go to the second boot device. 

easiest thing to do might be to format from win cd, install win, then install kubuntu/ubuntu  if you still are wishing to dual boot. 
but for this to work, you should have cd/dvd drive set as first boot device.

---

### Post by bug67 on 2010-02-22
> **Lighthugger said:**
> So I went to your link here and first thing off it says at such and such screen do this. I don't get that screen at all. The ONLY screens I get are BIOS if I prompt it, F11 again if I prompt it, and a completly black screen with the error:

Grub Loading.
Error: No Such partition
Grub Rescue_

Can't load Windows, can't load Ubuntu, I can put in GParted Disc but that's it. My Partion is NTFS but I am not sure that helps anyone.

Right, because you need to have either a Windows disk in the disk drive or, a Linux disk in the disk drive.  At this point you are unable to boot at all from you HARD DRIVE.  You need to put either a Windows disk or a Linux disk in your CD/DVD Rom drive and boot from that.  Then, either recover or reinstall.

I think we may all be assuming that you already know how to boot from a CD/DVD.  If not, I can walk you through it.

---

### Post by arashiko28 on 2010-02-22
I've messed up my partitions before and had that same error a couple of times, but never while trying to boot from the CD... 
Are you absolutely sure you have the Kubuntu CD on the CD/DVD drive when you turn it on? Do you leave it there? You have to put it in, and shut down the computer, then turn it back on with the CD inside.

I also found this,
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
With this you can restore your GRUB or MBR... just burn the .iso on a CD and boot from it, it has all the instructions you'll need on the web page and also you can do it on a USB drive, just follow instructions.

Hope this will help you... [sigh] wish I've had that tool a couple of months ago... you are lucky...:wink:

---

### Post by Lighthugger on 2010-02-23
> **arashiko28 said:**
> I've messed up my partitions before and had that same error a couple of times, but never while trying to boot from the CD... 
Are you absolutely sure you have the Kubuntu CD on the CD/DVD drive when you turn it on? Do you leave it there? You have to put it in, and shut down the computer, then turn it back on with the CD inside.

I also found this,

With this you can restore your GRUB or MBR... just burn the .iso on a CD and boot from it, it has all the instructions you'll need on the web page and also you can do it on a USB drive, just follow instructions.

Hope this will help you... [sigh] wish I've had that tool a couple of months ago... you are lucky...:wink:

ok well! I am a work in progress lol. I guess I had not tried the Kubuntu disk. SO...I tried it and it installed Kubuntu. So that is good and it'll just be a matter of time with more posts along this line to try and figure out Wine and Duel-booting etc. but looks good atm. Mucho thanks for all the input everones! If anyone now has any sage advice on how to install Win7 with Kubuntu on the box first then I would accept that link. :) :popcorn:

---

### Post by Lighthugger on 2010-02-23
> **Dracona said:**
> I havent used Win 7, but if its like most of there other install cds, when you go to boot from the install cd, it will ask you if you want to boot from cd. this is a timed ( 5-8sec, somewhere in there ) question. if you dont hit any key within set time, then it will go to the second boot device. 

easiest thing to do might be to format from win cd, install win, then install kubuntu/ubuntu  if you still are wishing to dual boot. 
but for this to work, you should have cd/dvd drive set as first boot device.

Actually THIS made alot of sense. EXCEPT because of GRUB it would not allow boot from anything else. :(

---

### Post by Lighthugger on 2010-02-23
> **bug67 said:**
> Right, because you need to have either a Windows disk in the disk drive or, a Linux disk in the disk drive.  At this point you are unable to boot at all from you HARD DRIVE.  You need to put either a Windows disk or a Linux disk in your CD/DVD Rom drive and boot from that.  Then, either recover or reinstall.

I think we may all be assuming that you already know how to boot from a CD/DVD.  If not, I can walk you through it.

No, I know how to boot from cd/dvd. I thought I said that :/ guess not but thanks for asking. No the issue is GRUB installer kicks in before a boot from CD/DVD can take affect...or so that seems. It worked with my Kubuntu disc because it's the installer for Kubuntu. When I have Kubuntu installed and open and try to install from my burned Win7 Pro disc it claims the disc format or wrong disc somthing. If I try to install Win7 boot from disc at start up, the Grub installer takes over before boot from disc can go into affect. The system just boots Kubuntu.

---

### Post by arashiko28 on 2010-02-23
> **Lighthugger said:**
> ok well! I am a work in progress lol. I guess I had not tried the Kubuntu disk. SO...I tried it and it installed Kubuntu. So that is good and it'll just be a matter of time with more posts along this line to try and figure out Wine and Duel-booting etc. but looks good atm. Mucho thanks for all the input everones! If anyone now has any sage advice on how to install Win7 with Kubuntu on the box first then I would accept that link. :) :popcorn:

Let me explain why you should install windows first. When you install windows it assumes that the disk is empty, windows does NOT recognize ext3, ext4 not swap partitions, therefore it will whipe it all. If you do succeed to install it without taking it, the MBR won't recognize the existence of Kubuntu on the box and therefore will be a waste.

My recommendation is to find another W7 copy and install it using the license you paid for and following the steps I gave you before. I have made several installations and lots of dual boot, that way is the easiest.

If you have any other question, don't be afraid of asking, that's how we all learn. Good Luck.

---

### Post by Lighthugger on 2010-02-23
> **arashiko28 said:**
> Let me explain why you should install windows first. When you install windows it assumes that the disk is empty, windows does NOT recognize ext3, ext4 not swap partitions, therefore it will whipe it all. If you do succeed to install it without taking it, the MBR won't recognize the existence of Kubuntu on the box and therefore will be a waste.

My recommendation is to find another W7 copy and install it using the license you paid for and following the steps I gave you before. I have made several installations and lots of dual boot, that way is the easiest.

If you have any other question, don't be afraid of asking, that's how we all learn. Good Luck.


Ahh great! Yeah I am sure i will have many questions. I love taking on new things and Kubuntu seems pretty cool imo. I am looking forward to playing around with it more!

So, regards to my copy of Win7, I go to school for (well currently) Win Server 2k8 and as part of my lab fees we get copy rights on many different iso's and so my copy IS a registered valid true COPY of Win7 I paid for it wih my lab fees. We just go to the school website [URL="http://http://www.e-academy.com/"]http://www.e-academy.com/
[/URL] There should be no reason Kubuntu does not recognize the disk except it's still a GRUB issue? Where it's kicking in faster then my CD/DVD drive is, so therefore it will not boot from CD/DVD? Possible? If so how would I resolve this?

Ok I just re-read your post...busy here at work, I get what you are saying with the Win install but I still get the issue when I put the Win7 Disk in. Grub takes over and it's boot into Kubuntu.

I stand here correcting myself, I am running Ubuntu.

---

### Post by mechro on 2010-02-23
[QUOTE=Lighthugger]There should be no reason Kubuntu does not recognize the disk except it's still a GRUB issue? Where it's kicking in faster then my CD/DVD drive is, so therefore it will not boot from CD/DVD? Possible? If so how would I resolve this?[/QUOTE]

Booting your Windows disk has nothing to do with Kubuntu or Grub. It's a setting in the BIOS.

If you've set the BIOS to boot the Windows CD and it doesn't boot then you've either got a BIOS setting wrong, or you have a faulty disk, or perhaps the Windows disk is looking for something before it will boot.

---

### Post by Lighthugger on 2010-02-23
> **mechro said:**
> Booting your Windows disk has nothing to do with Kubuntu or Grub. It's a setting in the BIOS.

If you've set the BIOS to boot the Windows CD and it doesn't boot then you've either got a BIOS setting wrong, or you have a faulty disk, or perhaps the Windows disk is looking for something before it will boot.

Ok...so truuue, but my BIOS is set to boot first from CD/DVD. I'll have to go back and reverify, but at one point I know I set it that way...but either way I hit F11 at startup and set it to boot from CD/DVD and walla it boots to Ubuntu which is what is installed.

---

### Post by mechro on 2010-02-23
... so is it a faulty disc then? Do any of your CDs (Kubuntu?, Ubuntu?, Gparted?) boot?

---

### Post by robert shearer on 2010-02-23
> **mechro said:**
> Booting your Windows disk has nothing to do with Kubuntu or Grub. It's a setting in the BIOS.

If you've set the BIOS to boot the Windows CD and it doesn't boot then you've either got a BIOS setting wrong, or you have a faulty disk, or perhaps the Windows disk is looking for something before it will boot.

+1.  It is a faulty Win-7 disc for sure.

If the system boots from Ubuntu on cd but not Win-7 then we know there is nothing wrong with the 'first boot device' being the cd/dvd drive.

If the Win-7 disc is faulty and unable to boot then the bios will kick in the next boot device after a set time.
This is probably the hard disk which is why you get the Grub prompt.

Repeat. a faulty disc.
 Go try it on another machine and it won't boot on that either.
You need to obtain a working Legitimate win-7 disc before you try to install from it.

---

### Post by Lighthugger on 2010-02-23
> **robert shearer said:**
> +1.  It is a faulty Win-7 disc for sure.

If the system boots from Ubuntu on cd but not Win-7 then we know there is nothing wrong with the 'first boot device' being the cd/dvd drive.

If the Win-7 disc is faulty and unable to boot then the bios will kick in the next boot device after a set time.
This is probably the hard disk which is why you get the Grub prompt.

Repeat. a faulty disc.
 Go try it on another machine and it won't boot on that either.
You need to obtain a working Legitimate win-7 disc before you try to install from it.

Well here's the thing. I have a Win Serv 2k8 Disc I burned also and that won't boot up either, but my Ubuntu will all three burned on to the same exact media (not the same CD/DVD just a CD/DVD made by the same manufacturer).


OK what is the easiest way to just wipe my disk and restart (given the issues I am having)?


....ok so you guys rock!I dug around and found my Win 7 Ultimate disk I bought off New Egg and kicked it in...up it spun! :) I'll install that...(hopefully...I seem to remember it was a single install disk) and install Kubuntu !! :)

---

### Post by robert shearer on 2010-02-23
> **Lighthugger said:**
> Well here's the thing. I have a Win Serv 2k8 Disc I burned also and that won't boot up either, but my Ubuntu will all three burned on to the same exact media (not the same CD/DVD just a CD/DVD made by the same manufacturer).

....ok so you guys rock!I dug around and found my Win 7 Ultimate disk I bought off New Egg and kicked it in...up it spun! :) I'll install that...(hopefully...I seem to remember it was a single install disk) and install Kubuntu !! :)

There you go, as we have said the problem is with your 'burnt' windows discs.
These have not been burnt correctly and your system cannot recognise them as valid media so defaults to the second boot device.
Proof is that a correctly burnt Kubuntu disc boots and your Official Windows disc boots.

Happy installs and remember Occam now and then.

---

### Post by arashiko28 on 2010-02-24
Glad to see you could solve your problem, now it's only a matter of time before you absolutely convert into the free as beer world of open sources and Linux :D

---

### Post by Lighthugger on 2010-02-24
> **arashiko28 said:**
> [QUOTE]
2. When you change disks, go for live session, that way you can use internet if any doubt comes while installing.
On the top of the installation window you'll see a bar showing your disk and it's partitions, that will give you the area you already designated for Windows. 

OK since I now have my Win7 installed I want to now duel boot Kubuntu. I have that burned to a disc now and I am going back through our thread here to figure that out. When you say "go for live session" what do you mean?

---

### Post by Temposs on 2010-02-24
Any Ubuntu install CD is called a LiveCD. A LiveCD means you can run Kubuntu directly from the CD without installing it on your hard drive. This is what arashiko28 refers to as a "live session".

When you boot the Kubuntu CD, it should come up with a menu, the first option being something like, "Try without installing". Choosing that will boot into Kubuntu straight from the CD. You can use any of the Kubuntu programs from there and connect to the internet, all without installing. This is good to have around in case you can't boot your computer for some reason. It's also good for using the Internet before/during your install to make sure you're doing it right. And lastly, it's good for testing Kubuntu to make sure it works with your computer's hardware, before you install.

There should also be a button when you're running this live session which says "Install Kubuntu" or something. So, you can initiate the install at that point.

---

### Post by Lighthugger on 2010-02-24
> **Temposs said:**
> Any Ubuntu install CD is called a LiveCD. A LiveCD means you can run Kubuntu directly from the CD without installing it on your hard drive. This is what arashiko28 refers to as a "live session".

When you boot the Kubuntu CD, it should come up with a menu, the first option being something like, "Try without installing". Choosing that will boot into Kubuntu straight from the CD. You can use any of the Kubuntu programs from there and connect to the internet, all without installing. This is good to have around in case you can't boot your computer for some reason. It's also good for using the Internet before/during your install to make sure you're doing it right. And lastly, it's good for testing Kubuntu to make sure it works with your computer's hardware, before you install.

There should also be a button when you're running this live session which says "Install Kubuntu" or something. So, you can initiate the install at that point.


kk thanks I opened the Wubi? but had no disk in at the time and the Installer window would not go away so I had to reboot. So I should be able to run the Wubi installer with the disc in and it will run right off the disc?

Thanks all for the helps!

---

### Post by Temposs on 2010-02-24
Do NOT use Wubi. Definitely not...

Boot the computer with the CD in it, and it will load the correct way.

---

### Post by Lighthugger on 2010-02-24
> **Temposs said:**
> Do NOT use Wubi. Definitely not...

Boot the computer with the CD in it, and it will load the correct way.

Roger :) thanks :)

---

### Post by Lighthugger on 2010-03-09
Ok all thanks for the help I took a stab at this again  last weekend and I have Win7/Mint up and running now :) Thanks for all the help

---

