---
title: "Rhythmbox cannot extract more than 1 cd"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-06-06
I have two cds. No matter what I do to get Rhythmbox to extract both, it repeatedly says I have all the files from the first cd, and either ignores or cannot read the second cd. It does find the NAME(S) of the cd, i.e., disk 1 and disk 2, but can't extract both. WTF?

---

### Post by -kg- on 2009-06-06
You haven't provided enough information.  What exactly are you trying to do, and how are you trying to do it?  Do you have two cd players and are trying to extract them simultaneously?  Are you trying to extract these two cds to one file?

---

### Post by Mark_in_Hollywood on 2009-06-06
> **-kg- said:**
> You haven't provided enough information.  What exactly are you trying to do, and how are you trying to do it?  Do you have two cd players and are trying to extract them simultaneously?  Are you trying to extract these two cds to one file?

Sorry, 'bout that. I confess I'm so much a novice at this that I don't much know what I am doing.

Both CDs are audio disks. I have a CD r-w and Jaunty offers to open with Rhythmbox automatically. I put disk-1 in the cd, opened Jaunty and when the app came onscreen, under media, it listed:

disk-1.

Highlighting that, I found I could "extract" and did. RB read the cd, made a folder under music and copies the cd-1 to that folder.

When that was finished, I "ejected the cd via the desktop icon, put the disk-2 into the drive and pushed the "open/close" button. Again the same happened, I was offered a choice and chose RB. It opened, and under media found disk-2, BUT when asked to extract the files, it DOESN'T. It did make another folder in /Music with the same "album" name, and inside that folder it says "disk-2" but the files are the exact same!!!!

the command: scan removeable media, doesn't seem to work.

---

### Post by -kg- on 2009-06-06
I am attempting to extract two albums the same way you did so I can tell you something.  Be right with you...

---

### Post by -kg- on 2009-06-06
Well, Rhythmbox seems to be doing it correctly for me.  Of course, the two albums are different artists, not Disk 1 and Disk two of the same album.  But I would think that it would be the same.

I did notice that it takes a while to rip the albums, but that could be because I'm ripping to ogg-vorbis format, and I have ogg vorbis set to a relatively high quality.

Did RB name the songs and artist in the list, or did you just have "Track-1," Track-2," etc.?  If that was the case, it might have worked but just looked the same.  Did you play, say, the first song from each disk to make sure that they were indeed the same song?  I don't know how it could possibly rip the exact same songs off of different disks.

<edit> #-o I meant to say, Did you play, say, the first song from *_the folder_* for each disk.  Naturally, I would assume that the first song off each disk would be different!

---

### Post by Mark_in_Hollywood on 2009-06-06
I'm not experienced with RB enough to give sensible answers, with this one excpetion:

RB made a folder for each disk. Each folder had a properly named sub-folder, viz:

/music/PI/disk-1
/music/PI/disk2

all files within those two folders were the same files. Same filenames, same sounds, etc.

The disks, are labeled with tracks with different names, but its (stupidly) possible that they are NOT different, only mis-labeled.

Thanks for your time with this, but for now, I quit.

---

### Post by -kg- on 2009-06-06
OK.  When you're ready to give it another go, try this:

Open Nautilus and navigate to the folder that contains the "Disk 1" and "Disk 2" folders.  Go into each folder and mouse over the first song in that folder.  This will "play" the song temporarily.

If the first song is different, then the songs on the 2nd disk were merely mislabeled and you will have to take the second disk and rename the songs.  If they actually are the same, I couldn't say *what* happened, because like I said above, I don't know how you could rip the same songs off of different disks.

Could it be possible that you accidentally put the same disk in the second time and re-ripped it?  Or you might check and see if the recording company accidentally put the same disk in for both disks and they both have the same songs on them.  You'd have to play both the disks to check that.

<edit> I really, *really should* read posts more carefully:

> all files within those two folders were the same files. [COLOR="Red"]Same filenames, same sounds, etc.[/COLOR]


#-o

Well, that just leaves the options of accidentally putting the same disk in the second time or the recording company screw-up.  There's no other way that I can think of.  Naturally, you won't need to open Nautilus and check something you already know. :p

---

