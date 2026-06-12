---
title: "Various types of media not being detected"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by techno-mole on 2009-11-02
Im not sure whats going on here, but I'll try to explain.

Im running 64bit karmic, which I first installed as a beta and I have since kept up with updates, but I don't think this has anything to do with it ?

any way it seems that the system isn't detecting various types of media, for example I have an akasa card reader, its a built in one (I installed it myself) fits into a spare floppy bay, it reads various types of card, sd,compact flash etc and it has a usb port as well, but when I put the compact flash card from my digital slr camera into it the system doesn't seem to know anything has been plugged in, I have checked to make sure an app is selected to open it should the system see it, it also doesnt pick up any other type of card.

this might point at there being an issue with the reader, but my dvd drive doesnt seem to work  either, that is to say that if i put a disc in, dvd film for example or any other type of dvd, blank,game disc etc the drive spins up but doesnt actually mount the disc, the same with the sd cards, compact flash cards etc.

I also have a cd rw drive and the same goes for this drive, i can put a disc in and it will spin up, but the system doesnt mount the disc.

the system does pick up my mp3 player, which i connect via a usb lead, however another curious thing i have noticed is that i normally charge the mp3 player using the usb lead, but whilst it will connect and i can transfer files it no longer charges ? no idea why not.

now if i plug in my compact flash card, or sd card etc or if i use a dvd disc etc if i leave the card or disc in the respect drive and log out and in again the system will mount it, this is the only way i have been able to mount the various media, music discs are the same, they dont get mounted unless i leave the disc in the drive and log out and back in again.

as i mentioned im running 64bit karmic, but my wife is also using karmic, but she uses the 32 bit version and all the various media gets mounted as the system picks them up almost straight away, she has a usb card reader.

I have looked around but cant find anything thats similar to my issue, so has anyone had a similar issue ?

cheers in advance for any help.

---

### Post by marenum on 2009-11-02
I've had a similar problem with Karmic. It doesn't always read my cruzer micro thumb drives, my sd/mmc USB converter, or my ipod. At fisrt I thought the issue was with my AUX USB ports, but I tried running my keyboard through them and they worked just fine. Even more interesting, is that I tried rebooting with the drives already in the USB ports, and it read them, but when I removed the devices and then plugged them back in they again would not read. 

I should also note that, although I am unable to read/write these devices, they do show up under Disk Utility. Hope this is in some way helpful.

---

### Post by delysid on 2009-11-03
I'm having this problem as well on both 32 and 64-bit versions.
It occurs more on the 32-bit version I installed on an HP Pavillion laptop.

The laptop uses a 500GB Maxtor OneTouch usb HDD.  If the hard drive does mount, clicking the icon that appears on the desktop causes the system to lock up.  :(

The only option after this is to log out and log back in.

I hope they fix this soon.
It's my only real complaint about Karmic.

---

### Post by marenum on 2009-11-04
Hey guys, I've noticed that my flash drives are usually picked up after I unplug then replug them. I know it's not the best fix but it's a little easier than logging out. 

Not sure if this will work for you, or if it works every time, but I guess it's something.

---

### Post by delysid on 2009-11-04
> **delysid said:**
> I'm having this problem as well on both 32 and 64-bit versions.
It occurs more on the 32-bit version I installed on an HP Pavillion laptop.

The laptop uses a 500GB Maxtor OneTouch usb HDD.  If the hard drive does mount, clicking the icon that appears on the desktop causes the system to lock up.  :(

The only option after this is to log out and log back in.

I hope they fix this soon.
It's my only real complaint about Karmic.


Oh, I should add that of the device is plugged in,
logging out/logging back in will cause the device to be recognised.

---

### Post by nhasian on 2009-11-04
after you plug something in run these commands from a terminal to see if they are read and available:

```
dmesg | tail
```

```
lsusb
```

```
sudo fdisk -l
```

perhaps even though your memory card is seen properly, it is not being auto-mounted?

---

