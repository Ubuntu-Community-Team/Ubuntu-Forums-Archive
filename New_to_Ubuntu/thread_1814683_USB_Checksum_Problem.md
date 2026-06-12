---
title: "USB Checksum Problem"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Green_Grenade on 2011-07-29
Im trying to put Ubuntu 11.04 on to a 4gb USB stick and at 38% it tells me the Checksum aint aligned or something like that. Pressed Retry and something 38% checksum problem

Any ideas??!

---

### Post by Redblade20XX on 2011-07-29
Can you check if the downloaded iso's checksum is the same as the one the site gives?

---

### Post by Green_Grenade on 2011-07-29
How do I do that?! LOL!

---

### Post by Redblade20XX on 2011-07-29
> **Green_Grenade said:**
> How do I do that?! LOL!

Take a look at this,

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Green_Grenade on 2011-07-29
ok.. it says "go to the correct directory to check a downloaded iso file" ... how do i do that?! 
The file is in my Home folder..

---

### Post by Redblade20XX on 2011-07-29
> **Green_Grenade said:**
> ok.. it says "go to the correct directory to check a downloaded iso file" ... how do i do that?! 
The file is in my Home folder..

Alright, you'll have to open a terminal and type in.

```

cd <the location where you downloaded the iso>

ls (to see if the iso is in that location)

md5sum <the iso name you'll see as a result of ls>


```
If the result of md5sum doesn't match the one given here
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

then there is a problem with the iso file you downloaded and you'll have to re download it.

---

### Post by Green_Grenade on 2011-07-30
K!

this is what i got..
f63028da38308d917cd1460e14fb8540  ubuntu-10.04.3-desktop-i386.iso
f63028da38308d917cd1460e14fb8540
The website ^

Sorrry about it being Ubuntu 10.. I lost my 11.04 somewhere.. No Idea.

---

### Post by Redblade20XX on 2011-07-30
There's nothing wrong with the iso. Are you trying to create a bootable usb or just transporting the iso file? Either way, can you format the usb to FAT32 and try again?

---

### Post by Green_Grenade on 2011-07-30
Im trying to make it bootable (friends windows comp crashed)

Ill reformat the usb stick and try it again. I downloaded the ... USB-creator-kde. But ill try it again with the Startup Disk creator.. or is that the wrong thing?!
Question: Does it matter that I'm running Ubuntu 11 and trying to make a Ubuntu 10.04 bootable USB??

---

### Post by Redblade20XX on 2011-07-30
> **Green_Grenade said:**
> Im trying to make it bootable (friends windows comp crashed)

Ill reformat the usb stick and try it again. I downloaded the ... USB-creator-kde. But ill try it again with the Startup Disk creator.. or is that the wrong thing?!
Question: Does it matter that I'm running Ubuntu 11 and trying to make a Ubuntu 10.04 bootable USB??

There shouldn't be a problem dealing with versions of ubuntu if the one that's creating the bootable usb is later than the iso.

---

### Post by Green_Grenade on 2011-07-30
Ok.. 

SO! I formated it.. the same thing happened (the checksum problem). So I hit retry and it started over now... No its doing it again. Any other ideas?!

---

### Post by Redblade20XX on 2011-07-30
> **Green_Grenade said:**
> Ok.. 

SO! I formated it.. the same thing happened (the checksum problem). So I hit retry and it started over now... No its doing it again. Any other ideas?!

Did you use the startup disk creator?

---

### Post by Green_Grenade on 2011-07-30
Yes. Im trying it right now with the KDE creator I downloaded..

---

### Post by Green_Grenade on 2011-07-30
Its not working.. I just checked Youtube.. and the guy was talkin about having a file in the folder that has the 'hash' numbers in it. And to name the file the same as the Iso file but to save it as blahblahblah.iso.md5... ??

---

### Post by Redblade20XX on 2011-07-30
Hmmm this problem is weird anyways, check this out for alternative ways to create a bootable,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Green_Grenade on 2011-07-30
LOL! Ya.. that what I got open to.. I dunno.. 

Tried making that iso.md5 file.. it didnt work.

---

### Post by Green_Grenade on 2011-07-30
Am I formatting it wrong?! I right click on the drive go down to format and ya.. format to FAT...

---

### Post by Redblade20XX on 2011-07-30
[COLOR=black]Your using the startup disk creator right?
[/COLOR][ATTACH]198830[/ATTACH]

You can format the usb by using the "erase disk option". Also can you post the exact error and the usb brand?

---

### Post by Green_Grenade on 2011-07-30
Yes. That is what I am using.
Um.. as for the brand name of the USB stick.. Im not sure.. it looks like Gohan from DragonBall Z..and when its plugged in its just.. 4.2 GB Filesystem
The message reads "Checksums do not match. Retry?" then Yes or no buttons. When i click No it just shuts down. Clicking Yes it just ya retrys..

---

### Post by Green_Grenade on 2011-07-30
OO! its a udisk USB 2.0

---

