---
title: "samba has problems with large quantities of mp3's (more than 40gb in my case)"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by ubuntu_demon on 2005-04-22
When I try to add a big quantity of mp3's (more than 40 gb)  in xmms or music player they sometimes crash. Sometimes I can't even connect with samba anymore using nautilus. after this has happened. 

The last time I even had to do a reboot to get everything working properly again (sudo init 1; sudo init 2 didn't help , sudo /etc/init.d/samba restart didn't help and other things I tried didn't either)

A friend of mine has had the same problem.

Actually I don't know if the problem is with samba or with the client.

---

### Post by orion_114 on 2005-04-22
Is the player crashing or is it just hanging ?

I managed to load 38.5 GB of mp3s into XMMS over my network.
I even did it on a 433 MHz Celeron !!
I haven't exceeded 40 GB just yet. 
Try reducing the number of mp3's down to below the 40 GB mark and see if that solves your problem.

---

### Post by ubuntu_demon on 2005-04-22
[QUOTE=orion_114]Is the player crashing or is it just hanging ?

I managed to load 38.5 GB of mp3s into XMMS over my network.
I even did it on a 433 MHz Celeron !!
I haven't exceeded 40 GB just yet. 
Try reducing the number of mp3's down to below the 40 GB mark and see if that solves your problem.[/QUOTE]
 I have 43.3 GB of mp3's according to xdiskusage to be precisely.

I don't know whether it hangs or crashes .. I always get impatient when it happens and then it crashes :) When I not impatient it just takes a lot of time in xmms. And in music player I don't even know how much time.

I know I can prevent it by being less impatient or adding less music at a time. But I want to get to the source of this problem.

edit :

maybe I should try to optimize my smb.conf for handling my mp3 files better. I'm still searching for tips how to do this (I don't want to read everything that is written about samba I just need this to work)

---

### Post by segrewb on 2005-04-22
Is it Samba or XMMS?  Have you tried to mount that many MP3s from a local drive to see what happens?  ;-)  Just a thought.

Segrewb

---

### Post by ubuntu_demon on 2005-04-22
[QUOTE=segrewb]Is it Samba or XMMS?  Have you tried to mount that many MP3s from a local drive to see what happens?  ;-)  Just a thought.

Segrewb[/QUOTE]
 it's samba or smbclient because when it happens nautilus has also problems with connecting to the remote filesystems.

xmms has the problem less than music player

---

