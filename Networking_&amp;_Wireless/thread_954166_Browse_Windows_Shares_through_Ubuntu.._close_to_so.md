---
title: "Browse Windows Shares through Ubuntu.. close to solution?"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by drazabyss on 2008-10-20
I know this topic has been covered ad nauseam, but I feel like I am close... I'm not just familiar enough with ubuntu to know what to do.

I'm trying to browse windows shares on ubuntu; ubuntu shares on a Vista laptop.  The vista laptop is doing a find job connecting with samba - I can share any ubuntu folder and access it on my laptop.

The problem is access my windows shares through ubuntu.  Nautilus lists my Workgroup and each computer, but when Colossus (my Windows computer) is clicked, the shares are empty.  When I click Colossus, I am never prompted for a password... 

I've discovered this much...

using the smbtree command and inputing my vista password, I can get a complete list of shares in each folder I have set to share in vista.
```

WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\videos         	
		\\UBUNTU\music          	
		\\UBUNTU\freewidescreenwallpapers	
		\\UBUNTU\PDF            	PDF
		\\UBUNTU\X125           	Lexmark X125
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\COLOSSUS       		Laptop
		\\COLOSSUS\Videos         	
		\\COLOSSUS\Users          	
		\\COLOSSUS\Public         	
		\\COLOSSUS\IPC$           	Remote IPC
		\\COLOSSUS\D$             	Default share
		\\COLOSSUS\C$             	Default share
		\\COLOSSUS\ADMIN$         	Remote Admin

```

The last entires under Colossus are what I am trying to access.

If I just type smbtree and bypass the password (hit enter), I get this:
```

WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\videos         	
		\\UBUNTU\music          	
		\\UBUNTU\freewidescreenwallpapers	
		\\UBUNTU\PDF            	PDF
		\\UBUNTU\X125           	Lexmark X125
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
	\\COLOSSUS       		Laptop
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine COLOSSUS.  Error was NT_STATUS_ACCESS_DENIED

```

My feeling is that Nautilus is not asking me for the pw when it should and if I could get it to, then my problem would be solved.  Maybe I'm right... or not.  But I do not know how to further troubleshoot this problem.

Any help?

---

### Post by drazabyss on 2008-10-21
SHould have searched harder... [this]("http://ubuntuforums.org/showpost.php?p=1686695&postcount=1") solution is dead on.

thank you dmizer

---

