---
title: "Music stored on Sanza Fuze appears in Windows; not Ubuntu"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by diablo75 on 2010-04-24
I have an 8GB Sanza Fuze that I have been able to mount easily in Windows when the USB mount settings on the device is set to "Automatic" and used Rhapsody (in Windows) to transfer MP3 files to the device.  However, when I attach the device to Ubuntu, it only recognizes/mounts it (or appears to, via the status notification up top) if it is set to MSC mode.  However, if I open Rhythmbox in Ubuntu and attempt to browse the contents of the device, it says there are import errors.  Under location:

file:///media/SANSA FUZE/AUDIBLE/AudibleActivation.sys

And under error it says:

"No valid frames found before end of stream"

If I go into my Places menu and select the Sanza from the menu, it appears to open just like a USB flash drive with a file structure, but none of the folders seem to contain any music at all (even if I select Show Hidden Folders from the View menu).  Further, there is no MicroSD flash memory installed in the device the music could be hiding on so I'm not sure where it's being stored; only that it says about 6 GB of my 8 GB of space is remaining free (so it at least knows some of it is being used somewhere).  Scanning the device the Applications>Accessories>Disk Usage Analyzer doesn't help in finding the location of any music so I'm not sure where it's gone to.

Now I tried to copy a few MP3s (while in Ubuntu) into the Audiobooks folder on the MP3 player and it seemed to copy with no problem.  But when I unplugged the device from the computer, the MP3 player said it was refreshing itself, but when I went to look for the files I copied over they weren't shown.  When re-attaching the device to Ubuntu to browse via the Places menu, it was as if the files just vanished or weren't actually copied like I thought they were.

Hmmmm......

---

### Post by I8NY on 2010-04-24
okay there are 2 modes for the fuze, MSC and MTP.  For some strange reason the files you write to it in what ever mode will ONLY show in that mode you wrote them in.  So windows will write the files in MTP and Ubuntu will read it in MSC and the files will not show until Ubuntu uses MTP mode that windows used.  I would set it to MSC and write all the files that way and not worry about it again.  Hope this helps.

---

### Post by anewguy on 2010-04-24
I8NY, is your userid based in any part on the Gary Larson FarSide where the city appears in destruction in the background while creatures drive a car with I8NY on the license plate, or is a reference to something a little more esoteric?

Dave ;)

---

### Post by diablo75 on 2010-04-24
> **I8NY said:**
> okay there are 2 modes for the fuze, MSC and MTP.  For some strange reason the files you write to it in what ever mode will ONLY show in that mode you wrote them in.  So windows will write the files in MTP and Ubuntu will read it in MSC and the files will not show until Ubuntu uses MTP mode that windows used.  I would set it to MSC and write all the files that way and not worry about it again.  Hope this helps.

Simple enough.

THANKS!

---

### Post by I8NY on 2010-04-25
anewguy, my user name did not come from FarSide strip(i have read them) the idea was from a garfield comic strip that had garfield in a car with the license plate I8NY.  But could you send me a link for that FarSide strip i would like to use it as a avatar.:D  diablo75 please mark the thread as solved.

---

### Post by XVampireX on 2010-05-14
Hi, I have the same problem, the thing is I didn't use any applications to transfer my music, I used MSC mode on windows, but when I go to rhythmbox using MSC, it can't find anything, nautilus doesn't see anything either, but in RTP it finds everything the only problem is that for some reason it gets stuck...

If anyone can help me that would really be good, thank you :)

---

### Post by I8NY on 2010-05-14
i don't know what "RTP" is.  i wouldn't try finding the files in rhythmbox or do anything when autoplay ask you to open with what ever, just close it.  Browse to it in nautilus, maybe even try MTP mode.  It could be a bad mount or you did write the files in MTP mode.

---

### Post by XVampireX on 2010-05-14
sorry I meant MTP Mode... not RTP :P

In MTP mode I see the files, but when I try to play it, it freezes.. in MSC, It mounts and everything but I can't see the music files.

---

### Post by I8NY on 2010-05-14
is the music the preloaded stuff? those have been written in MTP mode and i think you can use widows to move the music off and write it back in MSC mode.  I have tested that in ubuntu you can't play or view a image on the fuze memory in MTP mode but you can copy the files off and then open them. You could try finding the music in the terminal to see if your in the correct mode. But it sounds like you wrote the file in MTP mode that isn't too friendly w/ linux.

---

### Post by XVampireX on 2010-05-15
No, I loaded my own music on Windows, last time I checked without changing it, it was MSC, not MTP.

---

### Post by I8NY on 2010-05-15
well i'm running out of ideas but you could try the option in view to show hidden file.  maybe try viewing the music on a live ubuntu cd or another pc, it could be your pc idk. sorry i don't know what else to do.

---

