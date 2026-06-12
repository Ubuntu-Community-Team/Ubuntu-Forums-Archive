---
title: "[SOLVED] Backing up data from windows to linux"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by IanB2 on 2007-10-09
I have a windows laptop that I use for work (no choice on operating system) and I currently have an automated backup routine to a share on my windows desktop machine.

I have been trying to set up my linux test machine so that I can backup data files from my windows laptop but this time into a share on my linux machine.

I can view, edit, move, delete files in the windows share from my linux test machine, I can do likewise from another linux box, so I know that the shares are configured correctly. What I CANNOT do is access the linux share from a windows machine. 

I can navigate to the linux machine name, windows then asks for a username and password and I can get no further.

Any bright ideas? I'd like to move totally to linux on all my home PCs, but this backup problem is currently stopping me.

---

### Post by sonicx on 2007-10-09
hey,
i guess by share you mean a samba share. if you insist on using a samba share, there are TONS of HOWTOs about setting up samba. you problem is rather common, and not hard to solve - look around here: [http://swik.net/Feisty+samba](http://swik.net/Feisty+samba)
on the other hand you could just use a FTP share, which is a good (solid and simple) choice for synchronisation of backups. get some "ftp watchdog" for windumb to do the job.
regards,
sonicx

---

