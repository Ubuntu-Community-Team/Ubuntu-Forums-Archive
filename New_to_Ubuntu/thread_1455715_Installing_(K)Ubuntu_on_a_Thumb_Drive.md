---
title: "Installing (K)Ubuntu on a Thumb Drive"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-04-16
Hi guys.
For those of you who might not recognize me (I doubt anyone would), I'm DM. It's been about a year since I've run Ubuntu; about two since I already ran a version that was supported (I ran 6.06 long after the support ran out, because it was the only thing my computer could run).
I had switch over to PuppyLinux on a LiveUSB because my Ubuntu hard drive would've recognize in the computer. However, we've recently began running wireless and I've been forced onto Windows because Puppy has issues with the card.
It will recognize the card (Ndiswrapper has it as p54usb, but it's actually a Linksys card), it will recognize the network. It takes *forever* to find an IP address, and when I go to click on Opera or Firefox or whatever I'm in the mood to use at the moment, I get "network error."
It's similar to an issue we've had on Windows, but the difference is Windows has it on the back USB ports only, whereas Puppy has it in all of them. 

So the first thing is I want to know how exactly I would go about installing Ubuntu on my thumb drive (PNY Attache 8gb if it matters). I'm thinking about giving Kubuntu or perhaps even Xubuntu a chance. Kubuntu because I'm a huge fan of KDE, Xubuntu because I fell flat out in love with Xfce while running it on Puppy. 
Is it as easy as it is on Puppy? Where you go into programs and click on a LiveUSB creator? And is it the same on Kubuntu and Xubuntu?
I'll probably know whether the wireless card works or not as soon as I get on the CD, so if it works out all I need to do is use the info someone posts here and get going.
(+/- backing up my stuff on Puppy. Yeah, that might help...)
Thanks for the help. :)

---

### Post by Jon Monreal on 2010-04-16
If you want a LiveUSB in the sense of a Ubuntu LiveCD (where the installation is not persistent so your files and changes are not saved), then you can just grab unetbootin from Synaptic and work from there.

If you want a persistent installation, take a look at [this wiki page]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").

---

### Post by DM was on fire! on 2010-04-16
Persistent is what I'm wanting.
I'm wanting it to act like Puppy does.

Does this count for 9.10, or is it 8.04 only? 
I'm really curious to try out Lucid, but I think I'll hold off until it releases.

---

### Post by spydeyrch on 2010-04-16
If you want to create a persistent USB drive, read [this article/how-to]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/") at howtogeek.com Awesome article.

You can also use UNetBootin for a non-persistent usb. Just a side note, if you go with a persistent usb, the max amount of space that you can dedicate to your persistent install is 4GB of your 8GB. So My recommendation would be to format your 8GB usb into 2 partitions: 4GB each. Make sure both of them are FAT32. Install your flavor of *buntu to one of the partitions and then use the second one as a shared drive for files that need to be transferred between your persistent drive and your windows drive.

Just a thought. :lolflag:

-Spydey

---

### Post by Jon Monreal on 2010-04-16
I'm not sure if the Live USB Creator (GUI-based) works with 9.10, but I imagine it probably does. I would give that a try as it's probably the easiest option. If it doesn't work, we can always try something else.

About using Lucid: it might be a good idea to wait until Lucid is out and see if that works right off that bat if you plan on using it. That way you don't have to risk messing anything up with an upgrade installation. If you're not too worried about having the latest and greatest, you might consider waiting until a while after release so that everything is patched up before you jump in.

---

### Post by spydeyrch on 2010-04-16
The built-in usb creator is a great option .... if you already have *buntu installed. But I believe that you are running from a windows machine, right? So then that link that I gave previously in my other post will be the way that you will want to go. It is a windows native program and will allow you to create a persistent live *buntu usb drive.

One thing really quickly about my previous recommendation about setting the two partitions. Only do it once you are sure that everything is going to work.

Just install the persistent *buntu on the USB drive and make sure that it works with your computer's hardware. Give it a good test drive and then if you want to do what I recommended before, that is up to you. :)

