---
title: "How to add win7 to samba pdc?"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-13
ok so I can ping the server that has the samba on it from the windows 7 box. I can also see the shares from the samba on the windows 7 box. I can get the box to show up to add it to the samba pdc but the domain join erros out. added the screen shots and samba log files.

server name of samba computer is Therese
computer with win7 is momhp

terminal shows
lance@Therese:~$ smbclient -L localhost
Enter lance's password: 
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.5.8]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Home Directories
	netlogon        Disk      Network Logon Service
	leanne          Disk      
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (Therese server (Samba, Ubuntu))
	lance           Disk      Home Directories
Domain=[LBERMUDEZ] OS=[Unix] Server=[Samba 3.5.8]

	Server               Comment
	---------            -------
	MOMHP                
	THERESE              Therese server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	BERMUDEZ             BERMUDEZL
	LBERMUDEZ            THERESE

used guides 
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)
[http://www.youtube.com/watch?v=8MWBhlaLIxQ](http://www.youtube.com/watch?v=8MWBhlaLIxQ)

---

### Post by Gone fishing on 2011-07-14
It is a bit of a pain you need to change some registry settings and possibly the NETLOGON parameters depending which version of Samba.

have a look at [http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

I found the login time to be misserably slow 2minutes plus but I note the link I sent gives some Windows tweeks which might help.

---

### Post by lance bermudez on 2011-07-14
That worked thank you so much!

---

