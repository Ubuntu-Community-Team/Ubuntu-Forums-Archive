---
title: "Almost getting vista shares"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by benign on 2008-10-30
I've been having problems seeing vista shares in ubuntu 8.10... At one time, with 8.04, I could see them with no problem so I know it works with nautilus. I'm not even receiving any error messages when I open the host, but the window is just blank.

The s%#$ thing is that I CAN see the shares if I load up kubuntu's dolphin, at least, I can see: C, C$, D$, drivers, and Public. I still can't access the printer though.


> 
Domain=[HP] OS=[Windows Vista (TM) Home Basic 6000] Server=[Windows Vista (TM) Home Basic 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C               Disk      
	C$              Disk      Default share
	D$              Disk      Default share
	drivers         Disk      
	HP DeskJet 710C Printer   HP DeskJet 710C <- need to use this!
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Public          Disk      
	Send To OneNote 2007 Printer   Send To OneNote 2007
session request to 192.168.0.106 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available


What are those last 3 lines?

and SMBTREE gives this:

> 
WORKGROUP
	\\HP             		
		\\HP\Send To OneNote 2007	Send To OneNote 2007
		\\HP\Public         	
		\\HP\print$         	Printer Drivers
		\\HP\IPC$           	Remote IPC
		\\HP\HP DeskJet 710C	HP DeskJet 710C
		\\HP\drivers        	
		\\HP\D$             	Default share
		\\HP\C$             	Default share
		\\HP\C              	
		\\HP\ADMIN$         	Remote Admin
HOME
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)


Before, it tried to time-out resolve Ubuntu through OpenDNS, but I modified the host file and resolv.conf which took the error away.

If I go straight to smb://hp/C I can see everything there, but they shares just don't show in nautilus otherwise after clicking on the host name.

Any ideas? I know a lot of people are having problems with this, but I figured it would be fixed in 8.10.

---

### Post by mgmiller on 2008-10-30
What happens if you enter in nautilus: smb://192.168.0.106

I took that IP from your post.

Also, what happens if you edit the following file:
```
kdesu kate /etc/samba/smb.conf
```and change the line that reads:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```To this:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts wins bcast host
```Notice, I removed the ";" at the front of the line and changed the name resolve order.

You probably need to log off and back on to get it to work.

This works for me on WinXP networks.  I haven't tried it with Vista.

---

### Post by benign on 2008-10-30
> **mgmiller said:**
> What happens if you enter in nautilus: smb://192.168.0.106

I took that IP from your post.

Also, what happens if you edit the following file:
```
kdesu kate /etc/samba/smb.conf
```and change the line that reads:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```To this:
```
# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts wins bcast host
```Notice, I removed the ";" at the front of the line and changed the name resolve order.

You probably need to log off and back on to get it to work.

This works for me on WinXP networks.  I haven't tried it with Vista.

If I use the IP address, I get the same response as if I just use the host name, or browse through with nautilus - no shares are visible. I've had this working before, but I think it was on 32 bit, not 64...

for the smb.conf file, I've already changed it, so it never helped. I did just get my printer working though by changing the name on vista to something without spaces - and now ubuntu recognizes it. I can print from openOffice, but text editor gives me a "failed to print - too many failed attempts" warning as if it is holding a grudge :confused:

---

