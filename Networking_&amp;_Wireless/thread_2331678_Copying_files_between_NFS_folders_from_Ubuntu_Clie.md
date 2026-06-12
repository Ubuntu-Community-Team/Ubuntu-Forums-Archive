---
title: "Copying files between NFS folders from Ubuntu Client"
date: 2016-07-24
forum: Networking &amp; Wireless
---

### Post by xkalibur on 2016-07-24
I have a folder share from my Synology NAS server that was mounted as a NFS folder on my Ubuntu MATE client.
I think I lost some files while moving files from one folder in that mounted path to another folder inside that same mounted path.

**The scenario is like this:**
[LIST]
[*]I started to copy some photos that I've taken from one folder inside this mounted share to another all while using Caja.
[*]What I noticed was that Caja didn't show **file copy progress** even when I did several folders at once. 
[*]The folders appear right away to the new location and since these were just in JPEG format I figured it was a fast transfer and was done.
[*]However when I open the folder not all the files are there.. Eventually for most of the folders, the JPEGs and RAW appeared.
[*]I also want to mention that I started renaming the folders to match the date the grouped photos were taken.
[/LIST]


Afterwards I noticed one folder has 0 files contained inside. 
Performing in a terminal: "ls -l" also shows nothing inside the new folder. When I look at the old location, the folder is no longer there (it was moved from that location).

So I think I lost files inside the folder during this transfer and renaming. I'm 99% sure, not 100% because I didn't have a backup.
Afterwards I made sure to backup all my family photos to ensure nothing else like this happens in the future.:mad:
[B]
My questions are:[/B]
[LIST]
[*]Is there anyway possible I can recover the folder?
[*]How can I modify CAJA to show file progress (would be handy in the future)..
[*]Are there any logs I can look for to see if the folder had contained and lost some files?
[*]Should I stick to terminal for file transfer in the future?
[/LIST]


Thanks in advance!

---

