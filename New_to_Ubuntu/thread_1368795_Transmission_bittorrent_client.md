---
title: "Transmission bittorrent client"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by suniyo on 2009-12-31
My transmission bittorrent client crashed and some data was removed/missing (2.5 GB worth). Now my disk usage analyzer shows it as removed and gives me free space about 3GB, but I receive warning about low space that is equal to something around 500MB.

Where those missing bittorrent files are stored as my tmp directory is shows only 200 kb and default download location for transmission is not showing the files even when show hidden files is enabled. Any ideas?

---

### Post by suniyo on 2009-12-31
I've reinstalled baobab gnome-utils. it doesn't make any difference.

---

### Post by candtalan on 2009-12-31
Check the wastebasket in your account.
Also it is maybe possible (??) that the files are somewhere in the root account, including its wastebasket. Not sure. 
And of course, be aware that hidden files (with a leading '.' ) cannot be seen unless you ask for their view.

hth

---

### Post by Paqman on 2009-12-31
Launch the Disk Usage Analyzer as root using this command:
```
gksu baobab
```

It should help you find where your files have gone.

---

### Post by suniyo on 2009-12-31
> **candtalan said:**
> Check the wastebasket in your account.
Also it is maybe possible (??) that the files are somewhere in the root account, including its wastebasket. Not sure. 
And of course, be aware that hidden files (with a leading '.' ) cannot be seen unless you ask for their view.

hth

I have checked all the hidden files they are not there, may be there is some bug in transmission client. My trash is empty and there are no files in trash including hidden ones, this is bit strange as I lost data but it still is there somewhere on my disk or may be it is just in the filesystem and not actually on the disk. How can I check that?

---

### Post by suniyo on 2009-12-31
> **Paqman said:**
> Launch the Disk Usage Analyzer as root using this command:
```
gksu baobab
```It should help you find where your files have gone.

After running this from terminal it also shows exactly the same amount of free space available 2GB and still pop-up notices come. Now it is just 50MB free as my downloads are running but I am not facing any difficulties yet. System Monitor says everything is okey. 50% RAM and 10% of CPU usage. 

So may be there is some problem with the filesystem due to the transmission bittorrent client crash.

---

