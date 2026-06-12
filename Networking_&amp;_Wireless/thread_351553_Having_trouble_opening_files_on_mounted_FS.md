---
title: "Having trouble opening files on mounted FS"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by craig0ry on 2007-02-02
Hello! First of all, please forgive me if this is more appropriate for the newbie section. The problem I have been butting up against all night is this -

I have Samba installed and properly configured (I believe).
I use the GUI to navigate to my shared folders on my XP box and mount them.
At this point they show up as SMB mounts on my Ubuntu desktop. I can open them, navigate around, copy files, etc.
If I copy a file FROM the share TO MY UBUNTU box, it will open and play fine (MP3, AVI, etc.)
However, if I try to open it directly from the SMB mount, it will just open VLC and sit there not playing back anything; I get similar results with Amarok and Totem.

This is a big problem for me - with XP I can simply navigate to shared folders on my network and open files from them without having to copy over to my hard drive. I have done tons of searching on this subject and it seems that tons of us new converts to Ubuntu and other Linux flavors have a lot of trouble with this. I cannot seem to find a solution however, but this capability has to be there somewhere. 

Can someone explain to me, as if they were talking to an 80 year old who had never seen a computer before in their life, what I am doing wrong and what I can do to get these programs to open files without having to copy them to my hard drive?

Thank you so much in advance, I have been pulling my hair out over this! 

Much appreciation,
-Craig

---

### Post by whoismilan on 2007-02-08
How are they mounted?

I think I have a similar setup as you, and I noticed that if I go to the folder by just browsing to smb://servername/sharename, things don't work, but if I mount them in a folder just like a regular partition, things work fine.

This is how I am mounting my shares:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

