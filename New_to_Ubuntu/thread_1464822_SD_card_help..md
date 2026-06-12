---
title: "SD card help."
date: 2010-04-28
forum: New to Ubuntu
---

### Post by AbbyRose on 2010-04-28
First, I just downloaded ubuntu so I'm still getting the hang of things but I have a port on my computer to put in the SD card. I have photos and such that I want to transfer from my SD. I can't figure out how to have it be read and be able to be viewed/edited. When I plugged in my thumb drive it loaded right away.

---

### Post by ubunterooster on 2010-04-28
Go to: places>computer. Is it listed there?

---

### Post by AbbyRose on 2010-04-28
No this is why I'm having trouble. I have my CD-RW/DVD drive, USB drive and filesystem.

---

### Post by ubunterooster on 2010-04-28
Can you plug the camera to the computer via usb while the card is in the camera?

Can't remember commands to go through now for probing USB ports; too tired I guess. Hopefully you have it figured out by the time I manage to get back on.

---

### Post by bukwirm on 2010-04-28
What kind of camera do you have? If the camera has a USB interface, it might show up as a USB mass storage device if you plug it in with the USB cable.

Alternatively, plug the SD card in and type "dmesg | tail" into a terminal and look for information about SD cards.

---

### Post by AbbyRose on 2010-04-29
Well the SD card I was using is actually my phone's... sadly it has more GB than my camera's. I plugged in my camera with it's card and plugged the cord it. It registered and everything. I haven't tried with my phone's SD. I know they have the mirco SD but I have the converter that changes it to SD. I'm going to try to use my phone's card in the camera shortly. Well never mind I just tried and my camera couldn't read the card. 
bukwirm I'll try that and see what goes on. I'm currently in windows =/ I might have to reinstall ubuntu anyways so fixing it won't be much of a help until everything is set up. ((it downloaded ubuntu into windows and I didn't want it that way so I have to change it.))

---

### Post by JimTaverna on 2010-04-29
First Remove all other external drives then enter this in terminal. 

sudo fdisk -l

There should be at least one block of data, "Disk /dev/sda"

look to see if there is another block, something like "Disk /dev/sdb" if you're lucky

report back what you see.

---

### Post by bukwirm on 2010-04-30
An SD card will probably show up as something like /dev/mmcblk*p*, where the * are numbers - if you insert the SD card into a card reader, at least.

---

### Post by uBuddhu on 2010-08-17
I was having this problem, too. I was about to post, but this post led me  to wonder about an error when I clicked on Places->Computer (Nautilus  cannot handle computer: Locations)

The recommended course of action for that was:

> sudo mv /usr/local /usr/local.old
> sudo mkdir /usr/local
Reboot.

Lo and behold, after the reboot, my SD was appearing again and my new  MP3 player was also. Hope this fixes someone else's problems, too.

---

