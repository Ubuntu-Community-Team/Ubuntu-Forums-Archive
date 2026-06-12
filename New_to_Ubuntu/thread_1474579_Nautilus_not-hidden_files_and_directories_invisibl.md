---
title: "Nautilus: not-hidden files and directories invisible."
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Blodskaal on 2010-05-06
Hello,

I'm new to Ubuntu. I installed it a few weeks ago from the (then) latest Ubuntu Desktop CD. I run Ubuntu on a HP EliteBook 8530w. I bought the laptop half a year ago, it was preinstalled with Vista. I upgraded to Windows 7 as soon as possible. When I installed Ubuntu I shrunk the NTFS partition to make room for it. As my documents folder I still use the windows documents folder (/windows/Users/Myname/Documents/).
I use nautilus to browse my files.
I'm doing a practicum at the university and I noticed some files & folders I needed were missing. The folder with missing sub-folders and files is on my NTFS partition. I created a new folder, and intended to re-download the files. After I renamed the folder I decided to try something. I hit F5 (refresh I thought) and the folder disappeared. I then started a terminal and cd-ed to the folder. dir showed me the all the missing files and folders.
I can access my files via the terminal when I really need them, but it's still annoying. Does anyone know a solution to this problem?

Thanks in advance for your troubles,

Blodskaal

P.S. I found out afterwards that Ctrl + R is the reload button in Ubuntu. Maybe the functionality of F5 is 'hide files from the hapless n00b'?

---

### Post by false_chicken on 2010-05-06
Ctrl + H Will toggle the showing of hidden files. Do you see them after doing that?

---

### Post by Blodskaal on 2010-05-07
Thank you for your reply false_chicken,

I have hidden files visible by default.
I tried to make clear in the title that the invisible files are "non-hidden" files.
I booted my laptop in Windows 7 today to game, and I realized that the missing files were visible in Windows explorer. I now have another problem tough, when I try to use the folder in windows explorer: I cannot move files I created in Ubuntu to trash. It says "file missing or corrupted" and when I use "permanent delete" (Shift + Delete) the files reappear when I reload the folder. This has alarmed me a bit more than the previous problems, since I have used windows explorer and it's predecessors since I was a kid and never encountered any comparable error.

Regards,

Blodskaal


EDIT:

Hello everyone,

Today I booted in Windows 7 just to see if anything would happen. Windows automatically ran CHKDSK and removed all index entries of files I added to the NTFS partition from Ubuntu. I lost an annoyingly large amount of school files. I now think this issue has something to do with Ubuntu writing the NTFS index entries the wrong way. Does anyone have an idea how to fix this? Maybe even recover my lost files?

NOTE: This still doesn't explain to me why the files did show up in the Terminal in Ubuntu but not in Nautilus.

Thank you for your time,

Blodskaal

EDIT:

Hello everyone,

I tried to run Testdisk 6.11.3 on Ubuntu to undelete the files from the NTFS partition. The Testdisk freezes :(. I suspect the cause of my disappearing files might be the fact that I have on my ext4 partition several soft-links to my NTFS partition. I suspect that Ubuntu doesn't correctly register the partition changing or something. These are only wild speculations though, since I really don't know that much about data storage.

Thanks in advance for any help,

Blodskaal

---

### Post by Blodskaal on 2010-05-10
Editing is nice to avoid double-posts, it doesn't bump the thread apparently.
Sorry for the double-post.

B.U.M.P

---

### Post by krazyd on 2010-05-12
> **Blodskaal said:**
> When I installed Ubuntu I shrunk the NTFS partition to make room for it. 

This is almost certainly the cause of your problems. If the resizing is done incorrectly it can corrupt the partition.

I think you need to report a bug on launchpad, or search for one similar.

---

### Post by Blodskaal on 2010-05-13
Thanks for your reply Krazyd,

I however am already fairly convinced that the problem is in the way Ubuntu uses soft links. I noticed that all the files that were lost, were files that were saved to the NTFS partition through a soft-linked directory in the ext4 partition. I removed the soft links, and any subsequent saves have behaved normally. I noticed that when I soft-link a directory in Ubuntu it behaves like a hard-linked directory behaves in Windows. Apparently when you do this across partitions of different types, this causes Ubuntu to write the indexes in the wrong way.

I consider my problem solved, however it might be nice to see a more reliable form of directory linking in a future release of Ubuntu,

Blodskaal

---

### Post by krazyd on 2010-05-14
> **Blodskaal said:**
> I noticed that when I soft-link a directory in Ubuntu it behaves like a hard-linked directory behaves in Windows. Apparently when you do this across partitions of different types, this causes Ubuntu to write the indexes in the wrong way.

Interesting. This could be a bug in symlinking in general. It could be that the developers aren't aware of this issue.

The NTFS-3g forums are located here: [http://tuxera.com/forum/](http://tuxera.com/forum/)

I'm sure they would be interested in your problem, and probably be able to give you an explanation for the behaviour at the very least! :)

---

### Post by Ozymandias_117 on 2010-05-14
I'm wondering if this could have something to do with Windows 7 using a new version of NTFS... Perhaps the current drivers in Linux can't fully handle the new NTFS? I know there are lots of files I'm unable to delete on a Windows 7 formatted disk. Just something to think about.

---

### Post by Blodskaal on 2010-06-11
Noticing this old thread of mine didn't have a conclusive ending, I'll share what I learned from this experience.

Don't symbolic-link from an NTFS-3g partition to a Ext4 partition (and maybe vice versa). Files created/stored trough the link will kind of behave like 'heisenfiles' being visible except when you are trying to observe them.

Don't hibernate Windows and then access the NTFS-3g partition from Ubuntu. Files stored in that way will trigger CHKDSK upon resuming Windows and their entries will be removed, causing the data to become inaccessible. I had no luck in trying to 'undelete' it  with testdisk.

---

