---
title: "Samba can't access subdirectories of a windows network"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by figueiravasco on 2007-07-06
Hello,
I am trying to access a Windows machine from Linux using Samba through a home network. Everything is okay except the fact I cannot access subdirectories of windows shared folders I configured. This only happens when the client is a linux machine. When I try a connection win-win there's no problem at all. Is there a way to solve this situation?

Thanks.

---

### Post by Andra on 2007-07-06
how those Windows shares are shared? Simple sharing, users, everyone?
You may need to use the same user as all those Windows machines are using or map guest.
Sorry, for not providing exact code, I don't know your situation, and regarding guests I have a very little experience.

---

### Post by figueiravasco on 2007-07-06
Andra, the folders are shared with full permission until I know. Even when I connect with Ubuntu to the windows machine I can read/modify files without problems. The issue is that it is only possible to the exact folder I turned shared. If there's a sub-folder I have no permission even to access it...

---

### Post by Andra on 2007-07-06
hmm, but then check Security setting for shared folder and for subfolder.
Also there is some computer security setting about traversing folders, but then it all the same leads to some point why Windows users are able to access those subfolders and from linux it is not working. That is, Windows computers are connecting as different users than linux computer.

---

### Post by meshellwm on 2007-07-13
Hey. I just installed Ubuntu 7.04 x64 on an AMD PC. I set up a samba share for 1 folder. My XP machines can see it and read/write. My problem is that Ubuntu can't see anything and I can't print to my HP DJ 5550 printer on a XP machine. I've spent several days trying to get this to work. Any help would be much appreciated.

I'm starting a new thread with this question. Sorry, but I can't delete this post.

---

### Post by meshellwm on 2007-07-28
I think I've fixed my Samba problem. 

While I was trying to get Samba to work, I realized that the changes over the whole network may have been slow. After changing my /etc/samba/smb.conf file (below) I shut sown all my computers and brought them all back up again. Everything seemed fine after that. Here is my file:

[global]
	workgroup = home
	server string = %h
	security = share
	log file = /var/log/samba/log.%m
	max log size = 1000
	panic action = /usr/share/samba/panic-action %d
	socket options = TCP_NODELAY
	preferred master = yes

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
	create mask = 0700

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[SharedF]
	comment = LaptopWG2 Fedora
	path = /usr/Shared/
	guest ok = yes
	writeable = yes

[SharedK]
	comment = LaptopWG2 Kubuntu
	path = /KUBUNTU/usr/Shared/
	guest ok = yes
	writeable = yes

[C_TEMP]
	path = /MSDOS/TEMP
	guest ok = yes

[C_USER]
	path = /MSDOS/User
	guest ok = yes

[C_USR]
	path = /MSDOS/usr
	guest ok = yes

[C_JOBS]
	path = /MSDOS/jobs
	guest ok = yes

[C_DVD]
	path = /MSDOS/DVD
	guest ok = yes

[C_INFO]
	path = /MSDOS/Info
	guest ok = yes

[C_MP3MUSIC]
	path = /MSDOS/MP3Music
	guest ok = yes

---

