---
title: "Android micro-SD-card accessed by FTP does only show part of the content"
date: 2016-12-28
forum: Networking &amp; Wireless
---

### Post by Roland_Msl on 2016-12-28
Since years, I connect by FTP to the micro-SD-card of my smartphone.
The FTP is created on the smartphone by ES-file-explorer.

On my Linux system by mnt or in Nautilus by connect to server.

Last week, I changed from Android 5.1 to Android 6.

Now I see by FTP only a part of the files on the micro SD card.
The micro SD card is FAT 32 formatted.

Smartphone - ES file explorer: all files shown
Linux notebook access by FTP: only a part of the files shown
Linux notebook, the micro-SD card inserted with an adapter into the SD-card slot: all files shown.

I realized the problem while making a backup with Lucky Backup

Lucky Backup deleted several thousand files, because they do not longer exist on the original.
So I compared and found, that this files are not shown to exist when accessed by FTP.

Any idea?

---

### Post by praseodym on 2016-12-28
Lets try:

```
sudo apt-get install mtpfs mtp-tools gvfs-backends gvfs-fuse 
```

---

### Post by Roland_Msl on 2016-12-28
Just tried this.

Same problem. Only a part of the files on the micro-SD-card are shown.
After F5 refresh in Nautilus for the connected FTP.

---

### Post by Roland_Msl on 2016-12-28
Just tested to put the 128 GB micro SD card in my old Android 5.1 smartphone.
After start ES-file-explorer Network Remote start FTP

All is shown on my Linux notebook.

Than I put again the micro-SD card in my new Android 6 smartphone

After start ES-file-explorer Network Remote start FTP

only a part of the files shown.

---

### Post by ajgreeny on 2016-12-28
The card is probably formatted as exfat and you may need to install **exfat-utils** and **exfat-fuse** packages, though without them I would not expect anything to show at all.

EDIT:
I think I misunderstood your problem so you may need to ignore this post.

---

### Post by Roland_Msl on 2016-12-28
No, the card is formatted FAT32.
As I purchased the 128 GB card, my earlier Android 5.1 smartphone could not read exFAT. 
So I formatted the card as FAT32.

---

### Post by Roland_Msl on 2016-12-29
I discuss this also in a German Android forum.
Because of this, I tried to use the app "FTP server" instead of "ES-file-explorer"
It shows exactly the same problem when I look on my notebook by FTP on the micro-SD-card in my smartphone.

---

