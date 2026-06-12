---
title: "Blank Screen after upgrade to Ubuntu 10.04 Lucid"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-14
I upgraded to Ubuntu 10.04 via terminal but now I get a blank screen upon rebooting. What do I do, I read somewhere the issue had to do with the graphics card so I went to BIOS utility set up & gave that as my 1st booting option but I still get a blank screen, pls suggest what I should change under BIOS utility to remove the blank screen.

---

### Post by patC42 on 2010-09-14
I had the same problem when I upgraded from 9.04 to 9.10. I had the root and home on separate partitions and when I upgraded and booted back in I just got a blank white screen.

It was suggested that this was because I had desktop effects activated on the old distro and that there was trouble with the video drivers. But I didnt know how to correct this so I did a fresh install using a usb stick on the root partition and pointed the fstab to the old home partition. And now I have everything back again in the new version.
So if you can move the contents of your /home to a new partition then everything can be saved.

---

### Post by patC42 on 2010-09-14
**[Move /home to it’s own partition]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") 	*January 29, 2006***

This is the information that I found useful
As you can see its 4 years old but its a start.
Good luck.

---

### Post by Suzanne42 on 2010-09-14
I dun think that's the solution 4 me, I cleared my entire disk before installing Ubuntu 9.10, the issue is my graphics card-Nividia. Apparently it conflicts with Ubuntu 10.04 Lucid.

---

### Post by Rubi1200 on 2010-09-14
It sounds as if this may well be a graphics issue.

Try booting with the workarounds mentioned here:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

To edit the GRUB menu, highlight the entry and hit "e" find the line with quiet splash and replace with nomodeset then "Ctrl" + "x" to boot.

---

### Post by Suzanne42 on 2010-09-14
Anyways I put comp in recovery mode & tried 2 fix broken files, it did no use so now m back 2 square one with Ubuntu 9.10. Qn is shud I try upgrading via Update Manager?Will it be flawless, if m again faced with a blank screen or unable 2 reach my desktop after upgrade I dun see the point.

---

