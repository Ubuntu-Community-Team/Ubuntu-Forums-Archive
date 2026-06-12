---
title: "Mount Network-Path"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by muh2k4 on 2007-07-14
Hey there.

I have a network of several PCs. One is a Windowsclient holding a couple of mp3s.
When i browse through them i got a path like

mb://192.168.0.103/Musik/somefolder/some.mp3 ...

That path dragged to xmms regetably does not result in that file getting played, it will be skipped. Using the standard totem-player it is getting played. So i assume XMMS has some issues with the resolving of that network path.

My idea for a solution was to kinda mount that network path to a local path - somehow like a wrapper ... but i got obviously proved blueeyed with that approach ...

Are there any other ideas how i could move XMMS to play that file exept downloading it?
(XMMS ist just 1 example where that problem has got significance)

THX for help ... the l1nux-bo0n collecting beans! =)

---

### Post by McNils on 2007-07-14
Have you tried to mount with smbfs?

[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29)

---

### Post by muh2k4 on 2007-07-14
Well iam just having a look at this.
Am i misstaken or are these all under the assumption to have that location mounted permanently? 

sudo mount //server/share /media/mount_folder smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0 

gives me the description of the usage of mount =/

---

