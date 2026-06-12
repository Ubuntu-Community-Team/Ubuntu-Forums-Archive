---
title: "can see other machines not on same subnet"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by tech0007 on 2008-07-19
My ubuntu box has 2 nics and shares its internet connection with an XP box. The ipaddress of the nic that connects to XP is 192.168.0.1, the XP has 192.168.0.2. I setup samba to share folders in ubuntu.  When I do:

tech0007@myubuntu-desktop:~$ smbclient -L 192.168.0.1
Password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (myubuntu-desktop server (Samba, Ubuntu))
	print$          Disk      Printer Drivers
	PDF             Printer   PDF
	videos          Disk      
	music           Disk      
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	3954FB20C0D04D7      
	ARABSWELL            
	MYUBUNTU-DESKTOP     myubuntu-desktop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	HUNTER               KUBO
	MSHOME               JUNOISLAND
	WORKGROUP            MYUBUNTU-DESKTOP

My XP box is currently turned off. I don't recognize the other machines (3954FB20C0D04D7, ARABSWELL, KUBO, JUNOISLAND).  Is this normal? Am I sharing my files with other people that shouldn't have access to it? I checked the /var/log/samba dir and here's what I got:

tech@myubuntu-desktop:~$ ls /var/log/samba
cores          log.192.168.0.1      log.192.168.250.230  log.arabswell        log.myubuntu-deskto   log.nmbd.1.gz
log.127.0.0.1  log.192.168.0.2      log.192.168.254.229  log.chloenicole      log.myubuntu-desktop  log.smbd
log.127.0.1.1  log.192.168.242.234  log.3954fb20c0d04d7  log.demo-e39834e01b  log.nmbd              log.smbd.1.gz

I get a bunch of different ipaddresses I dont recognize! Do i need to reconfigure smb.conf? Any input is appreciated.

---

### Post by tech0007 on 2008-07-20
bump

---

### Post by flytripper on 2008-07-20
bleh

---

### Post by tech0007 on 2008-07-20
bump

---

### Post by tech0007 on 2008-07-25
bump

---

