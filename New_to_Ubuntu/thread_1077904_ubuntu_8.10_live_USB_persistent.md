---
title: "ubuntu 8.10 live USB persistent"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by commander56 on 2009-02-22
Dear Ubuntu forum,

I have been up and about searching for a pertinent answer to my question. I really want - from the bottom of my heart - to make a transition from windows/leopard to ubuntu, but unfortunately none of the info available is really making it easy for me!
My problem is that I am trying to make a 8.10 live persistent usb pen drive work. I have tried the pendrivelinux.com method ( [http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/) ) to no avail! (during DOS install in windows xp it keeps giving me data errors - total 60 and when i boot it loads the select screen, every time when i press ENTER it just resets the counter!). Then I tried 2 of the methods described here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) still to no avail!
All cases I was using 2 different usb drives formatted FAT32 - Kingston and Corsair - on 3 different computers - MSI Wind U100, 2008 pc and Dell 1330 laptop.
Please if there is anybody out there that can point me in the right direction i would be awfully grateful! 
I really want to make this big step towards open source OSs' and software but I really need help!

P.S. Do not shoot me down for my lack of linux knowledge, I am new and I am trying to learn; i tried searching but here was no coherent method of doing this that i could find!

Thank you in advance!

---

### Post by 5BallJuggler on 2009-02-22
what size is your pendrive?
do you have ubuntu installed anywhere?
do you have a liveCD of ubuntu8.10?

