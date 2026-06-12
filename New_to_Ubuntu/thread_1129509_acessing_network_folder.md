---
title: "acessing network folder"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Novnia on 2009-04-18
All id like to do is CnP a folder from my windows machine to my linux machine.


the windows share is \\PETEP4_2\World of Warcraft

my linux box sees Windows Network and then Workgroup, but cant browse workgroup.

I installed samba via add/remove and then installed pyNeigborhood, a rework of LinNeighboorhood, a program someone said might help. i did a whereis samba in terminal and samba is isntalled, i can do smbclient too and get a list of switchs.

what i cant seem to do is copy n paste easily. help please? thank you.

---

### Post by cariboo on 2009-04-18
Have you got the shares set up in /etc/smb.conf?

You shuld be able to see the shares on your Ubuntu computer if you type in a terminal:

```
smbclient -L <servername> -U%
```

the output should look something like this:

```
 smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.32]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (FreeNAS Server)
	backups         Disk      my home dir backups
	misc            Disk      varous stuff
	media           Disk      music and video files
	data            Disk      document storage
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.32]

	Server               Comment
	---------            -------
	WILLY                FreeNAS Server

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Jim

---

### Post by xarquid on 2009-04-18
This is a great guide:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Specific to your situation. Please look at "Browsing SMB shares."

Also, re-confirm all of your settings are correct. Most importantly, for your network.

The main problem here, I bet, is access to the Windows machine via your network. 

Are you being prompted for your login to that specific machine? If not, something is not configured properly. You should be asked for your login (the login for the Windows machine) and have to login before you are even able to copy/paste anything.

---

### Post by Novnia on 2009-04-18
i double click workgroup and it opens a window saying "Opening workgroup, you can stop this action by clicking cancel."

then it sits.

then it says Unable to mount: Failed to retrieve share list from server

reading that guide, its alot to take in. i installed the smbfs and it removed the samba i got. i think i got the server not the client the first time, i dont got the /etc/sbf file setup

---

