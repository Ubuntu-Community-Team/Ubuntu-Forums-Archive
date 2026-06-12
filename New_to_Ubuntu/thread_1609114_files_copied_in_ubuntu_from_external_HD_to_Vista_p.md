---
title: "files copied in ubuntu from external HD to Vista partition corrupted?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by jellyfish27 on 2010-10-30
Hi. I've been dual-booting Lucid x64 (ext3) and Windows Vista x64 (NTFS) on my HP laptop for about 4 months.  I also have a 1.5 TB Seagate external hard drive (NTFS), which is mostly music and videos.

I'm in the process of moving about 35GB of music from the external drive to the Vista partition on my computer.  I started doing this from the Ubuntu partition.  I could play them in Rhythmbox after I copied them.  About 10GB in, I was booted into Vista and decided to check on the files to make sure they were working ok.  The folder I put them in was empty.  Nada.  0 bytes used.  So I booted back into Ubuntu and looked again.  Well, all of the folder names were correct.

Out of the 68 folders transferred, five contained a single .dll file, 62 were no longer folders (instead becoming what the computer thinks are a mix of xml files, .exe files, a .ink, a .cab, and unreadable files), and one contained 1358 items -- .cat files, .mum files, .manifest files, and folders with long names (containing .mui, .exe, and .dll files, with some others thrown in).  The names of these last files and folders had many references to Windows Media Player (which I never opened).

So I get that those files are probably irretrievable.  Here are my two problems.  First, the total size of the corrupted files is much smaller than their original size -- 3.8 MB.  But the space they took up is still being counted as used as reported by both Vista and Ubuntu.  How do I get it back?  Will it magically reappear if I delete the files from Ubuntu?  Or run a disk scan?

Second, If I boot into Vista and plug in my external hard drive, will all the files I wrote to the drive (or altered) while booted into Ubuntu die the same fiery death?  If not for these two things, I'd just delete the mess, boot into Vista, copy the files again, and be done with it.  But if I lose the copies on the external hard drive, they're **really** gone.

I have no idea what actually happened.  I've transferred files here and there from my Ubuntu partition to my Vista partition, and they all worked fine (some picture files, a few .docs and .pdfs).  Help please?  :confused:

I attached the output of ls -g -G -R in case the file and folder names are relevant... if not you can skip that part.  Please don't judge my taste in music.  :lol:

---

### Post by robsoles on 2010-11-04
Welcome to UF.


Sorry to say that I don't know what has happened to your files as an absolute certainty, I am responding to let you know that I have heard of this behaviour before though.

I've the impression that MS Windows (after and including Vista) destroys the files while it is booting or as you go to access them because they don't match the last picture the OS had of the folders you put them in.

It might be done in the name of defending the user from bizarre boot processes that write a bunch of files as part of an attack, it may be that Ubuntu/Linux handling of NTFS is a little off and it could just as well be something I would never think of :(

I personally think it is an over-zealous defence mechanism care of Microsoft, it doesn't seem to be present in XP but I've seen Windows 7 do it to a friend of mine and yours is about the fourth time I've heard of it via the internet - where you say you checked them from Ubuntu after moving them and they were fine, checked under vista they were gone, checking back in Ubuntu they are broken...

TIP: Always **_copy_**, always confirm the destination files are intact using the destination OS and only when completely satisfied remove the originals - sorry I'm a little too late for 10Gb of your stuff!


Did you copy the files to somebody's folders (ie., under "%windrv%\documents and settings\...") or to a folder you made in the root of a drive (ie., under "C:\MyTemporaryFolder")? (If 'to a folder you made in root', did you do create it while logged into Vista?)

---

