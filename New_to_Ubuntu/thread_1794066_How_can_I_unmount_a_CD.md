---
title: "How can I unmount a CD ?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-30
Hello,
I am trying to figure out how to unmount a CD.
I have Ubuntu 10.10 and I am using Virtualbox with a guest OS of Windows XP. When I run XP, for some reason XP will not access the CD player. I think I might need to unmount the CD in Ubuntu, so that XP can read it, but I don't know how to unmount the CD.
 I don't have anything in my /media folder except a "floppy" and a "floppy0" directory, so the CD is not mounted there. 
Also, the only thing in my /mnt directory is a "floppy" directory.
I have a /dev/sr0, which I believe is the CD device, but I tried to unmount it and that doesn't work.
 ( I have "ATAPI iHAP322 9 sr0" showing for the CD in the virtualbox cd/dvd devices )

---

### Post by haqking on 2011-06-30
it is not always in /media

try 
sudo umount /cdrom

depends on its location

---

### Post by dFlyer on 2011-06-30
Have you tried typing eject from the command line. Also if any windows from the cd is open it will not unmount or eject until they are closed.

---

### Post by haqking on 2011-06-30
> **dFlyer said:**
> Have you tried typing eject from the command line. Also if any windows from the cd is open it will not unmount or eject until they are closed.

eject will open the drive

umount will remove the volume ?

these do similar things but not the same ?

eject first calls umount, umount just does its job

---

### Post by s1baker on 2011-06-30
When I do a "sudo umount /cdrom"
I get this:
```

umount: /cdrom: not mounted
```

yet, the CD has to be there, I can play a music disk in it.

---

### Post by dFlyer on 2011-06-30
make sure the music player is closed. If it's open you will be unable to eject it.

---

### Post by s1baker on 2011-06-30
also, I can eject the CD by calling "eject /dev/sr0",
but then when I go into VB with XP running, and I try to access the CD drive, XP tells me to insert a CD, when the CD is inserted, XP won't acknowledge the drive. When I go back out into Ubuntu, I can access the drive and read it with Ubuntu.

---

### Post by s1baker on 2011-06-30
```
make sure the music player is closed. If it's open you will be unable to eject it.
```

There isn't any window in Ubuntu open for the CD and the tray is closed, it is just sitting there, but I have a icon on the Ubuntu desktop that I can click on and music will play ( Ubuntu can access the disk ), I shut that down, go back into XP, but XP can't see or read the CD.

---

### Post by howefield on 2011-06-30
I think you are on the wrong track here, only data cds get mounted not audio cds ?

---

### Post by s1baker on 2011-06-30
```
I think you are on the wrong track here, only data cds get mounted not audio cds ?
```
here is the story. I can reboot the computer without any CD in the player. I then can run Virtualbox and run XP as the guest OS. When I am in XP and I try to access the CD, it asks me to insert a CD, which I can do, I can select "eject" and the tray will open up and I can put a music disk in the CD and close the tray. but XP then says that the disk is unreadable. When I try to eject the CD in XP or manually eject it, nothing happens. When I go back out into Ubuntu, I have a CD icon on the desktop, and I can eject the tray in Ubuntu. I can't play the music in XP though, works just fine in Ubuntu.
 I think it may be because XP running within Virtualbox can't play music.

---

### Post by haqking on 2011-06-30
> **s1baker said:**
> ```
I think you are on the wrong track here, only data cds get mounted not audio cds ?
```here is the story. I can reboot the computer without any CD in the player. I then can run Virtualbox and run XP as the guest OS. When I am in XP and I try to access the CD, it asks me to insert a CD, which I can do, I can select "eject" and the tray will open up and I can put a music disk in the CD and close the tray. but XP then says that the disk is unreadable. When I try to eject the CD in XP or manually eject it, nothing happens. When I go back out into Ubuntu, I have a CD icon on the desktop, and I can eject the tray in Ubuntu. I can't play the music in XP though, works just fine in Ubuntu.
 I think it may be because XP running within Virtualbox can't play music.


XP plays music just fine in Virtualisation.

Do you have passthrough enabled ? and from devices menu making sure device is checked which on mine removes it from host.

---

### Post by howefield on 2011-06-30
> **s1baker said:**
> I think it may be because XP running within Virtualbox can't play music.

OK, try this, when you have XP up and running, pop the Audio CD in and open up Windows Explorer, then from the VirtualBox Devices menu, select the "Remove disk from virtual drive" option. Then from the Devices menu select the CD-rom drive. Windows explorer should see the audio CD.

