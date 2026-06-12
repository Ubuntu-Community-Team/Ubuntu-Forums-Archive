---
title: "bootmgr missing"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by nitstorm on 2009-11-25
hey guys,

i picked up an old hard-drive and wanted to install karmic on it jus to try it out. had wiped it a while back using the partition manager on vista.this is what i did:

1. used usb startup disk creator on jaunty and wrote the image of karmic (32-bit)
2.had to use the cable that connects the dvd drive i have  coz the hard drive is pretty old and the one connecting my current hard-drive is different
3. disconnected the old hard drive and booted the comp
4. this is where the error BOOTMBR missing gets displayed asking me to restart by holding ctrl+alt+del

what do i do???

---

### Post by mbzn on 2009-11-25
Am i correct to say that you have your SATA(Guess) disk back as it was before you added the 'old-hdd'

If this is the case, just check in your BIOS that the hdd boot order is the same as it was before. (This error typically means that the bios is looking for a boot record in the wrong place). 

Hope this helps

---

### Post by nitstorm on 2009-11-25
i disconnected the hard drive i am using currently before connecting the old one, so no boot error thing there....

---

### Post by kansasnoob on 2009-11-25
Shouldn't it be trying to boot from the usb startup disc first?

If it's not maybe the BIOS settings need to be changed like try to boot from CD 1st, then usb, then hard drive?????????

Or maybe I'm totally barking up the wrong tree.

---

### Post by nitstorm on 2009-11-25
wen i connected jus the old hdd and the usb drive, the usb drive was detected in the hdd boot order, i set it first to the usb and hdd was second and once i rebooted i got the error message

BOOT ERROR

BOOTMGR missing
Press Ctrl+Alt+Del to restart

now i am trying to format the hdd to fat32 in vista and gonna try again,jus a brainwave here - should i copy the image of xp or something and go into the recovery console and type fixmbr? will that work?

---

### Post by nitstorm on 2009-11-25
ok, i discovered usb startup disk creator only works with ubuntu images, doesn't support to copy any other .iso  plus i cannot use the dvd drive directly either coz if the old hdd is connected the dvd drive doesnt get detected, any way to solve this problem guys???

---

### Post by nitstorm on 2009-11-25
what do i do? what do i do? what do i do?????

---

### Post by nitstorm on 2009-11-25
bump? 

no fix at all???????

---

### Post by nitstorm on 2009-11-25
am i asking this in the right place or am i supposed to be asking this is main supported categories?

---

### Post by oldfred on 2009-11-25
I would check your drive and cable. 

If this is an old pata drive you have jumpers for master, slave & cable select. Newer pata drives used cable select but required newer cables that supported cable select. As I remember the last connector (master) was black and the middle was grey (slave). Where old cables both connectors were grey and you could only select with the jumper on the hard drive. I have been using sata for several years so I am not sure of all this but I would check hardware. I think if you use the CD/DVD cable it will not work for the hard drive.

---

### Post by nitstorm on 2009-11-25
but i use the dvd drive cable, which fits perfectly, and the hard drive was detected by the comp and i could format it and access the drives. is there someway to put in a MBR, coz that's the only thing missing i guess, or is there some way to copy the MBR from this comp to that old HDD so that i am able to format it

---

### Post by nitstorm on 2009-11-25
bump????

---

### Post by ElevenWarrior on 2009-11-26
having a similar problem, Vista woln't boot with it saying boomgr is missing.
still haven't sloved it yet.

---

### Post by oldfred on 2009-11-26
Further explanation of why cables that fit may not be the same and with many versions of the ATA standard not all cables/devices work the same if the cable is wrong.

[http://en.wikipedia.org/wiki/AT_Attachment](http://en.wikipedia.org/wiki/AT_Attachment)

---

