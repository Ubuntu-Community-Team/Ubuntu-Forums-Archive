---
title: "Using Wine to launch windows apps relative to a windows server...."
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by SC2Sick on 2006-09-17
An application I use at my work is designed poorly IMO for network distribution.

It uses a foxpro database and runs in windows..

In order to use it I have to do a minimal install on the client computer and then shortcut and "run in folder option (windows)".

On a typical windows setup to access this program we map a network drive to the servers share and call it X:\ and on the server we have a total install.

This application runs great through Wine (seemingly better than on the Win98 machines we use....) and I'd like to be able to use it.  I'd like to be able to mount the share on the server through Samba so that it appears rather than smb://server/share  to /mnt/share on the local filesystem so i can use "winefile" to mount it as a drive and then do like i do on the windows machine.


so basically the main question of this whole post is how i mount a windows share to map as  /mnt/share ??

---

