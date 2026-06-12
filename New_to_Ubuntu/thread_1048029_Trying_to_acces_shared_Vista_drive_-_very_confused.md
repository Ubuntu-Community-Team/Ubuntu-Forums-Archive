---
title: "Trying to acces shared Vista drive - very confused!"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Fizwidget on 2009-01-23
I've read through heaps of guides, and I'm getting more and more confused. Basically, I need to access a hard drive that's connected to a PC running Vista. The HDD is shared on the Vista PC, and I can access it easily from my other Vista computer and from my MacBook. It seems a hell of a lot harder trying to access it from Ubuntu though :(

When I open 'network' in nautlius, the Vista PC (it's called DIMENSION) shows up. When I double-click on it, there is a short delay, and then...nothing but an empty folder. Shouldn't the shared drive be showing up here?

I have installed Samba and smbfs...don't know what to do now. Help would be appreciated!

---

### Post by Fizwidget on 2009-01-23
...bump...

---

### Post by superprash2003 on 2009-01-23
try connecting this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by tarps87 on 2009-01-23
I the above does not work can you try the following three commands and post the output here:
```

ping *ip of vista pc*
smbtree
smbclient -L *ip of vista pc*

```

---

### Post by Fizwidget on 2009-01-23
> **superprash2003 said:**
> try connecting this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

When I enter smb://192.168.1.6 (the IP of the Vista PC) into nautilus, I get a blank window. This is the same as what happens when I open 'DIMENSION' from the network section in nautilus.

> **tarps87 said:**
> I the above does not work can you try the following three commands and post the output here:
```

ping *ip of vista pc*
smbtree
smbclient -L *ip of vista pc*

```

Output of the first command:

```
james@Ubuntu:~$ ping -c5 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
64 bytes from 192.168.1.6: icmp_seq=1 ttl=128 time=1.41 ms
64 bytes from 192.168.1.6: icmp_seq=2 ttl=128 time=0.735 ms
64 bytes from 192.168.1.6: icmp_seq=3 ttl=128 time=0.545 ms
64 bytes from 192.168.1.6: icmp_seq=4 ttl=128 time=0.376 ms
64 bytes from 192.168.1.6: icmp_seq=5 ttl=128 time=1.34 ms

--- 192.168.1.6 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 0.376/0.882/1.416/0.421 ms
```

Output of the second command:

```
james@Ubuntu:~$ smbtree
Password: 
WORKGROUP
	\\UBUNTU         		Ubuntu server (Samba, Ubuntu)
		\\UBUNTU\ubuntu         	
		\\UBUNTU\MP760          	Canon MP760
		\\UBUNTU\IPC$           	IPC Service (Ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\DIMENSION      		
		\\DIMENSION\Secondary Disc E	
		\\DIMENSION\print$         	Printer Drivers
		\\DIMENSION\MP760          	Canon Inkjet MP760 Series
		\\DIMENSION\Local Disc C   	
		\\DIMENSION\IPC$           	Remote IPC
		\\DIMENSION\External Drive 	
		\\DIMENSION\E$             	Default share
		\\DIMENSION\Chris          	
		\\DIMENSION\C$             	Default share
		\\DIMENSION\ADMIN$         	Remote Admin
```

Output of the third command:

```
james@Ubuntu:~$ smbclient -L 192.168.1.6
Enter james's password: 
Domain=[DIMENSION] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	Chris           Disk      
	E$              Disk      Default share
	External Drive  Disk      
	IPC$            IPC       Remote IPC
	Local Disc C    Disk      
	MP760           Printer   Canon Inkjet MP760 Series
	print$          Disk      Printer Drivers
	Secondary Disc E Disk      
session request to 192.168.1.6 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```

I hope that helps! Thanks for the help so far :D

---

### Post by cariboo on 2009-01-23
I'm not sure if it makes any difference, but Linux really doesn't like spaces in disk labels I would change:

> External Drive

to

```
External_Drive
```

and

> Local Disc C

to

```
Local_Disc_C
```

and to make things easier on yourself make comments to help you remember what you did.

Jim

---

### Post by Fizwidget on 2009-01-24
OK, I might try that. Any other suggestions? I don't understand why I can see the computer but not the shared drive...

---

### Post by Fizwidget on 2009-01-24
I have just tried renaming the drive and removing the space. No difference - it still does not show up in Ubuntu.

---

### Post by Fizwidget on 2009-01-24
One last bump...

---

### Post by tarps87 on 2009-01-26
What is the name of the share, if it is in the list:
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	Chris           Disk      
	E$              Disk      Default share
	External Drive  Disk      
	Local Disc C    Disk      
	Secondary Disc E Disk 

Try smbmount //*ipaddress*/*sharename* -o username=*share usersname or vista password*

---

### Post by tsali on 2009-01-26
Nautilus doesn't browse Vista shares worth poop. Vista uses a different networking hierarchy than XP and I've never been successful getting Nautilus to browse Vista shares without issue.

Try installing "TkSMB" from synaptic. Yeah, I know, it's ugly...but it works.

---

