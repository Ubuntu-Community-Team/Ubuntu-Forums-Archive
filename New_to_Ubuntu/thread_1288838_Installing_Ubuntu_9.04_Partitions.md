---
title: "Installing Ubuntu 9.04 Partitions?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by marcelluspye on 2009-10-11
I am trying to install Ubuntu 9.04 on my old 2003 Dell Dimension 2350, and have slowly gotten to the parts with the partitions (Steps 4 & 5). I have checked the space in Windows, and it says I have 20+ GB of space free. In Step Four, it says Windows is taking up 55.8 GB, and there is 23.5 MB of space free. I do not want to erase Windows, and I do not know where the 20 GB of space is. How do I install this?:confused:

---

### Post by yeats on 2009-10-11
> **marcelluspye said:**
> I am trying to install Ubuntu 9.04 on my old 2003 Dell Dimension 2350, and have slowly gotten to the parts with the partitions (Steps 4 & 5). I have checked the space in Windows, and it says I have 20+ GB of space free. In Step Four, it says Windows is taking up 55.8 GB, and there is 23.5 MB of space free. I do not want to erase Windows, and I do not know where the 20 GB of space is. How do I install this?:confused:

You'll need to shrink the Windows partition, which you should be able to do from the LiveCD.  Even though Windows shows the 20 GB as "free", it is still within the Windows partition.  If you shrink the size of the Windows partition, you will then have free space to create the Ubuntu partition.

---

### Post by marcelluspye on 2009-10-11
How do I shrink it? In step 3,  It shows /dev/sda1 as blue, taking up 31 MB's of space, XP, in Green, with 55.8 GB's of space, and Ubuntu 9.04, below, in Orange. It does not allow me to select "Use the largest continuous free space" because it is too small, and "Specify Partitions Manually" shows a large orange bar (Ubuntu?) filling up the bar. If I choose this and go to step 4, it gives me this

[CENTER] [COLOR=DarkOrange]------------------------------------------------Long Orange Bar on one line-----------------------------------------[/COLOR]

[COLOR=Lime][]sda1 (fat16)         [COLOR=DarkOrange][]sda2 (ntfs)            [COLOR=Black][]Free space
[/COLOR][/COLOR][/COLOR][LEFT][CENTER]                                    [COLOR=Lime]31.3 MB            [COLOR=DarkOrange]55.8 GB                           [COLOR=Black]23.5 MB[/COLOR][/COLOR][/COLOR]
[/CENTER]
 
Device       |Type  |Mount Point|Format?|Size          |Used
/dev/sda     |             |                                   |                       |                      |
  /dev/sda1  |fat16 |                              |         []         |32 MB       |32 MB
  /dev/sda2  |ntfs  |                                  |        []        |59962 MB |unknown
  free space|           |                                      |       []        |24 MB       |                     
[New partition table] [[COLOR=Silver]New Partition[/COLOR]] [[COLOR=Silver]Edit Partition[/COLOR]] [[COLOR=Silver]Delete Partition[/COLOR]]
[Undo changes to partitions]

the []'s are squares and the [text]'s are textboxes, the grey ones are the buttons it was not allowing me to push. What do I do?
[/LEFT]
[/CENTER]

---

### Post by yeats on 2009-10-12
Okay...  the program you need is called gparted and it *should* be on the Live CD.  If not, you can actually burn a separate disk:

1. Go to [http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

2. Go to gparted-live-stable -> 0.4.6-1 -> gparted-live-0.4.6-1.iso an click on that link to download.

3. Burn the .iso with the same program with which you created your Ubuntu disk.

Then follow these instructions for resizing:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

You might want to make sure your WinXP partition is cleaned up (defragged, extraneous files removed) since Windows tends to spread files out all over the disk.  You wouldn't want to write over something you need :-).

---

### Post by munkeh on 2009-10-12
[LEFT]Hi I have found a few of her videos to be really helpful, the following one maybe some help to you;

[http://www.youtube.com/watch?v=GhnLk3gviWY&feature=player_profilepage](http://www.youtube.com/watch?v=GhnLk3gviWY&feature=player_profilepage)

from about 1:29 should be relevant.

Hope it helps.
[/LEFT]

---

### Post by marcelluspye on 2009-10-12
Thanks man, I hadn't been looking in the Ubuntu Software.

---

