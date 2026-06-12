---
title: "Samba troubles"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Chevalier on 2008-06-28
This is my first post. I am a novice Ubuntu user (2 monthe) and would be grateful for help with Samba. i have read many posts and advice on the subject; pardon me if I have overlooked the obvious.

I have been trying to connect my Ubuntu 6.06 PC to a Windows XP PC by using Samba. The two computers are connected through a router, the XP (IP 192.168.1.100) through wireless connection, Ubuntu (IP 192.168.1.101) with an ethernet cable.

From Ubuntu I can go straight to a Windows shared directory by typing the IP address (192.168.1.100) into the file browser and get files from the shared directory. However, if I try to access the same Windows share from Ubuntu by going through the Network Servers in "Places," it takes longer, and when it eventually finds a "Windows Network", the shared folders are nowhere to be seen.

Similarly, if I approach the Ubuntu shared folder from the XP, I can (sometimes) see Ubuntu in the Windows workgroup folder, but I can't cannect, and am told that \\Ubuntu is not available and that I might not have permission.
 
My smb.conf is given below. This is the latest and probably simplest of many versions; none of them has worked. In some of them I had a "host allowed" entry with the IP address of the ubuntu machine and the localhost IP (127...) as well. I took them out because I thought they might be redundant. 

As for the shared folders settings, I also have the Ubuntu "Shared folders settings" > "Share folder" > "General Windows sharing settings" set to "Do not use WINS server"

Under "Network settings" I have the Static IP address options filled in.

One further point: various samba related commands don't seem to produce any results, for example findsmb or sudo smbtree. They seem to run, but no information is given, as follows:

mike@Ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
mike@Ubuntu:~$



Here is the smb.conf:

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2008/06/28 16:04:22

[global]
	workgroup = MSHOME
	server string = %h server
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	ldap ssl = no
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[MLK]
	path = /media/hdb1/Share
	read only = No
	guest ok = Yes


Any advice you may have will be gratefully received.
MC

---

### Post by Iowan on 2008-06-29
For connecting to the XP share from Ubuntu, Places>Connect to Server works better for me.
To share from Ubuntu, you will probably need to install Samba-server (client comes installed by default - server does not) and perhaps **smbfs**.  You will also need to verify your Windows user has an account on the Ubuntu machine AND on Samba.  More details available [here]("http://ubuntuforums.org/showthread.php?t=202605").

---

