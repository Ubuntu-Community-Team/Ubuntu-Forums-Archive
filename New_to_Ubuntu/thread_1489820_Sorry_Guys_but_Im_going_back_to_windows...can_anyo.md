---
title: "Sorry Guys but Im going back to windows...can anyone show me the way?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by robbiegoodfellow on 2010-05-21
Hi
its all my fault for fiddling I know, but I wiped my eepc and the only way I could get it to work again was with ubuntu.  Its been great and I would love to dual boot both ubuntu and xp.  However, most of the programmes I need i.e. pc suite for my samsung phone, itunes for my mac formatted ipod and flash mx just dont work on linux or they cant do what I need.  The thing is Im stuck now with no cd drive and only a 2gb flash card that Ive tried to install windows onto it using unetbootin, alas though It doesnt work.  I have a windows xp iso that my mate gave to me and i was wondering if there was a way to go back.  Ive had a look around but Im a newbie and it all seems a bit complicated for me.

cheers
Robbie

PS..I promise to dual boot both as Ive got an idea to write an app like the old ispy books with big chief ispy.

---

### Post by -humanaut- on 2010-05-21
Get a windows disk and install. Make sure you have the C.O.A key that matches your bios or the one that came with the windows disk.

---

### Post by robbiegoodfellow on 2010-05-21
would do but I havent a cd/dvd drive to put it in...all i have is a flash card:(

---

### Post by Arla on 2010-05-21
I'm not sure if you can install windows without a CD drive, perhaps through a network (maybe) or buy an external DVD drive, not sure I know of any other way.

[This site]("http://www.pctipsbox.com/installing-windows-xp-using-a-usb-flash-drive") appears to have instructions how to do it, I would assume you do need another computer with a CD drive though to do the setup.

---

### Post by dmorri18 on 2010-05-21
This may help:

[http://www.pctipsbox.com/installing-windows-xp-using-a-usb-flash-drive/](http://www.pctipsbox.com/installing-windows-xp-using-a-usb-flash-drive/)

Dave

Oopsie...I see Arla posted the same site...sorry...

---

### Post by robbiegoodfellow on 2010-05-21
cheers guys but been to that website already, you need to have windows already installed to make it work.  Tried to boot it from sun virtual box but couldnt get it to work...To be honest think Im daft!!!!

---

### Post by -humanaut- on 2010-05-21
Is there a "recovery" partition on your computer from the OEM?

---

### Post by halitech on 2010-05-21
everything I'm finding searching google says the same, you need to do certain things on a windows based computer in order to boot from a usb stick. I'm not sure if you could make a bootable usb drive with ubuntu and boot into a terminal only mode and install over a network or not. You certainly can't boot from a floppy drive.

---

### Post by jerome1232 on 2010-05-21
Install Windows to a virtual machine, do the things you need to do there to get that usb stick bootable.

Oracles VirtualBox 3.2 should work for ya [http://www.virtualbox.org/](http://www.virtualbox.org/)

(seems weird saying oracle instead of sun)

---

### Post by halitech on 2010-05-21
> **jerome1232 said:**
> Install Windows to a virtual machine, do the things you need to do there to get that usb stick bootable.

Oracles VirtualBox 3.2 should work for ya [http://www.virtualbox.org/](http://www.virtualbox.org/)

(seems weird saying oracle instead of sun)

would a 2gig flash drive be big enough to have an ubuntu install and a windows xp install in virtual box?

---

### Post by LowSky on 2010-05-21
Do you have $35?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827135206](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135206)

---

### Post by jakeeee on 2010-05-21
I know theres a tool to get windows 7 on a bootable falsh drive.
You just need a windows iso or a windows install disk..
Maybe it'll work with xp?

You need a windows machine to use the tool though..
Idk but heres the link..
Hope I helped :)

**[http://images2.store.microsoft.com/prod/clustera/framework/w7udt/1.0/en-us/Windows7-USB-DVD-tool.exe](http://images2.store.microsoft.com/prod/clustera/framework/w7udt/1.0/en-us/Windows7-USB-DVD-tool.exe)**

---

### Post by jerome1232 on 2010-05-21
> **halitech said:**
> would a 2gig flash drive be big enough to have an ubuntu install and a windows xp install in virtual box?

I was under the impression the OP has Ubuntu currently installed to the computer with a Hard Disk Drive that would presumably have much more than 2 GB's of free space. If I assumed wrong that's my bad.

If I was correct in my assumption then the OP should be able to install VirtualBox inside the Ubuntu install, install Windows into the VM via a torrented iso, make the flash drive into a bootable Windows install disk. Install Windows into it's own partition keeping Ubuntu. Boot into Windows and from within Windows the OP can erase the flash drive, download unetbootin, put a live desktop cd on the flash drive and restore grub so that the op can have a working Ubuntu and Windows side by side.


edited: I forgot like a whole sentence. :)

---

### Post by KdotJ on 2010-05-21
I think getting an external CD/DVD drive is your best bet really, or even better buying an actual internal one and fitting it. Because even if you get to install windows on your machine through another method, surely you're going to need a CD/DVD drive at some point in the future...

---

### Post by droadtrip on 2010-05-21
Get a External USB CD/DVD for your netbook. If you can'tYoafford one, then do you know any Tech friends who can loan you one? From there, run your Windows restore discs and you follow the on screen instructions. If you did not get a Restore disc for your netbook then your screwed. Well, not really because Linux is a wonderful thing. They said all around the world that a netbook is supposed to be a 2nd pc to your main pc anyway. Take it from me - I owned a MSI Wind Netbook for a few months but had to restore WinXP to it and sell it because of some hardware buttons failing on me. After that I said to heckfire with netbooks.

---

### Post by slibuntu on 2010-05-21
Ok, so the options here are;

Get an external CD/DVD drive

or

Create a Windows XP virtual machine and use it to prep a USB stick so Windows can be installed from it. 


One's free but is a bit of hassle, the other costs money, but is simple.

---

### Post by ron999 on 2010-05-21
But if you go to the trouble to create Windows XP in a virtual machine then you can leave your Ubuntu intact and just use Windows in virtual machine for those particular programs that won't run in Ubuntu.

---

### Post by robbiegoodfellow on 2010-05-23
Cheers guys.  Have installed Virtual machine and installed windows to the usb with win to flash..  Tried to boot it up using removable disc option in the bios, but when it boots it just says please insert bootable disc blah blah blah.   Think Im just gonna just have to stay on linux... To be honest the only thing Im missing is flash mx and the new doctor who games!!!!

Robbie

---

