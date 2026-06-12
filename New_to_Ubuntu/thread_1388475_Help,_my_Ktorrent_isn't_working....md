---
title: "Help, my Ktorrent isn't working..."
date: 2010-01-23
forum: New to Ubuntu
---

### Post by ribozyme on 2010-01-23
I'm not familiar with the technical aspects of programs. Anyway I have installed Ktorrent from KDE windows installer and it worked nicely. I have followed the directions. I have downloaded from a few .torrents. The last time I was using it, there were two .torrents on download, I added a third and during pre-allocation of memory space Ktorrent stopped working. So I tried to open Ktorrent again but it did not work anymore. I tried to restart my laptop, remove a few files from my documents to accommodate the 3Gig required for the last .torrent file I entered, but the same result, Ktorrent failed to run. I made a re-installation of that version of Ktorrent and the same result, it did not work. I deleted the last file (from the download files) corresponding to the third .torrent it tried to preallocate memory with, and I noticed that every time I attempt to run Ktorrent, the file reappears. There's something about the file or my laptop, maybe, that do not remove the last .torrent queued, and Ktorrent keeps on trying to process this but fails and thus a dialogue box instead appears saying: "ktorrent.exe has stopped working..a problem cause the program to stop working correctly. Windows will close the program and notify you if a solution is available."

How can I remove that last .torrent I entered, or how can I make Ktorrent run again?

thanks.

---

### Post by Ant59 on 2010-01-23
Try:

```
sudo apt-get purge ktorrent
sudo apt-get install ktorrent
```

**EDIT: Sorry, just realised you are on Windows. I have no idea how to help in this case, sorry.**

---

### Post by ribozyme on 2010-01-23
Thanks anyway. I guess, this isn't the proper place for that specific Ktorrent problem,  I apologize, but I do wish that the problem be solved in less time because I will needing to download a lecture at .torrent, thanks.

---

### Post by Ant59 on 2010-01-23
I tried the KDE bug tracker, but there are no bugs found for KTorrent under MS Windows on there.

---

### Post by ribozyme on 2010-01-23
I found a way just now. I uninstalled Ktorrent, deleted KDE folders at C:\User\AppData\Roaming (scary, I might have deleted important files) and reinstalled Ktorrent. It worked. Maybe in the future, I don't have to uninstall but look into these folders. Ktorrent is running again. Whew!

---

### Post by lovinglinux on 2010-01-23
> **ribozyme said:**
> I found a way just now. I uninstalled Ktorrent, deleted KDE folders at C:\User\AppData\Roaming (scary, I might have deleted important files) and reinstalled Ktorrent. It worked. Maybe in the future, I don't have to uninstall but look into these folders. Ktorrent is running again. Whew!

Yes. That folder is where Ktorrent saves settings and the state of each torrent. Once you delete it, you reset Ktorrent to default state.

---