Here's what happens when I put an audio CD into the windows VM. Both Ubuntu and Windows can see it.

---

### Post by s1baker on 2011-06-30
I just discovered I can read a data disk in XP and if I put a music disk that has MP3's on it, I can play them. But a music disk with .wav files on it won't open in XP. Now I can copy those wav files in Ubuntu to the shared folder that I have with XP, and I can play them. But the cd with the wav files on them will not open in XP. This wav CD has a total size of 1/2 gig, so it might be some sort of memory constraint, maybe I need to increase my memory allocation for XP.

---

### Post by haqking on 2011-06-30
> **s1baker said:**
> I just discovered I can read a data disk in XP and if I put a music disk that has MP3's on it, I can play them. But a music disk with .wav files on it won't open in XP. Now I can copy those wav files in Ubuntu to the shared folder that I have with XP, and I can play them. But the cd with the wav files on them will not open in XP. This wav CD has a total size of 1/2 gig, so it might be some sort of memory constraint, maybe I need to increase my memory allocation for XP.


Audio Cd's do not use .wav files.  They us Redbook audio format.

IS this a genuine Audio cd or copy or a cd full of .wav files ? as this would be different.

Can you play a genuine audio cd ?

---

### Post by s1baker on 2011-06-30
```
Audio Cd's do not use .wav files. They us Redbook audio format.

IS this a genuine Audio cd or copy or a cd full of .wav files ? as this would be different.

Can you play a genuine audio cd ?
__________________
```

Yes, these are all store bought music CD's with "Track1.wav", Track2.wav", etc., on them. They will not open in XP, and after inserting one in XP, I cannot get the "eject" command to work, but when I go back out into Ubuntu, then I can eject them. I can get them to play by copying them in Ubuntu over to my shared folder that I use with XP, and then I can play them from there in XP, only one track at a time though, but XP under VB will not open any of my wav files off of a CD. 
No problem playing them in Ubuntu, so it probably doesn't make any difference anyway, because I can listen to them in Ubuntu will I use XP. I only really need XP CD to work so I can load drivers for a cad package I use in XP.

---

### Post by haqking on 2011-06-30
> **s1baker said:**
> ```
Audio Cd's do not use .wav files. They us Redbook audio format.

IS this a genuine Audio cd or copy or a cd full of .wav files ? as this would be different.

Can you play a genuine audio cd ?
__________________
```Yes, these are all store bought music CD's with "Track1.wav", Track2.wav", etc., on them. They will not open in XP, and after inserting one in XP, I cannot get the "eject" command to work, but when I go back out into Ubuntu, then I can eject them. I can get them to play by copying them in Ubuntu over to my shared folder that I use with XP, and then I can play them from there in XP, only one track at a time though, but XP under VB will not open any of my wav files off of a CD. 
No problem playing them in Ubuntu, so it probably doesn't make any difference anyway, because I can listen to them in Ubuntu will I use XP. I only really need XP CD to work so I can load drivers for a cad package I use in XP.

have you enabled passthrough from the Vm machine settings ?

---

### Post by s1baker on 2011-06-30
```
have you enabled passthrough from the Vm machine settings ?
```

When I select "passthrough" and then run XP, I have no icons on the desktop screen , nor do I have a command bar at the bottom with the "Start" on it. All I have is the desktop screen. I have to select the "X" at the top right of XP to power of the machine. If I go back into settings and uncheck "passthroug", then XP boots up properly.

---

### Post by FormatSeize on 2011-06-30
I found this:
> A Virtual Machine has no direct hardware access. A VM is not designed for Multimedia.
 
It came up in a Google search. [http://forums.virtualbox.org/viewtopic.php?f=1&t=4564](http://forums.virtualbox.org/viewtopic.php?f=1&t=4564)
 
I don't have any experience with virtual machines, so I don't know how true/untrue that is.

---

### Post by haqking on 2011-06-30
> **FormatSeize said:**
> I found this:

 
It came up in a Google search. [http://forums.virtualbox.org/viewtopic.php?f=1&t=4564](http://forums.virtualbox.org/viewtopic.php?f=1&t=4564)
 
I don't have any experience with virtual machines, so I don't know how true/untrue that is.

It is true that VM are not designed to have direct hardware access, it does not stop them playing audio cd's perfectly fine however ;-)

His problem is not related to VM and direct hardware access IMO, i have numerous VM's and have used virtualisation for many years and never had an issue especially with such a simple thing as playing a Audio cd

---

