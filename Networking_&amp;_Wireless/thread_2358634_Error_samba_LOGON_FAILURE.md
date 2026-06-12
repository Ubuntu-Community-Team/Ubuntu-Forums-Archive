---
title: "Error samba LOGON_FAILURE"
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by awachens on 2017-04-15
Hi good night !! I'm trying to share a folder with Windows 7 to Ubuntu 16.04.02 LTS

 [EMAIL="seguretat@seguretat"]seguretat@seguretat[/EMAIL]-informatica:~$ smbclient -L nobody -U samba
WARNING: The "syslog" option is deprecated
Enter samba's password:
Domain=[NOBODY] OS=[Windows 7 Ultimate 7601 Service Pack 1] Server=[Windows 7 Ultimate 6.1]
 	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Admin remota
	C$              Disk      Recurso predeterminado
	E$              Disk      Recurso predeterminado
	IPC$            IPC       IPC remota
	Linux ISO       Disk      
 When i try this:

 [EMAIL="seguretat@seguretat"]seguretat@seguretat[/EMAIL]-informatica:~$ smbclient //nobody/Linux ISO -U samba
WARNING: The "syslog" option is deprecated
session setup failed: NT_STATUS_LOGON_FAILURE
 

Regards !

---

