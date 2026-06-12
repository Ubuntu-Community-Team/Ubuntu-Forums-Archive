---
title: "accessing share from windows xp"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by rakem123 on 2008-07-24
Hi Guys,

Im a completed Linux noob so excuse my ignorance here.

I have Ubuntu 7.10 installed on a computer. I need to share a folder so that i can access it from my windows XP machine.

The folder is that a need to share is on a separate drive, it shows up as Local Disk if i click on places then computer.

I right click on the folder, then go to share folder and run through everything there. The folder is shared through Windows networks (SMB). However if i go to the permissions tab of the folder properties i can't modify anything on there. it says owner is root and i am not the ower so i can't modify permissions.

I assume this is my problem because when i try to browse the share from my XP computer i just get "network path not found."

I can ping the IP of the ubuntu computer.

So how do i take ownership of this folder so i can share it and set permissions correctly. Then how can i access it from windows??

thanks guys!

---

### Post by superprash2003 on 2008-07-24
go to the terminal and type sudo nautilus .. then the nautilus window would open, now browse to the folder which you want to modify permissions, and then change it..

---

