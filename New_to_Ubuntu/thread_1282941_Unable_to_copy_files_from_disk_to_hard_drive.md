---
title: "Unable to copy files from disk to hard drive"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by protoguy on 2009-10-05
Hi all, My son just got me started with ubuntu 9.04 then went off to college. So I am on  my own.  I have been reading the ubuntu pocket guide, and now feel like I am ready to try things out, or screw things up.  :P
My first project, beyond the standard web surfing and emailing, was to see if I can play some of my old games. I installed wine and found instructions on how to make generals work.  One of the first steps was to copy the disks on to the hard drive, and there is where I run into the first problem. I put the disk in the diskdrive and right click on the symbol on the desktop. I clicked on create archive. I went with the default selections "GENERALS1.volume" ".tar.gz" and my location "david" i then clicked create and got the following message:
An error occurred while adding files to the archive.

The specified location is not supported

not supported? what does that mean? I changed the name and tried different file types, but get the same message.

---

### Post by nhasian on 2009-10-05
i dont think you want to create an archive.  that creates a compressed file for storage.  you can create a folder then copy/paste the contents of each CD into the folder.  (i'm guessing when you mentioned disks you were talking about CDs not floppy disks)

rather than copying files, can you not just open the cd and run the setup.exe file with wine?

---

### Post by protoguy on 2009-10-05
Here are the first 3 steps of the instructions I got from the wine website:

1. Download msvcirt.dll and put it in your .wine/drive_c/windows/system32 directory
2. Copy both CD's to your harddisk into the same folder.
3. Install Command & Conquer Generals from your harddisk using wine setup.exe.

The file already had the msvcirt.dll, so I did not have to do that.  They said, because there are 2 CD's it will not prompt for the second CD and will end with an error. I am also unclear on how to run the wine setup.exe and not the setup.exe that is on the CD. Does wine automatically sub it's setup.exe for the one on the CD?

And this is just the first 3 steps, the ones I thought I understood. After this I am really clueless. But hey, gotta start somewhere. :)

---

### Post by sgosnell on 2009-10-05
Just run the setup.exe that's on the CD.  If Ubuntu doesn't recognize it, select wine as the program to open it.

---

### Post by hashimoto on 2009-10-05
OK, so the game is on two disks?
1. Create a folder in your home directory with an approproate name e.g. "Game"
2. Insert disc n.o 1 and open it by clicking the icon on the desktop
3. In the opening window, select all files & folders by pressing Ctrl+A (Ctrl and a at the same time) and then copy them by pressing Ctrl+C
4. Open the created folder "Game" and paste the files by pressing Ctrl+V
5. Remove the disc n.o 1
6. Repeat points 2 to 5 for disc n.o 2
7. In folder "Game" doubleclick the setup.exe (or install.exe) and let Wine install the game
8. Play. Game can be found in Applications - Wine - Programs -...

---

