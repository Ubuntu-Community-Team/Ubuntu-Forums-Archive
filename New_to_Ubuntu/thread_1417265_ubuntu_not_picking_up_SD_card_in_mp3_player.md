---
title: "ubuntu not picking up SD card in mp3 player?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by ave2 on 2010-02-27
I have an mp3 player that has built in storage and can take an additional micro SD card. in ubuntu 9.10 I cant access the micro sd, but I can in windows and ultimate edition- (based on ubuntu 8.04).

I seem to remember reading something about ubuntu not searching for storage within storage- it just searches for the one level and then stops- something like that anyway

anyone know how to solve that.

---

### Post by camporter1 on 2010-02-27
Someone might know, but you'll probably need to tell us exactly which device it is that's causing the problem. I know that players that just have flat file support tend to work the best.

---

### Post by cloyd on 2010-02-27
I don't know if this will work, but I had trouble with Sandisk drives, and Ubuntu seemed to see them as a usb drive inside a cd drive. This worked.

sudo mount -t vfat /dev/sdb1 /media/usb -o  uid=1000,gid=100,utf8,dmask=027,fmask=137

It also mounted some other usb drives I was having trouble with.  Don't know that it will work for you, but give it a try.  If it works, you will have to give the command every time you mount, and also manually unmount.  I wrote an executable script file so I wouldn't have to enter this every time. I'll be off line for the rest of the day, but interested to know if it helps.  Found the command in the community documentation.

---

### Post by Bartender on 2010-02-27
We've got a Sansa Fuze, and three different Ubuntu PC's that all see the microSHD card without any difficulties.  They'll show two devices on the desktop when the Sansa is plugged in.  Clicking them opens up browsers for each storage device.

You _have_ to set the Sansa to run in MSC mode rather than MTP.  This option is in Settings> System Settings> USB Mode>

---

### Post by ave2 on 2010-03-03
> **cloyd said:**
> I don't know if this will work, but I had trouble with Sandisk drives, and Ubuntu seemed to see them as a usb drive inside a cd drive. This worked.

sudo mount -t vfat /dev/sdb1 /media/usb -o  uid=1000,gid=100,utf8,dmask=027,fmask=137

It also mounted some other usb drives I was having trouble with.  Don't know that it will work for you, but give it a try.  If it works, you will have to give the command every time you mount, and also manually unmount.  I wrote an executable script file so I wouldn't have to enter this every time. I'll be off line for the rest of the day, but interested to know if it helps.  Found the command in the community documentation.

Hi, yes I am using the sansa express- unfortunately I run most of my day to day activities as a user and not as administrator, so I dont have access to sudo.... is there perhaps another way to search for connected devices?


> **Bartender said:**
> We've got a Sansa Fuze, and three different Ubuntu PC's that all see the microSHD card without any difficulties.  They'll show two devices on the desktop when the Sansa is plugged in.  Clicking them opens up browsers for each storage device.

You _have_ to set the Sansa to run in MSC mode rather than MTP.  This option is in Settings> System Settings> USB Mode>

sorry to sound stupid, but I cant find settings > system settings- im using 9.10 if this makes a difference, and when I look through applications, places and system at the top of the screen there doesnt seem to be any option for USB mode

---

### Post by mcduck on 2010-03-03
> **ave2 said:**
> 
sorry to sound stupid, but I cant find settings > system settings- im using 9.10 if this makes a difference, and when I look through applications, places and system at the top of the screen there doesnt seem to be any option for USB mode
That would be a setting in your music player, not in Ubuntu... ;)

---

### Post by Bartender on 2010-03-03
Thanks, mcduck, for clarifying that important distinction. :)

It didn't even occur to me to mention that those settings are on the player, not the computer.  Of course, at that point I didn't know whether the OP was using a Sansa product or not.  

I wonder - do most portable players that are designed to function across various platforms have a similar function built into them?  It seems like they'd have to?

---

