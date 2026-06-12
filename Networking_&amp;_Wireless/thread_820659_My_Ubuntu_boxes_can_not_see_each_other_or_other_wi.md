---
title: "My Ubuntu boxes can not see each other or other windows pc's on my home network"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by dcwandj on 2008-06-06
I have been working with Ubuntu and other distros for a few years on and off (off mostly) but now want to get serious about Ubuntu, especially since the last release.  While my setup is meeting most of my needs there's one issue that I can't work around that I haven't been able to resolve by reading most relevant posts after googling the question.  I'm hoping this forum can straighten this out.

Here's the problem:  My Ubuntu boxes can not see each other or other windows pc's on my home network.

Setup:  1 Xubuntu and 2 Ubuntu boxes (dual boots), 2 Windows XP (dual boot) & 1 Windows Vista.  Hard wired network with a router and cable modem.

Some details:  Samba is installed. smb.conf has the same network workgroup for all boxes (Linux and Windows).  All boxes can browse the WWW freely.

My experience:  From any windows pc I can go to Network and select my home workgroup and view all connected pc's.  I can then open and manipulate any shared folders on the Ubuntu pc's.  I need to login from Windows at the first connection after that my identity is remembered.
When I try the reverse from a Ubuntu screen, I can go to Places/Network/Workgroup and then there's nothing.  Ubuntu "clocks" for a while and then leaves a blank window at the workgroup level.  Xubuntu times-out with a "cannot connect" message.

Additional comments:  Other posts on related topics indicated that PyNeighborhood could help.  I installed this and, in part, it does.  With PyNeighborhood I can browse to a networked Windows pc and mount a shared drive or folder.  Unfortunately the file management options are rather clumsy, it takes a few more steps to get there, and it still doesn't work for my Ubuntu to Xubuntu connection.

Any suggestions gladly welcomed. Maybe I've missed something obvious since not many other posts seem to run into this.

Thanks in advance.

---

### Post by dmizer on 2008-06-06
for allowing windows computers to see ubuntu, check the first link in my sig.

to allow ubuntu to connect to windows computers, see the second link in my sig. this will not allow you to browse the windows network, but it will give you a fast, reliable, and usable connection to windows shares.

---

### Post by dcwandj on 2008-06-07
dmizer thanks for the quick assistance.  I followed the directions in your second link but no progress.  I went through the posts in your link and saw the posts to use the command "smbtree user=usereid".  Tried it  and got the following response that the connection to my windows boxes "Athlon64_Aria" is denied.  The AthlonXP is this machine.

```
dad@AthlonXP:~$ smbtree user=MumDad
Password: password
	\\WHITNEY-PC     		
timeout connecting to ip1:445
timeout connecting to 1p1:139
Error connecting to ip1 (Operation already in progress)
cli_start_connection: failed to connect to WHITNEY-PC<20> (ip1). Error NT_STATUS_ACCESS_DENIED
	\\ATHLONXP       		AthlonXP server (Samba, Ubuntu)
		\\ATHLONXP\documents      	
		\\ATHLONXP\LaserJet_1018  	LaserJet_1018
		\\ATHLONXP\PDF            	PDF
		\\ATHLONXP\IPC$           	IPC Service (AthlonXP server (Samba, Ubuntu))
		\\ATHLONXP\print$         	Printer Drivers
	\\ATHLON64_ARIA  		
timeout connecting to ip1:445
timeout connecting to ip1:139
Error connecting to ip1 (Operation already in progress)
cli_start_connection: failed to connect to ATHLON64_ARIA<20> (ip1). Error NT_STATUS_ACCESS_DENIED
	\\APTIVA         		Aptiva server (Samba, Ubuntu)
timeout connecting to ip1:445
timeout connecting to ip1:139
Error connecting to ip1 (Operation already in progress)
cli_start_connection: failed to connect to APTIVA<20> (ip1). Error NT_STATUS_ACCESS_DENIED
dad@AthlonXP:~$ 
```

---