Also I would recommend either 9.04 or 9.10. I make usb persistent drives like twice a week for friends, family, myself and those are the two that I constantly use. :KS

-Spydey

---

### Post by DM was on fire! on 2010-04-16
I was planning on waiting until Lucid came out anyway before I gave it a try. XD

I'm on Windows right now. I was hoping it would be similar to Puppy, in that all I would have to go is go to the USB creator in the distro and set it up that way. I guess I got spoiled with my pet. 

Spyder, I currently have only 1gb set up for Puppy and I never run out of room; unless I go on an image saving or music downloading binge (and even then I've still got about 100mb left). 

I'm downloading 9.10 as we speak (then I realised I wanted Kubuntu and facepalmed. Oh well. I can install it via Synaptic). Thanks for the help!
I'll end up trying it on the LiveCD and make sure the wireless runs before I mess with my current setup.

Albeit off-topic, anyone have any experience with a Linksys Wireless G WUSB54GP card? First edition software?

---

### Post by spydeyrch on 2010-04-16
Very cool that you are only using 1GB of space and that you have not run out of room.

So do you have a dual boot setup then? windows and Puppy?

---

### Post by DM was on fire! on 2010-04-16
I guess you can call it that.
I have Puppy on my 8gb thumb drive, and then Windows is on a 250gb hard drive.
I'd have my Ubuntu hard drive in here, but for some reason, this computer wouldn't recognize it. I heard about Puppy from these forums actually, and I decided to give it a shot. <33

---

### Post by spydeyrch on 2010-04-16
So you have puppy on an 8GB usb flash drive and it only takes up 1GB? What about those other 7 GBs? Are you able to use them in puppy/windows?

When you say that it only takes up 1GB, is that just the os or is that the os and everything that you have saved in puppy too (i.e. apps, photos, music, etc.)?

Just curious because that is super small and I would love to use something like that for smaller flash drives that I have. 

-Spydey

---

### Post by DM was on fire! on 2010-04-16
What you do is the first time you turn Puppy off or reboot it, you're given an option to create a savefile (similar to the persistent version of Ubuntu you're talking about). Your savefile can be any size, and can be made larger later on.
The 1gb is every program, image, song and anything else you have saved on there. I don't remember if it includes or excludes the programs that already come with Puppy by default (which is a lot).
The other files for the system take up about 100mb or so on the flash drive (the .iso for Puppy is all of 105mbs). 
The remaining 7gb, I use for storage and transferring things onto Puppy. You can access the files on there straight from Puppy, by mounting sdb1 from the Desktop. Even the other files on there, you can still use Puppy as a normal thumb drive.

I've got a lot of programs on Puppy; aMSN and a ton of custom emotes, Xfce...I considered downloading KDE but I didn't feel up to it.

[http://www.puppylinux.org](http://www.puppylinux.org)
[http://www.puppylinux.com](http://www.puppylinux.com)

It's a really great operating system. But if you're not keen on ROX-Filer, I definitely suggest hunting down a .pet for Xfce or your own environment of choice.

---

### Post by Jon Monreal on 2010-04-16
If you want something really small to fit on a flash drive, Puppy is great. You can save your state to either the flash drive itself or a hard drive (although it would be best to use a separate partition for the file system and the files) It also offers write-caching so it makes less writes to the drive (therefore making the drive last longer).

With the default, you'll come in well short of 1 GB.

---

### Post by DM was on fire! on 2010-04-16
Haha, oops. I just went and took the .iso and installed it with the Universal Installer. No partitions or anything.
For a moment, I *felt* like I was smrt @ linooks.

Thirty-six minutes to go until my .iso is downloaded! Whoo.
...I hate our internet.

---

### Post by spydeyrch on 2010-04-16
Interesting. I wasn't ware that puppy was so small as an .iso. I will have to take a look at it and possibly use one of my really old 256MB flash drives that I have.  :P

Interesting way of mounting the remaining space on the flash drive. Thanks for the tip.

I just looking at the puppy linux site. Looks very low key but with quite a bit of functionality. Almost reminds me a little of knoppix but smaller.

So are you planning on going with Xubuntu 9.10?  :guitar:

---

