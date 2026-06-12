---
title: "netbook, ubuntu and NAS"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by beachgeek on 2010-06-13
I have Ubuntu-Netbook 10.04 running from a USB stick. I think. I told it to install the files on Partition D which it did but after a reboot it said it was installing [there were 8 steps] and suggested removing my partition. I stopped. I assume that would work like Windows and wipe out everything on Drive C. 

As it doesn't see my NAS [but does see the router allowing me to access the internet] I am reluctant to do that. Am I going to have an issue accessing my NAS? It says ***Unable to mount location. Failed to retrieve share list from server.***

Is there something I need to do to make it see my NAS? When I can do that I should be ready to fully install.

---

### Post by cariboo on 2010-06-15
Can you ping your NAS? If you can what is the output of:

```
smbclient -L <server> -%H
```

The output should look similar to this:

```
smbclient -L willy -%H
Enter my password: 
Domain=[APLUS] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	Images          Disk      iso images
	Iso             Disk      Mounted iso's
	Stuff           Disk      Everything Else
	Documents       Disk      Documents
	Music           Disk      Music
	Movies          Disk      Movies & TV Shows
	print$          Disk      Printer Drivers
Domain=[APLUS] OS=[Unix] Server=[Samba 3.4.0]
```

---

### Post by beachgeek on 2010-06-15
No, cannot ping the NAS

---

