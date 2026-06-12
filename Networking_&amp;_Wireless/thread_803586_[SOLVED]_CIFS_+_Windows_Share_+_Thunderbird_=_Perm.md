---
title: "[SOLVED] CIFS + Windows Share + Thunderbird = Permission Problem"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by PaganBlasphemy on 2008-05-22
Hello, I'm ready to take a hammer to my laptop...

I'm using Hardy Heron, re-installed it about a week ago.  Quickly got everything set up the way I like as I made a short list, and things have been going smoothly, except recently I noticed Thunderbird is unable to compress my mail folders.

As I began to dig, I found out the reason I couldn't compress the folders is that I have a weird permission problem.  

This is the appropriate line in my /etc/fstab:

```
//192.168.8.30/Mail   /lan/mail   cifs   credentials=/root/.smbcredentials,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

This works apparently fine for everything else I'm doing (other shares/programs). 

I almost hoped the problem was not having the 'nounix' flag, but that didn't fix my problem, even though it sounded *very familiar*: [http://ubuntuforums.org/showthread.php?t=800313](http://ubuntuforums.org/showthread.php?t=800313)

What I see is all of my files are owned by the root user/group, and have the correct permission (read/write for user, group and others), including my Inbox.msf file. **When I open Thunderbird however, it changes the permission of the .msf files to read/write for the root user only, read only for the group and for others.**  So, I take a gksudo nautilus and fix it back, but Thunderbird (or something) immediately changes it back. 

I don't see how this could be possible, but it is what I am seeing :confused:

From what I've gathered in a confused manner, Ubuntu isn't really setting the permissions on the files (as they are hosted on windows machine) but instead setting something (incorrectly) locally apparently.

All I know is that I'm ready for Something That Just Works...I don't have any hope that anyone can help me, I'm just throwing my experience out there in case someone else has seen this and wants to take comfort in shared grief.

---

### Post by PaganBlasphemy on 2008-06-11
This problem ended up being on the Windows side of things.

I noticed that if I added my windows user as having full permission directly of a directory or file that was giving me problems inside the share, It Would Just Work.  Some time between when I created the original share and now apparently something Got Broken on my Windows box with regards to that share and its permissions.

So, I just created a new folder, moved the contents of the original share over to the new folder, deleted the old share, renamed the folder and recreated the share.  It looked (on the surface) identical, and Ubuntu accesses it identically, but now It Just Works.

I guess something wasn't recursing correctly down through the share for some reason.

Not at all anything wrong on the Ubuntu end!

---

