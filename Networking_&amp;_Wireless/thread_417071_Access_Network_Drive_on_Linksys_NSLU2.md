---
title: "Access Network Drive on Linksys NSLU2"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by laurent_wies on 2007-04-21
Hi,

I am new to KUbuntu. I have updated my Windows XP laptop to KUbuntu 7.04.
I used to acces my MP3 collection located on my Linksys NSLU2 via a networked drive in Windows. I have tried many HOWTOs but I cant get it to work.

I can acces my MP3s in Konquerer (smb://192.168.0.77/DISK 2/MP3)
I wanna use this folder for building my music collection in Amerok. To do this, I think I need to mount it with Samba.

A step-by-step explanation would be great.

My configuration:

NSLU2: 192.168.0.77
MP3 collection folder on NSLU2: /share/flash/data/public/MP3

In Windows XP the network drive is: //linksys/DISK 2/MP3 with "admin" & "Ineluki" as login.

When I try: sudo mount ///192.168.0.77/share/flash/public/MP3 /media/mp3      I get an error message about an invalid share name.

BTW, what exactly is this SHARENAME I find everywhere in the forums?


Thank your for your help, else I will have to stick with Windows XP.

  Laurent

---

### Post by NeillHog on 2007-07-23
Exactly my problem. Did you ever solve this? If so please let me know how.

Thanks - Neill

---

### Post by NeillHog on 2007-07-24
For a solution go to
[http://ubuntuforums.org/showthread.php?p=3068110#post3068110](http://ubuntuforums.org/showthread.php?p=3068110#post3068110)

---

### Post by NeillHog on 2007-07-26
I found an answer at -
[http://ubuntuforums.org/showthread.php?p=3068110#post3068110](http://ubuntuforums.org/showthread.php?p=3068110#post3068110)

Neill

---

