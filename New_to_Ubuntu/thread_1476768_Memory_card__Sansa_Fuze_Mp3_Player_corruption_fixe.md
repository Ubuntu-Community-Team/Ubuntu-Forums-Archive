---
title: "Memory card / Sansa Fuze Mp3 Player corruption fixes?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2010-05-08
Hiya everyone,

I and a friend have a problem his memory card reader seems to be corrupted and the suggested advice is to use Windows to back it up and reformat it, but not to use Ubuntu to reformat it has his Digital camera wouldn't read it.his post is here [http://ubuntuforums.org/showthread.php?t=1476244&highlight=memory+card+reader]("http://ubuntuforums.org/showthread.php?t=1476244&highlight=memory+card+reader")

I have the problem I have a Sansa Fuze 4gb which accepts Mp3 files draged and dropped in windows but in Ubuntu hangs when doing the same when refreshing the media library on itself (Done Automatically by the player and cannot be skipped).

The problem lies in: > suggested advice is to use Windows to back it up and reformat it, but not to use Ubuntu to reformat it has his Digital camera wouldn't read it.

We are both dual-booters (Windows/Ubuntu) so this is possible however we wish to go UBUNTU ONLY in the future this reliance on windows is a stumbling block can anyone help (using Ubuntu only)?

---

### Post by Nightstrike2009 on 2010-05-08
Surely it must be possible on Ubuntu? how do the Ubuntu only users manage to get around this if they don't run windows.  

Is it possible that you could format it with Ubuntu as long as you placed the same folders (by creating new ones) on the reformated card as they were before?

---

### Post by dracayr on 2010-05-08
for your player: If I understand correctly, you can't place files on it? in the mp3player settings, there should be sth. like connection mode where you can choose between MSC and MTP. Choose MSC and see if that helps.
(Tipp: If you want sth. really cool, install Rockbox on your fuze. I have a fuze with rockbox, and it works perfectly)

dracayr

---

### Post by Phosphorror on 2010-05-08
Nightstrike,

[The aforementioned post is here (clicky)]("http://ubuntuforums.org/showthread.php?p=9258983#post9258983")

I have further investigated another memory card and it works completely fine. I do remember going to a gig with the camera and coming back, and a couple of the pictures had got garbled.

It worked in Windows, but Ubuntu doesn't understand it and appears not to be very forgiving of the problem. If you observe the post above, it was mentioned not to format the card via Linux as the camera wouldn't understand it - from what I gather.

---

### Post by Nightstrike2009 on 2010-05-08
I have located you post now Phosphorror,

Thanks for the link though the advice is sound, I think there must be another away other than dual booting just to sort out a memory card problem, I have posted similar on your thread.

I don't accept using windows as a workaround just to fix a memory card, their must be another way and hope this post gets to the bottom of it.

PS: I have an Sony Memory Stick Duo Adapter and an old card out of a PSP (a Sony 32mb Memory Stick Duo) and have no such issues with my reader, I was going to ask if your reader was compatible with SDHD rather that just SD but has it works in windows it doesn't seem to be your reader (unless it relies on some kind of Windows software to work, which seems unlikely).

---

### Post by Nightstrike2009 on 2010-05-08
Hiya dracayr,

No mate I know what you mean but it isn't the issue, I can do everything I can in windows as my sansa fuze is drag and drop. The problem lies in after the player has been disconnected it "updates its media library" this completes in windows but not after Ubuntu drag and drop, does having your album art highter res that 128x128 cause this? 

I know having the tags in ID3v2.4 standard causes issues with my player but when you use ID3v2.3 the error still occurs.

---

### Post by dracayr on 2010-05-08
that's strange, it works fine on my fuze. I normally use the command line to copy files to the player. does that work? (should be sth. like ```
cp music.mp3 /media/SANSA\ FUZE/
``` but maybe the mount point is different on your computer)

dracayr

---

### Post by Nightstrike2009 on 2010-05-08
maybe dracayr

Problem is i am newish to Ubuntu (7.04) and although I do use the command line more these days my knowledge is limited to "suso apt-get install" and other basic commands I used to use deb files up until now,

You also mentioned previously you use rockbox I am using the original firmware on mine, cheers for the help thou

---

