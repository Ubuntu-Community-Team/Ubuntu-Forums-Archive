---
title: "Samba gives back not enough space while that's not the case"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by spam7 on 2014-01-05
Hi,

I'm running Ubuntu 13.10 minimal with 2 harddrives ext4 formatted.

When trying to copy files from my Macbook to my Ubuntu machine I'm getting the error there's not enough space available.
I tried to google this problem and found out it has been a bug for NTFS systems but not for ext4 disks.
The problem occurs on both hard drives.
I haven't changed the config except for adding a user.
Share has been set to path / so I can access everything with just 1 share.

The drive has 800GB free space so it's not nearly full.
Any suggestions that might solve this?

Thnx.

**EDIT:** I can copy a .mp4 file of 163MB but a .mkv file of 323MB is too big according to samba

---

### Post by TheFu on 2014-01-05
I don't know the answer, but have a few ideas ...
[LIST=1]
[*]What do the log files say? - Always check the logs 1st!
[*]If you run the command from the CLI Samba Client , smbclient, with verbosity turned up, what messages are displayed?
[*]Have you tried using the gvfs method? That happens automatically with most *File Managers* now.
[/LIST]

Does either /var or / have less than 323MB of space?  Perhaps a temporary file is being used?  Use **sudo lsof** to find where that file might be.

---

### Post by spam7 on 2014-01-05
Weird. I gave it a try with a cp command in terminal and that seems to work just fine.

---

### Post by TheFu on 2014-01-05
> **spam7 said:**
> Weird. I gave it a try with a cp command in terminal and that seems to work just fine.

I've been burned over 2,000 times using GUI stuff rather than the CLI over the last 20+ yrs.
If you would please, state which GUI tool you were trying?

---

### Post by spam7 on 2014-01-05
Finder, build-in file browser in OS X. (Mavericks)

---

### Post by TheFu on 2014-01-05
> **spam7 said:**
> Finder, build-in file browser in OS X. (Mavericks)

Sorry, the last time I used OSX, there was a bug in their CIFS/SMB implementation that prevented any connection to work at all.  Access and transfers between Windows and Linux in either direction worked without any issue ... and still works here on all may 12.04 boxen.

How are the disks formatted?  Which file system on the source and the target is being used?  HFS or NTFS involved?

I see this is marked as "solved" now.  What was the root cause?  Please post so that others can learn too.

---

### Post by spam7 on 2014-01-06
The problem by GUI isn't really solved but my main concern was to copy the files to the network disk and I've succeeded to do so by using the cp command in terminal.

To be complete, my source disk is formatted MAC OS Extended (journaled) and the destination disk is formatted as EXT4.
I guess it's just some sort of bug in OS X since it works when I perform the same action in a different way.

---

