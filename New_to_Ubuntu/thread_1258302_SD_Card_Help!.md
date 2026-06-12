---
title: "SD Card Help!"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by ColinGrimm on 2009-09-04
I have a PNY SDHC card, which worked fine with the built in SD reader on my Sony Vaio, however, I was trying to get data off a friends computer (Who is running Vista) I think that their computer reformatted the SD card, now it will not work at all with my Ubuntu 8.10. Nothing happens at all when I plug it in. Please help! I am a newbie to ubuntu

---

### Post by tacantara on 2009-09-04
Have you tried inserting any other SD cards to see if there is a hardware problem?  Was the SD card that you're having a problem with previously formatted in a Linux format (i.e. ext3 or ext4)?  I have an SD card reader on my machine, and I haven't had any problem with it going between my digital camera and the computer, and I haven't changed the formatting on it (I previously used it with a Windows Vista based machine).

---

### Post by ronparent on 2009-09-04
does the card show in gparted?

---

### Post by ColinGrimm on 2009-09-04
Yeah, I used it all the time as movie storage for my MP3 player, but ever since I put it in my friends laptop it won't work. And yes, other SD cards work fine. And not it doesn't show in GParted.

---

### Post by ronparent on 2009-09-04
Looks like a reformat is your best bet. If reformatting doesn't work with gparted, you could try vista.

---

### Post by ColinGrimm on 2009-09-04
It does not show in Gparted, or even when I type "df" in Terminal. I don't have a Vista computer, is was my friends computer. Any other ideas? Thanks for the help!

---

### Post by Paqman on 2009-09-04
> **ColinGrimm said:**
> Any other ideas?

Is there another machine you can try it in? Sounds a lot like the card has died.

---

### Post by ColinGrimm on 2009-09-04
I only have my MP3 player right now, and it says "Media is not formatted with a supported filesystem" I think it reformatted when I put it in my friends computer, cause it worked on her machine.

---

### Post by ronparent on 2009-09-05
Will your mpt player format it?

---

### Post by LewRockwell on 2009-09-05
when it's in your reader, what does```
sudo fdisk -l
```show?

(that's a little "L" and not a one)

.

---