[http://ubuntuforums.org/showthread.php?t=1022708](http://ubuntuforums.org/showthread.php?t=1022708)

have a read of the above thread, it may be of some help

---

### Post by commander56 on 2009-02-22
> **5BallJuggler said:**
> what size is your pendrive?
do you have ubuntu installed anywhere?
do you have a liveCD of ubuntu8.10?

thank you for your reply!

a.my pendrives are: .

1. Kingston DT mini Slim 2GB
2. Corsair Survivor 8GB

b.I just have the 8.10 image from this link [http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-desktop-i386.iso](http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-desktop-i386.iso) 

c. since my main pc is a MSI WIND U100 (which does not have a CDROM or any kind of optical drive) I have tried in the past working with LiveCDs created with unetbootin (8.04 and 8.10) on USB drives (my current ones - see <a.>).

---

### Post by 5BallJuggler on 2009-02-22
You will have more luck with the corsair, apart from that i'm not going to be much help, ubuntu8.10 has a function to make a USB startup disk, but I need to load from a CD or have it installed in the first place to make it work.
When I was first looking at this a friend of mine recommended unetbootin, so there may be some mileage in that

Sorry I can't be anymore help.

---

### Post by commander56 on 2009-02-22
> **5BallJuggler said:**
> You will have more luck with the corsair, apart from that i'm not going to be much help, ubuntu8.10 has a function to make a USB startup disk, but I need to load from a CD or have it installed in the first place to make it work.
When I was first looking at this a friend of mine recommended unetbootin, so there may be some mileage in that

Sorry I can't be anymore help.

unetbootin is a great tool but it works just to copy the live cd onto the USB drive as far as I know. 
It really seems weird to me that it is so simple to make a live USB drive but just to save your settings you have to go these ridiculous lengths.
5BallJuggler, thank you for your help so far! I hope more people will try to lend a helping hand to this confused old platypus.

---

### Post by commander56 on 2009-02-23
Anyone, please? There is not one person that can help me with this?

---

### Post by psoplayer on 2009-02-23
The built in USB tool in the 8.10 release has the option to reserve space for the user's documents. I haven't actually tried it with this option so I don't know if it allows for the installation of new programs (what I think you want) or if it still runs off ram and just mounts a part of the usb drive as the home folder (just a place to save a few files).

---

### Post by Einar Schlereth on 2009-02-25
> **commander56 said:**
> Anyone, please? There is not one person that can help me with this?

For days I'm also looking for help with this (not exactly yours) problem to make a live USB startup disk. I find plenty complaints and nothing that is really helpful. I have a 1 GiG Sony Memory Stick and everything works fine. Successfully finished and Now you can start up with your USA. A lie. Nothing happens. It's attempting to boot .... infinitly.
And as I can see the complaints start right with the release of 8.10 and nothing happens. REally strange.
Einar

---

### Post by bobmatino17 on 2009-02-25
unetbootin can be used to make a cd like flash drive. if you dont want that, boot of a live cd and install to your flash drive (the 8gb one perferably.)

---

### Post by pme 72 on 2009-02-25
I have made successful USB drive persistent installs onto 2GB, 4GB and 8GB flash drives. I was able to download updates, write and save Open Office documents and save pictures and videos to the USB drives. I used an 8.10 Live CD to make the drives. I do not know how you would do it without a CD drive though.

---

### Post by Amenhoteph on 2009-02-26
Have you tried a different distro?

I tried several different variations of USB boots before I found one that worked consistently.  #!CrunchBang Linux worked for me out of the gate, and eventually led me here because it is an Ubuntu based release.

Follow the steps here and see if this gets you up an running:

[[COLOR="Blue"]_Install CrunchBang to USB_[/COLOR]]("http://www.pendrivelinux.com/crunchbang-linux-flash-drive-install-windows/")

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by InvisibleMan on 2009-02-26
I've tried this ([http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/)), I've tried the installer on the 8.10 live CD and I've tried unetbootin. I've tried a 4 GB drive, a 2 GB drive and an 8 GB drive. I must be missing something somewhere.

The latest error message is "SYSLINUX 3.63 Debian -2008-07-15 CBIOS Copyright (C) 1994-2008 H. Peter Anvin. Missing parameter in configuration file. Unknown keyword in configuration file."

Any thoughts, anyone?

---

### Post by randalph on 2009-02-26
Hey I finally got persistence to work. You just need to create a large casper file named "casper-rw" in the root of the usb disk.
you can either download a pregenerated one:
[http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/)
or make your own:
[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)
note the 4GB fat32 limit warning - you won't have a single 16GB persistent system with a fat32 formatted stick.

I verified persistence w/ a text file on my desktop and another in /. I also noticed there are some casper packages in synaptic that are not installed by default. Maybe they're not marked as dependencies for usb startup disk creator but are necessary for the persistence feature. I would test this out myself but I have a new persistent system to play with.

If you try any of this please post your positive/negative results in this forum.

---

### Post by randalph on 2009-03-10
anyone?

---

### Post by tea for one on 2009-03-11
The USB creator within Ubuntu 8.10 functions perfectly and gives you the option of creating a persistent area for saving files.

I have used it successfully on a 2GB Kingston DataTraveler and a 4GB Sandisk Cruzer.

You can either create the "Live USB" direct from a CD and also from an iso image stored on your hard drive.

The following article may also be helpful:-

[http://www.tuxradar.com/content/how-install-linux-usb-flash-drive](http://www.tuxradar.com/content/how-install-linux-usb-flash-drive)

Also, it is quite an interesting experiment to create your own distro by starting with a minimal installation, adding chosen software, remastering to produce an ISO and then creating a mini "ubuntu-like" distro with persistence on a USB device. (using USB creator in 8.10)

So far, my attempt boots slowly and there are obviously some gremlins somewhere but the experiment is enjoyable on a rainy weekend.

---

### Post by novafluxx on 2009-03-11
I was never able to get it to work either. It wouldn't even boot, let alone be persistent!

I tried using the creater included with 8.10 in an installation in virtualbox, the software ran flaslessly, however it wouldn't boot when I tested it. 

Next I tried booting 8.10 liveCD and created it, same results, eventually I gave up and installed Ubuntu on my laptop and then on my desktop using Wubi!

I was using a verbatim 8GB usb flash drive

---

### Post by Brinstar on 2009-03-11
i have had success using unetbootin for creating the liveusb, but persistent mode didn't seem to work with other distros (using the casper-rw file and appending 'persistent' into the syslinux.cfg). maybe something else is required?

liveusb definitely works with unetbootin, i have tried it on several pcs.

i tried the ubuntu usb creator, but had problems with it.

---

### Post by nothingspecial on 2009-03-11
I don`t install any distro with a cd since I found unetbootin. It`s so much easier. Just select your distro and tell it where your usb drive is and it downloads the iso and makes a live usb for you.

I have successfully installed Ubuntu 7.10, 8.04, 8.10, Arch, Fedora, Suze and Puppy with it.

[[COLOR="Magenta"]Here`s the link[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by randalph on 2009-03-12
tea for one: It most certainly does not function perfectly. it may work for you but there are several people reporting persistence doesn't work, and I verified on two 8.10 and one 9.04 systems. This could be because of different packages installed such as casper packages which are not something that the usb creator package depends on. If you want to try to help this thread rather than asserting that it works, first try to replicate the problem by removing all your casper packages or preferably find a bone stock Ubuntu (not Ku or Xu) install and making a new stick.

nova: Yeah if it doesn't boot you have other issues, not (yet) persistence. can't help you in this thread.

brin: What were the problems you had with ubuntu usb creator?

nothingspecial: What? this is about persistence not just straight up installing.

I reiterate: did anyone failing on just persistence, using the Ubuntu USB Startup Disk Creator app (preferably someone that opened the thread) try my instructions above and succeed or fail?

---

### Post by nothingspecial on 2009-03-12
> **randalph said:**
> 

nothingspecial: What? this is about persistence not just straight up installing.


apologies, skim read the thread. Hope you get it sorted.

---

### Post by nothingspecial on 2009-03-12
I don`t want to waste your time again, but I seem to remember being able to do this persistence thing with puppy.

From memory, I think it even asks you when you log out/ shut down etc.

Of course, being me, my memory might fail, but if you can`t get it to work with ubuntu then maybe it`s worth a go.

---

