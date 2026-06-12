---
title: "Ubuntu 9.04 Live"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Trentor on 2009-05-22
I have been trying to get Ubuntu 9.04 on my usb thumb drive I just bought.  

I used this post to guide me in the process:  [http://ubuntuforums.org/showthread.php?t=873743]("http://ubuntuforums.org/showthread.php?t=873743")

I tried first using the linux ubuntu installer, it went into not responding, waited a long time and then had to force quit it.  The second time I tried the live usb maker in ubuntu it seemed to work, I had it do persistent home directory, but whenever I tried booting to the usb it recognized a linux iso and had a screen that said "boot: ", was unable to do anything.

At this point I tried using the windows client that normally installs fedora and it worked, however now the partitions on my flash drive are completly messed up and I have no idea how to fix the drive.

When I boot from the drive it works, however it shows three partitions:

Note: Size of usb drive is 16gb, some space is missing and no clue where it is.

**UBUNTU** (799mb, and what I installed it to in Windows live usb maker, this is what it is booting from)

**Ubuntu 9.04 i86** (same size, same files, have no clue WHY it is there)

**home-rw** (13.3gb size, only a lost-found folder that cannot be accessed)


I tried using gparted to see if I could fix the drive but it does not detect the usb drive.

So a few questions:

Is there a tool that I can download that will auto-detect usb 2.0 devices such as thumb drives and completely reset (reformat and repartition) them?

The live partition works, however I would like more space towards my UBUNTU drive, because I only have about 99 mb to install stuff and 13.3gb on my home-rw drive, i want to be able to install software there.

Thanks, I really would like to be able to completely reset this flash drive, without saying some random stuff to get the place where I bought it from to give me a new one :D

Link to previous thread: [http://ubuntuforums.org/showthread.php?t=873743](http://ubuntuforums.org/showthread.php?t=873743)
Link to windows installer: [https://fedorahosted.org/releases/l/i/liveusb-creator/liveusb-creator-2.7.zip](https://fedorahosted.org/releases/l/i/liveusb-creator/liveusb-creator-2.7.zip)
Link to linux installer: [http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

Trent

---

### Post by Trentor on 2009-05-23
Update: Ok, so after some messing around with the partitions in windows it found an unknown partition, I deleted it and apparently had to reformat the flash drive two times and it finally got back to normal.

Tried using the windows fedora installer with the ubuntu iso and put aside 2gb of persistent space.  Now heres what it looks like when I boot up.

The Filesystem said it has 977.2mb of free space, and I have a drive named UBUNTU that has 14.4gb of free space, it contains the wubi.exe and such.

I tried installing a program, tried installing abiword, it went into the filesystem and a little bit of the 977.2mb went towards abi word, but when I restarted the laptop abiword was not installed.

How can I get the Filesystem to have a larger size and retain programs?

Trent

---

### Post by superprash2003 on 2009-05-23
you should try the tutorials at pendrivelinux.com they have step by step tutorials , you can never go wrong

---

### Post by Trentor on 2009-05-23
Ok, thanks for the information, I have acctually taken a look at that site before, and what they offer seems to be a lot simpler than what I was trying to do.

Here is another question, so I have done exactly what the website ([http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)) says.  The default size for the casper-rw partition is 1gb they say, which makes sense given what I was trying to do earlier (900ish mb free)

The websites offers other sizes up to 4gb, but how can I make the casper-rw partition larger than 4gb, can I make it around 10gb? or even 16gb considering I have a flashdrive that is 16gb.

Trent

---

### Post by Trentor on 2009-05-23
Update:  The thumb drive will now boot and an option to start ubuntu persistantly will show up.  I tried booting like so and tried installing a program (tried abiword) and the installation finished, the program ran fine, but when I restarted it was not there.

Maybe I am not understanding what is going on, but as far as I can tell there are two systems:

* filesystem
* and my drive name - the amount of "persistant" space I have, currently being around 13.4 gb

When I am trying to install programs am I installing them in the ram?  Is the filesystem in the ram at this point?

**Edit:** Ok, I guess what I am trying to ask is, it is indeed possible to boot from usb and have the entire drive (/ and everything past it, the entire ubuntu os) be persistant? be the size of my entire usb drive?
Because if this happens then I assume any changes to the operating system (changing the desktop background, editing text files, installing and removing programs, saving music, photos in home) should stay after you reboot.

Trent

---

