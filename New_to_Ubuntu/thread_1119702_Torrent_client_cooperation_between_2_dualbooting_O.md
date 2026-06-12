---
title: "Torrent client cooperation between 2 dualbooting OSes (XP/Ubuntu)"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by ydraliskos on 2009-04-08
Basically what I am trying to achieve is having either 2 different instances of utorrent "synced" between the 2 OSes, or the OSes using the same actual client.


So this would look like this:
You would start a torrent on Ubuntu, it would reach 30%, then you have something you need done in XP, you boot XP, and utorrent would recognize that torrent at 30% and continue downloading it.


Is this achievable?


(EDIT: obviously they would both be able to write on a shared partition where the data will be kept, that's not a problem)

---

### Post by 505 on 2009-04-08
Yes, it is possible. It should matter which program you use for it, as all torrent client can verify a download to see what still needs to be downloaded. For it to work you would have to setup both your client to wach a certain folder for .torrent file, and have them both configured to download the the same folder. And you may want to erase the .torrent file after complete download, so it will not start verifying all old downloaded torrents.

I'm not sure whith which program you can actually do all that on both Windows and Ubuntu. I do know that utorrent runs in Wine, so you could give that a try. Or find a client that runs on both Ubuntu and Windows.

---

### Post by ydraliskos on 2009-04-08
> **505 said:**
> Yes, it is possible. It should matter which program you use for it, as all torrent client can verify a download to see what still needs to be downloaded. For it to work you would have to setup both your client to wach a certain folder for .torrent file, and have them both configured to download the the same folder. And you may want to erase the .torrent file after complete download, so it will not start verifying all old downloaded torrents.

I'm not sure whith which program you can actually do all that on both Windows and Ubuntu. I do know that utorrent runs in Wine, so you could give that a try. Or find a client that runs on both Ubuntu and Windows.


i don't think utorrent has a setting to delete .torrents of completed downloads, only "loaded" downloads but yeah, I am trying what you said and it should work nicely.

EDIT: it can move them tho so I might just move em to a deletion folder

---

### Post by lovinglinux on 2009-04-08
You could easily achieve this using Deluge, which is the best torrent client for Linux/Windows in my opinion.

You can download the Linux version from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge) and the Windows version from [http://download.deluge-torrent.org/windows](http://download.deluge-torrent.org/windows)

Then setup both versions to  use the same download directory for the files and for the .torrents.

1 - Edit >>> Preferences >>> Downloads >>> "*Download to:*"
2 - Edit >>> Preferences >>> Downloads >>> "*Copy of .torrent files to:*"

This should do the trick without re-checking the files every time you switch OSs.

EDIT: Sorry. This will only works with deluge 0.5.x, because the fastresume files (those that control the torrent state) are now stored under */home/user/.config/deluge/state/*. Anyways, you could move the* /home/user/.config/deluge/state/* to your Windows Deluge folder and create a link to it on Ubuntu. Which means that whenever the Ubuntu client save a fastresume file to */home/user/.config/deluge/state/* it will actually saving it in the windows directory, so both applications share the same fastresume data.

---

### Post by ydraliskos on 2009-04-08
> **lovinglinux said:**
> You could easily achieve this using Deluge, which is the best torrent client for Linux/Windows in my opinion.

You can download the Linux version from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge) and the Windows version from [http://download.deluge-torrent.org/windows](http://download.deluge-torrent.org/windows)

Then setup both versions to  use the same download directory for the files and for the .torrents.

1 - Edit >>> Preferences >>> Downloads >>> "*Download to:*"
2 - Edit >>> Preferences >>> Downloads >>> "*Copy of .torrent files to:*"

This should do the trick without re-checking the files every time you switch OSs.

EDIT: Sorry. This will only works with deluge 0.5.x, because the fastresume files (those that control the torrent state) are now stored under */home/user/.config/deluge/state/*. Anyways, you could move the* /home/user/.config/deluge/state/* to your Windows Deluge folder and create a link to it on Ubuntu. Which means that whenever the Ubuntu client save a fastresume file to */home/user/.config/deluge/state/* it will actually saving it in the windows directory, so both applications share the same fastresume data.

Ok ima try this with deluge.


I just tried something v. similar under utorrent and NO, it does NOT work:
(folders are examples)
utorrent1:  Reads torrent from /  , when read it deletes (if it doesnt delete it forcefully renames it) it and puts it in /one/
instead.

utorrent2: Reads torrent from /one/, when read it deletes and puts it in / instead.



This would work if, once loaded, each utorrent didn't need the files anymore, but right now, one utorrent is deleting the other's necessary files and neither can work.

---

### Post by banda on 2010-07-11
> **lovinglinux said:**
>  you could move the* /home/user/.config/deluge/state/* to your Windows Deluge folder and create a link to it on Ubuntu. Which means that whenever the Ubuntu client save a fastresume file to */home/user/.config/deluge/state/* it will actually saving it in the windows directory, so both applications share the same fastresume data.

I tried this with deluge and it kinda works, but i have to show deluge the storage location for the files each time i reboot because windows stores the patch as "D:\storage\.." and ubuntu as "\media\D_Drive\Storage\..".

Any way i can make deluge understand its the same path? and not do it manually?

---

### Post by banda on 2010-07-11
ok, i found a solution to this, heres what i needed to do..

create another link to teh download drive in my home directory..

i created a directory called 
'/home/name/D:/'
and inside it placed a link to 'storage' foldr on the windows drive, so the torrents added in windows with the path d:/storage now get downloaded to the correct place even if i switch to ubuntu.

also got the partition to automount [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup)

---

### Post by Paqman on 2010-07-11
> **ydraliskos said:**
> 
Is this achievable?


Yes, although it might not be very practical for lots of large downloads. When you open the torrent client after booting up into the second system, it will have to check all the torrents before it can start downloading them. This may take quite a while if you've got large files or you're accessing them over a slow connection.

Tbh, I would just farm the torrent work out to another box. You can get routers like the Fonera 2.0N that will run your torrents for you, or you could use a nettop or something like a Viglen MPC-L/linutop or mini-ITX box. Doing this is not only convenient, it'll significantly reduce the amount of power you're wasting leaving your main machine on to run torrents.

---

### Post by banda on 2010-07-11
> **Paqman said:**
> Yes, although it might not be very practical for lots of large downloads. When you open the torrent client after booting up into the second system, it will have to check all the torrents before it can start downloading them. This may take quite a while if you've got large files or you're accessing them over a slow connection.

Tbh, I would just farm the torrent work out to another box. You can get routers like the Fonera 2.0N that will run your torrents for you, or you could use a nettop or something like a Viglen MPC-L/linutop or mini-ITX box. Doing this is not only convenient, it'll significantly reduce the amount of power you're wasting leaving your main machine on to run torrents.

umm with the method i described above, i can add torrents to deluge either from win or ubuntu + there is no file rechecking involved as both clients use the same location to store exit state so the download continues from where i left off on the other os

---

