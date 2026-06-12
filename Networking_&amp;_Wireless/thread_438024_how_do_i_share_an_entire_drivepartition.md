---
title: "how do i share an entire drive/partition?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by souldances on 2007-05-09
hi.  i'm happily using a fresh install of edgy (so long micros**t) and am grappling with networking (using samba, networking to a win xp machine).  i appear to have gotten a couple of folders shared, but can't figure out how to share an entire drive.  i've got several drives (partitions) that have way too many folders to share individually, particularly my music drives - they have upwards of 90 folders.  is there a way to share the entire drive?  when i select the drive, i don't see a share option, and when i select more than one folder, i don't see a share option...  is there a terminal command i can use?  help, please!   :-)  thanks - alan

---

### Post by dante.regis on 2007-05-09
if you are talking about sharing your WINDOWS folders, you don't need to do that, windows already shares, by default, all your partitions (call that security if you want!). To access them, just place an "$" after the partition drive letter. So, to access C:\ on \\OLDPC, just use \\OLDPC\C$ . If I am not wrong, you will have the same read/write access as you would if you were logging in locally with the chosen user.

Best,
Dante

---

### Post by tact on 2007-05-10
last poster mentioned sharing whole windows drives...

Regarding sharing whole drives in ubuntu:
You are still suffering "windows-think" if think about sharing whole drives.  In ubuntu (linux generally) you have a (proper) multi-user system and thus you need to get into the habit of thinking "home folder" and not "C:\"

Store all your files in a directory off your home folder (eg /home/your_username/your_music) and then share out your whole user home directory (if you must - its not a good idea .... just share the music folder).

---

### Post by souldances on 2007-05-14
> **tact said:**
> last poster mentioned sharing whole windows drives...

Regarding sharing whole drives in ubuntu:
You are still suffering "windows-think" if think about sharing whole drives.  In ubuntu (linux generally) you have a (proper) multi-user system and thus you need to get into the habit of thinking "home folder" and not "C:\"

Store all your files in a directory off your home folder (eg /home/your_username/your_music) and then share out your whole user home directory (if you must - its not a good idea .... just share the music folder).

how do i do this if i've already got 65gb of music files in over 90 folders on another (physical) drive and the partition my home folder is in is about 7gb?  i have three physical drives, each set up with at least three partitions, and each of my media storage partitions is larger than the entire physical drive my ubuntu and swap partitions are in.  i was really hoping for a way to key a line into terminal that would render an entire media 'drive' (partition) shared.  if the 'virtual drives' are considered folders, i should be able to share the entire music drive like sharing a folder, or at least that was what i was hoping to find...

---

### Post by tact on 2007-05-16
> **souldances said:**
> how do i do this if i've already got 65gb of music files in over 90 folders on another (physical) drive...

Ok. Now I understand more what you are trying to do..the short answer is:  I don't know how to share an entire drive thats attached to a linux box.  But....

....what about creating a 91st folder in the root of that physical drive containing all the music files in 90 folders, and giving it a name like "music drive" and then select the 90 other folders full of music and drop them (move them) into the empty "music drive" folder.  Then share THAT folder for using Samba so the WinBox can see it.

Cheers

---

### Post by souldances on 2007-05-22
sorry for the delayed reply.  thanks for the folder suggestion, it worked.  actually i feel silly that i didn't think of that myself - it is rather obvious.  i'll keep that in mind when i eventually move everything to a bigger storage drive.  i realized i could further organize my music according to how i create playlists (all audio, music only, 'low thump' music only, meditation music, spoken word, etc.).  i must say that my ubuntu experience has been increadibly positive - a world apart from my micros**t experiences had  been.  happy, happy, joy, joy!  :p  - alan

---

### Post by scott_g on 2007-05-22
Hi,

If you know where your extra "physical drive" is mounted (using fdisk, or system monitor), you can share that folder.  For example, by default, the windows partition is mounted in /media/windows.  So you could share the /media/windows folder.  I think thats what you're trying to do?

Scott

---

### Post by tact on 2007-05-23
*BING*   scott_g!  Of course that would also work....


Whenever you mount another HDD its in /media there somewhere... sharing that shares a whole drive for sure.

---

