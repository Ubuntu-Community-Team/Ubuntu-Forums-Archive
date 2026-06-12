---
title: "Can't open files on Linux Samba server from Linux client"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Aztek on 2008-04-19
EDIT: Ok, doing some more searching I found the thread below. After running

```
 sudo apt-get install smbfs 
```

the mount operation works and I can open files now.
[http://ubuntuforums.org/showthread.php?p=1492284]("http://ubuntuforums.org/showthread.php?p=1492284")

[SOLVED] (not sure how to change title to reflect this)








I have a feeling that the solution to this is very simple but I have yet to find it.

I just got an Ubuntu 7.10 server edition file server up and running using Samba. I configured using SWAT. The share is located on the server at /share. I can map this with windows clients just fine and browse the folders, play music files on the server, etc all fine.

However, when I try to use a Linux client (Ubuntu 8.04 beta, which is my primary desktop) I'm running into problems. If I try to "Connect to server" it gives me the error:

Can't display location "smb://server_name/share_name/" Location is not mounted. But it appears as though it *does* mount it. I can access the share through a link on my desktop. I can browse the folders, copy/paste files, create new folders. The problems arise when I try to open files. For example, if I try to play an mp3 on the server with VLC, it gives me an error. Same thing in Rhythmbox. However, mplayer works. In the same way, gedit can not open text files, but OpenOffice can.

I appreciate any efforts in assisting me.

---

### Post by brownknight on 2008-04-20
You can change the status to solved from the Thread Tools at the top right of the the thread.

---

