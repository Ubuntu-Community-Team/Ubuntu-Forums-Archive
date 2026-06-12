---
title: "Wine-No-Cd-ROM Drive found"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Bellator777 on 2011-08-25
I'm fairly new to Ubuntu and a program named Wine. I'm trying to play KotOR2, but whenever iI try to play it, a box pops up that either says "No CD-ROM drive found" or "No CD inserted". Please try to answer in simple terms. I'm not too good with computers lol

---

### Post by flurospar on 2011-08-26
Does the game require a CD to be inserted for playing. Insert the CD, and then press Alt+F2, when the window appears, type "winecfg" (no quotes). You might see a tab called drives in the Wine configuration window. Open the window and see if the CD is mounted as a drive in the list. If it isn't, open the CD from the icon on the desktop and copy the location of the CD drive from the text box that opens after you click Go > Location in Nautilus. Add this as a drive on Wine configuration window.

If the disc is copy-protected (as most game CDs are), Wine cannot always handle it well, It might not even read the disc, but that depends on the Wine version.

---

