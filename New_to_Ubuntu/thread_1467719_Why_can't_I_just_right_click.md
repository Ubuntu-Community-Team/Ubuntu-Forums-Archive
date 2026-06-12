---
title: "Why can't I just right click?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by 5systems on 2010-05-01
I am new to Ubuntu... well fairly new in that I have been trying and trying to use it for a while now and I find myself getting frustrated. 

I just loaded ubuntu and I am tying to map a network drive  and can't seem to do it through the GUI. 

Is there such a way to do this using the GUI?

the second thing is my nas came with a disk and there is a LInux folder to just load the utility that will suposedly map them to the system, however when i click the setup file it tells me the following: 

Could not open the file /media/Solutions/Linux/setup.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.:confused:

---

### Post by ugm6hr on 2010-05-01
What kind of Network Drive is it?

If it is a Windows Share, you should be able to access it in Network Places.

A reasonable alternative is the software called Gigolo, which is in Xubuintu.

---

### Post by Paqman on 2010-05-01
Unfortunately this is one of the things that Ubuntu isn't terribly good at. While the share should be accessible through Network Places as ugm6hr says, it won't be automatically mounted at boot, so if you're connecting a whole bunch of apps to data stored on the NAS (eg: your music collection) then you'll need to set it up in a bit more involved way.

It looks a bit complicated, but it's actually pretty straightforward once your get your head around what's going on:

[How to permanently mount Windows shares through fstab]("http://ubuntuforums.org/showthread.php?t=288534").

---

