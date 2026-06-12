---
title: "Mint Elyssa and network printer!"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by panteraz on 2008-06-24
Hi!

I have my laptop with mint elyssa latest with all updates. I also have a desktop at my local lan with a usb hp printer (all-in-one) attached to it. I tried several methods to make my printer work with linux but nothing helped. It seems to be a samba problem. When I go to network servers -> windows network -> workgroup I can see my laptop and my desktop. When I click my desktop I am getting an empty nautilus window (like nothing is shared). When I give to nautilus smb://10.106.69.234 (the ip of the desktop) then I can see my shares...

Also, when i go to Administration - Printing then click new printer -> windows printer smb and browse I can see my printer! But I cannot connect to it when I click verify. I tried with or without password, tried my windows admin pass, guest and blank pass a lot of times... I disabled simple sharing from windows xp... Nothing! 

Inaccessible

This print share is not accessible.

also:

antonis@che-laptop ~ $ smbclient -L 10.106.69.234
Password: 
Domain=[FIDEL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	D$              Disk      Default share
	print$          Disk      Printer Drivers
	WD_250 (D)      Disk      
	Music (F)       Disk      
	F$              Disk      Default share
	ADMIN$          Disk      Remote Admin
	linux           Disk      
	C$              Disk      Default share
	HPC4340         Printer   HPC4340
session request to 10.106.69.234 failed (Called name not present)
session request to 10 failed (Called name not present)
Domain=[FIDEL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

Also tried smb://10.106.69.234/HPC4340 for smb://WORKGROUP/FIDEL/HPC4340.. nothing again..

Plz.. help...

---

### Post by panteraz on 2008-06-25
Up...:confused:

---

### Post by panteraz on 2008-06-25
I also found out that:

antonis@che-laptop ~ $ smbtree
Password: 
WORKGROUP
	\\FIDEL          		Fifel
timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
Error connecting to 208.69.34.132 (Operation already in progress)
cli_start_connection: failed to connect to FIDEL<20> (208.69.34.132). Error NT_STATUS_ACCESS_DENIED
	\\CHE-LAPTOP     		che-laptop server (Samba, Ubuntu)
		\\CHE-LAPTOP\amsn_received  	
		\\CHE-LAPTOP\Print_to_PDF   	Print to a PDF File
		\\CHE-LAPTOP\IPC$           	IPC Service (che-laptop server (Samba, Ubuntu))
		\\CHE-LAPTOP\antonis        	
		\\CHE-LAPTOP\print$         	Printer Drivers


-----------------

What is this IP??? I see it first time!!! My windows (FIDEL) IP is 10.106.69.234 and has nothing to do with 208.69.34.132 (it is not my internet adress even!). So its trying to access a wrong ip...

---

### Post by panteraz on 2008-06-26
The problem for this IP was the dns server ;) I solved it by changing it. Printer is still not working!!!!

---

