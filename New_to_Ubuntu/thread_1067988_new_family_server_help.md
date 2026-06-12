---
title: "new family server help"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by RobTi on 2009-02-12
Hi all
This is my first post although been olurky for a while.
I have a basic pc that i want to store files on and allow 2 x pc's and 2 laptops to access.
I installed ubuntu and followed this site [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4")up to page 4.
When i try to access the server from anywhere it fails to find the files, i am typing in 

\\(whatever the IP of the server is)\homes

Any help and if i have done all this wrong a little nudge in the right direction please
Thanks
Robert

---

### Post by kanikilu on 2009-02-12
What happens? Does it ask you for your username/password? Did you do the smbpasswd part of that step?

Are you sure samba is running? You can do "ps aux | grep smbd" (w/o quotes) at the terminal to find out.

Also, this is obvious, but are you able to ping the server from one of the other machines to make sure you have the right IP?

---

### Post by Hospadar on 2009-02-12
To be honest I can't really help you with samba (which is the protocol windows uses and that guide tells you how to set up).  I'd suggest you try ssh, it's a very secure protocol that can potentially allow you to transfer files, remote control your server, run programs that are installed on your server, etc.

The community documentation has a really great writeup here:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Also you might want to look at their samba writeup
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=samba&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=samba&sa=Search)

---

### Post by cariboo on 2009-02-12
Could paste the output of the following command in your next post. Open an Applictions-->Accessories-->Terminal on your server and type:

```
smbclient -L localhost -U%
```

it should look something like this:

```
smbclient -L localhost -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	stuff           Disk      misc stuff
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
	HP_LaserJet_5P_LPT_1 Printer   HP LaserJet 5P
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	JACK                 jack server (Samba, Ubuntu)
	WILLY                willy server (Samba, Ubuntu)
	WINMCLEESE           

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Your output will be different, but it should have the same elements.

Jim

---

