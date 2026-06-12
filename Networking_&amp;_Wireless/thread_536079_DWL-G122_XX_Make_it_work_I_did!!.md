---
title: "DWL-G122 XX Make it work I did!!"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by Gage_AB on 2007-08-27
If you have a windows parition, that's great. Otherwise, this guide should still work. I installed the card using my windows partition, but I put the files I used on a website for those of you that don't have xp installed. These will probably work, but no guarantees. I believe you can get to the same files by clicking on the first link.

Step 1
If possible, install the card on a Windows XP partition.

Step 2
Install ndiswrapper via synaptic. The two packages I had installed were ndiswrapper-common and ndiswrapper-utils-1.9.

Step 3
Now look in your windows partition for prisma02.inf. I did a file search for this, mine was located in /../windows/inf/prisma02.inf. Enter the directory that the file is in and run the command
Code:
 ndiswrapper  -i  prisma02.inf
For me, this created the directory /etc/ndiswrapper/prisma02 which had 4 files in it: 045E:00C2.F.conf, 2001:3701.F.conf, 09AA:1000.F.conf, prisma02.inf. Some people may only have 2 files: 2001:3701.F.conf, prisma02.inf.

Note: If you don't have a windows partition, try using the files from the first link or the files I used here. No guarantees on these though. I suspect it would only work for the B1 revision of the card. If your not sure of your revision, check the back of your card for where it says H/W Ver. Any feedback on if these work would be appreciated, they may even make a few other steps unnecessary.

Step 4
When you run the ndiswrapper command, it does not find 2 of the files. Add 2 copies of each of these files to the directory /etc/ndiswrapper/prisma02; one copy with all lowercase and one copy with all uppercase letters (except for the extension). The first file is prisma02.sys (mine was in /../windows/system32/drivers/) and the second is prismapi.dll (mine was in /..windows/system32/).

The directory /etc/ndiswrapper/prisma02/ should now have the following files in it
Code:
dan@dan-deskbook:/etc/ndiswrapper/prisma02$ ls
045E:00C2.F.conf  2001:3701.F.conf  prisma02.sys  prismapi.dll
09AA:1000.F.conf  prisma02.inf      PRISMA02.sys  PRISMAPI.dll
Note: Again, if you don't have a windows partition try the files I uploaded or the ones from the first link.

Step 5
Now, we need to disable the original ubuntu drivers that didn't work. To do this, open up the blacklist in gedit
Code:
sudo gedit /etc/modprobe.d/blacklist
Add the following lines to the file
Code:
blacklist islsmusb
blacklist islsm
blacklist islsm-usb
blacklist prism54usb
Step 6
Plug in, reboot, and you should be good to go.

---

