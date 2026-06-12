---
title: "TOTALLY PERPLEXED: win xp filesharing"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by samster on 2008-10-05
I want to use my ubuntu machine to access files on a win xp machine already on my network.

Using the default smb.conf file (plus changing the workgroup name) I can connect the two machines directly together with a crossover cable, and they work flawlessly.  From the ubuntu box, I can see my shares on the win xp box (and vice versa).

However, when I run both of these through my router, neither of them work.  I have turned off all firewalls, opened all ports, and still nothing.  I *can* see the workgroup from the ubuntu box, but can't see the ubuntu box in it, or anything else in it.

There are three other win xp machines on my network, and I can see none of them.  I'd like to get the ubuntu machine to work through the router so I can see/access all three win xp machines.

I have been reading posts and trying things all weekend, and nothing has helped.
Using ubuntu 8.10 beta now, but it doesn't work in 8.04 either.

ANY HELP IS APPRECIATED.

---

### Post by cariboo on 2008-10-06
What is the output of:

```
smbclient -L ubuntu_computer -U%
```

Where ubuntu_computer = the name of your Ubuntu computer or it's ip address

The output should look something like this:

```
 smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Willy server (Samba, Ubuntu))
	win_updates     Disk      Project Dakota
	data            Disk      data storage
	images          Disk      iso images
	music           Disk      Music directory
	Movies          Disk      Tv and Movies
	print$          Disk      Printer Drivers
	HP-Laserjet     Printer   Laser Printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	RISKY                Dad's computer
	WILLY                Willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY

```

Jim

---

### Post by superprash2003 on 2008-10-06
when connected to the router, firstly ensure that ubuntu machine is able to ping all the 3 windows machines

---

