---
title: "[SOLVED] Samba can only access neighbors through IP address"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by sanz on 2008-06-06
Ubuntu 8.04, always updated.

I'm in a LAN by a wireless router, together with some XP and some Mac under workgroup. Everything was fine, web surfing, file sharing and network printing, until I upgraded to 8.04.

Now I can surf the web without any problem. But I cannot access shared folders on any others', by Nautilus or inputing "smb://neighbor". Though I can access neighbors by input IP address, but we are using DHCP. "Network servers" displays a "windows network" icon, without correct workgroup name. By click it, an empty folder is displayed as "0 items". Though sometimes I do see the correct workgroup name, or even computer names in workgroup, I always get "0 items" when trying to open others' computer, even by inputing "smb://neighbor".  Yet I can only access myself by typing "smb://myself" in Nautilus.   
By "nmblookup", all computer names are successfully queried. All other computers do not have any problem. They can see and access all others, including mine.

my smb.conf:
-----------------------------

[global]
	workgroup = WORKGROUP
	server string = %h (Ubuntu)
	security = SHARE
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = wins lmhosts host bcast
	dns proxy = No
	wins support = Yes

[shared]
	path = /home/sanz/shared
	read only = No
	guest ok = Yes

------------------------------

---

### Post by sanz on 2008-06-09
:confused:
No replies? even worse situation in another forum, 3 same posts for 1 month, with hundreds of viewers yet not a single reply.

Is it a rare prob? what other info can i add?

---

### Post by heatpumpcontrol on 2008-06-09
No, this is a bug.  [https://bugs.launchpad.net/bugs/209520]("https://bugs.launchpad.net/bugs/209520") and if you read my post at the bottom (miguel) you'll see that I have the same issue and it's been like this since the upgrade. From what I've learned is that it might be a vfs issue or a nautilus issue because konqueror works without a problem under 8.04.

Many of us are waiting for this to be fixed.

Miguel

---

### Post by michaelzap on 2008-06-09
I've had this problem since Gutsy, so I'm not convinced that the problem is caused by the new Nautilus system (although it does appear to be a bug with Nautilus).

---

### Post by sanz on 2008-06-10
Tks guys. 
at least now i know that i can stop making useless efforts. quite relieving....

---

### Post by sanz on 2008-06-11
Solution :

1. make sure "wins support=yes" in /etc/samba/smb.conf
2. add "wins" after the line of "host" in /etc/nsswitch.conf
3. restart

---

### Post by michaelzap on 2008-06-11
> **sanz said:**
> Solution :

1. make sure "wins support=yes" in /etc/samba/smb.conf

That's it you want your computer to be a Samba server. If you want it to be a Samba client (so it can access other network shares) then you need to uncomment the line below that one and enter your router's ip address. At least that's what I did, and it seems to be working now.

If you're using Firestarter you also have to allow connections from the network shares.

---

### Post by lorenfb on 2008-06-11
The problem presented in this thread seems similar
to this thread:

[http://ubuntuforums.org/showthread.php?t=825401](http://ubuntuforums.org/showthread.php?t=825401)

but different in that my problem only occurs
with a DSL modem attached to the router, i.e.
Ubuntu has no problem with file sharing & NAS
access as long as the DSL modem is not attached.

This problem has existed from initial install
of 7.04.

Thanks for insights.

---

