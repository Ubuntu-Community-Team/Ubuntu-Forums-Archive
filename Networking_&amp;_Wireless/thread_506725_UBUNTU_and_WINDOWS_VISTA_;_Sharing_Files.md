---
title: "UBUNTU and WINDOWS VISTA :; Sharing Files"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by uniqueumang on 2007-07-22
Due to university requirement to do programming in UNIX-Like enviroment, I just installed UBUNTU(LAPTOP). Since as safe game player, I backed up files to my WIndows Vista(DESKTOP), however now i want to move files from vista-business to ubuntu, it ask ask for username domain  and password. All the detail, i tried to enter was incorrect
 don't know the reason

---

### Post by uniqueumang on 2007-07-22
Hence I need help and assistance. Cheers

---

### Post by scxtt on 2007-07-22
1. sudo aptitude install samba
2. edit /etc/samba/smb.conf to be in the same workgroup as vista, make a share (check out the smb.conf.example if necessary) restart samba if necessary (sudo /etc/init.d/samba restart)
3. sudo smbpasswd -a <windows user name>
(enter your windows password)
4. "map network drive" from vista ...

i know it works cause i did the same last night to share all the music on my Gentoo box w/ my new Vista laptop :)

you could also use Putty's SFTP client and make sure you have an ssh server running on ubuntu, and do it that way ...

---

### Post by uniqueumang on 2007-07-22
Thanks for the reply.

Can u tell the steps in more detail. I am a newbie.

---

### Post by scxtt on 2007-07-22
1. this will install samba, a protocol which allows windows and ubuntu to easily share files ("samba - A Windows SMB/CIFS fileserver for UNIX") ... the command i gave should be run in a terminal window, it will allow you to easily install samba ... you can fire up synaptic and install it that way too ...
2. you need to (possibly) make a few configuration changes to samba, since everyone's network is different ... the WORKGROUP defaults to either MSHOME or WORKGROUP and not everyone uses either one ... it's one of the 1st entries, so you should see it straight away ... there might also be some ubuntu GUI for configuring samba, not sure ... you can use any editor of your choice, command line (nano, vi) or GUI (gedit, kate, etc.) - just make sure you have root access (i.e. use sudo) ...
3. this is a big step a lot of people miss, and it's understandable - not something you'd generally think about ... samba (on unix) doesn't just let anyone connect - so the command i gave will **add** a new user account to use samba ... i generally have my ubuntu/windows password on my local network be the same, so it's easy ... if you don't do that, you just have to add another step when using "map network drive" ...
4. this is done in vista, and allows you to use the share you created in ubuntu as a disk drive in vista ... you just navigate to "map network drive" and enter the path to the share (\\<ubuntu_host>\<share_name>) and the drive letter you want to use ... if you use the same U/P combo between the two it should connect straight away ...

---

