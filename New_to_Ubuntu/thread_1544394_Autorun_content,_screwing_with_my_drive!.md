---
title: "Autorun content, screwing with my drive!"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Covertoddity on 2010-08-02
This problem has persisted for several weeks, I have a second hard drive  that I use to store my downloaded files named "Spinning" and I needed  to mount a 6.4 gb game iso on it so I downloaded the mount and unmount  scripts from an ubunutgeek tutorial. Unfortuneatly the unmount script  would not work at all or even show up so I just delted the mounted iso.  Now, when I open my drive up it shows the below window and when clicking "run" it says it can't find the autorun file and cancel does nothing[IMG]http://www.use.com/images/s_3/4b8bafa16a8515002514.jpg[/IMG]
I have tried messing with alot of autorun setting but nothing works,
 thanks in advance

---

### Post by beew on 2010-08-02
I could be wrong, but I think the .inf file for auto run is a windows file and it wouldn't be executed in Linux.  The autorun prompt will show up regardless but you can change it in file system > edit > preference > media. It seems that  the .inf file would not  run in WINE, seems to be a security thing..

I tried the script, umount doesn't seem to work. You have to go to the terminal and cd into the directory where the iso is mounted and type ```
sudo umount isoimage
```You can try gmount-iso from the repo, you have to create a mount point (a directory to mount your iso) manually though. Also you can try furius iso  which takes care of the mount point automatically and can mount multiple isos, but I am not sure if you can choose your mount point if desired (say you want to set up a designated mount point for Windows app and map it to the cd rom drive in WINE)

---

### Post by Covertoddity on 2010-08-02
See, the problem is, I no longer have the .iso that was mounted (deleted) so I don't see how I can unmount it. 

:(

---

### Post by Covertoddity on 2010-08-08
Sooo, does anyone want to shed some light on this?

I really need to unmount this iso that I deleted, this is seeming impossible to me right now. 

Maybe Could I disable autorun altogether?

thanks

---

