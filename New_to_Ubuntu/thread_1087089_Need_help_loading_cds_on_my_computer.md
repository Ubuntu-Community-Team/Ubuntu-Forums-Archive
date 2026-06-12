---
title: "Need help loading cds on my computer"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Stringsnharps on 2009-03-04
Why can't I load cds on my computer since I switched to ubuntu?
Stringsnharps

---

### Post by avtolle on 2009-03-04
What do you mean by "can't load cds"? Do you get any error messages, and if so, what are they? What kind of cds are you trying to load (data, music, isos)?

---

### Post by Dougie187 on 2009-03-04
If its music cds, just open up rhythmbox and import your cd. Otherwise it should just be a data file you can put on your desktop, or you can rip an ISO using brasero.

---

### Post by dannyboy79 on 2009-03-04
after you put the cd into the drive (by the way, what kind of a drive is it, please post back what this command returns ```
dmesg | grep CD
``` OR
```
dmesg | grep DVD
```
does the drive light light up and can you hear the disc spinning? If it's a music cd, Sound Juicer should automagically popup wanting you to rip the music from the cd into mp3's. If it's an cd with an iso on it, you may have to mount it manually using the command line.
Do you have an entry in your /etc/fstab file for your DVD or CD drive like this?
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto  0     0
NOTE: you can make the mount point something other than /media/cdrom0 just make sure the permissions on the mount point are like this:
drwxr-xr-x
Also, you may have /dev/dvd or /dev/dvdrw which is a symlink to the actual drive. For example /dev/hdX or /dev/scdX or something like this.

---

### Post by Mud.Knee.Havoc on 2009-03-04
If you switched from Windows to Ubuntu, your CDs may not be working because Ubuntu is a different operating system.  Your old software is written for Windows, not linux, so much of it won't work.*

If you put a CD in the drive, though, the disc's contents should be displayed (regardless of which OS the disc is for).  Does this work?  What exactly is your problem?

*-It is possible to use a program called wine to run Windows programs in linux, but it doesn't always work perfectly (or at all, in some cases).

---

### Post by Stringsnharps on 2009-03-07
I have a few cds that have text / manuals on it that I would like to load onto ubuntu and have ready access such as desktop or folder but I cannot seem to figure out how to get the data off of the cds onto ubuntu so that I can click on and read. I used these same cds when I had vista but that OS crashed so I quickly downloaded and installed ubuntu as I need computer access and I did not want to go back to vista.
What happens when I put the cd in is: the drive spins and then a window appears with icons showing setup, and a few other icons. I have tried several times clicking onto each one and the drive spins for a little while and then stops but no automatic loading or bringing up the contents of the cd. Please excuse me as I am very new to ubuntu and maybe I am missing a task. I have read that some things need to be mounted using a terminal but I have no clue what that means. If someone can walk me through this I would appreciate it as I have several cds that are text based that I like reading and would like to be able to do so using ubuntu.

Thanks,
Stringsnharps

---

### Post by mike555 on 2009-03-07
If these are text files you should be able to drag and drop them onto your Ubuntu desktop , then into what ever folder you want (documents?) if your trying to open them you should be able to, check their extensions (you know , the .txt or .doc at the end of the text files title) if they are some goofy Windows format that requires a Windows program , you might have a problem .....  if you want to you can type the extension into your browser search box and it should tell you which programs it works with ......
  or just ask us here , and we will try to help.....

---

### Post by Stringsnharps on 2009-03-07
Hi, I seem to be having trouble getting my cd to load onto ubuntu. The cd's are text /manuals that I used when I had vista and would have them saved to my desktop so that I could always open it and read. I don't seem to be having any luck with ubuntu. I am new to this OS so maybe I am not doing something right. When I put the cd in the drive it spins and then opens a window with icons such as setup, etc., but when I click onto them the cd drive spins and the program or wizard does not open.If you can walk me through this I would appreciate it. Right now I am very frustrated.

---

### Post by mike555 on 2009-03-07
Sounds like you are trying to install a Windows program on Ubuntu, "setup" is usually a Windows install....

---

### Post by Stringsnharps on 2009-03-08
Hi everyone,
Since I have downloaded and installed ubuntu I do not know how to go back and retrive files and photos from vista? I checked off the box for partician but I am not sure it worked. Is there a way I can retrive my old files and photos and load on ubuntu?

---

