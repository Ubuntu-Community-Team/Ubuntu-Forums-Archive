---
title: "Samba server suddenly stops responding"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by Hase on 2007-01-11
Ok, I can SSH into the machine, everything works on the machine, but, there is no response when trying to access the smb shares.  I'm so desperate to figure this crap out, I deleted the /etc/samba/smb.conf file and it restarts without a hitch. Does this mean that my conf file is elsewhere?  I have beat my head against this for seven hours already. Please help.

---

### Post by kebes on 2007-01-11
The title of your post was "suddenly stops responding" ... does that mean that you previously had samba running properly, and then it stopped working?

It would help if you described the network environment you're in, and the things you've already tried.

For instance, if you're using some kind of router in a a small LAN, it's possible that you simply need to reboot the router or go into its configuration. Perhaps it is blocking smb? Alternately perhaps you un-blocked the samba port previously, but the router crashed and lost the setting. (Double check that it is there?)


Also, from a terminal (or while SSHed in), use the "netstat -l" command to list servers. Make sure you have a server listening for samba on the port you think it should be on. (Perhaps your samba switched to a non-standard port?)

---

### Post by Hase on 2007-01-11
It happened when I switched to a new router Netgear to a Linksys wrt54g.  I immediately switched back to the old one, with the same settings and it still didn't work.  smb.conf is:
```
[global] 
   workgroup = shoebox
   netbios name = server
   server string = server
   security = user

   interfaces = 127.0.0.1 192.168.1.100/120
   bind interfaces only = yes
   hosts allow = 127.0.0.1 192.168.1.100/120
   encrypt passwords = true

   log file = /var/log/samba/log.%m
   log level = 2
   syslog = 0
   syslog only = no
   max log size = 50

   wins support = no
   name resolve order = wins hosts lmhosts bcast
   local master = yes
   os level = 255
   preferred master = yes
	

[share]
	comment = Share
	valid users = aaron,nicole,samba
	writeable = yes
	path = /mnt/share
	force create mode = 0755
	force directory mode = 0755

[docs]
	writeable = yes
	valid users = aaron,nicole,samba
	path = /mnt/backup/documents.backup
	create mask = 0755
	force directory mode = 0755

```

I did delete smb.conf and smb.conf~, instead of restarting the deamons, I rebooted the system and it worked.  Now, I don't know what defaults it is using but it is working.  I am piecing parts back into /etc/samba/smb.conf until it breaks again.

---

### Post by kebes on 2007-01-11
Also, consider running "nmap" on the samba server (from the computer you are trying to connect from). Install it if it's not already installed ("sudo aptitude install nmap").

Try running it while SSHed in:
nmap localhost

Then from the remote computer
nmap 192.168.0.100

(or whatever the IP address for the server is...)

See whether you get a listening port. I believe samba is supposed to listen on 139.


Hopefully these diagnostics will let you decide whether the server is even listening.

---

### Post by Hase on 2007-01-11
I have gotten it to work.  I used the same smb.conf posted above but with one line commented out and a slightly different IP:

```
   interfaces = 127.0.0.1 192.168.1.
#   bind interfaces only = yes
   hosts allow = 127.0.0.1 192.168.1.
   encrypt passwords = true
```

Ideas?  And, does leaving the last octet off work or do I need some kind of wildcard?

---

### Post by Hase on 2007-01-12
And it's back dead this morning.  I rebooted with this, same as I left it last night, and it worked again.

```
[global] 
   workgroup = shoebox
   server string = server
   security = user

   interfaces = 192.168.1.1/20
#   bind interfaces only = yes
   hosts allow = 192.168.1.1/20
   encrypt passwords = true

   log file = /var/log/samba/log.%m
   log level = 2
   syslog = 0
   syslog only = no
   max log size = 50

#   wins support = no
#   name resolve order = wins hosts lmhosts bcast
#   local master = yes
#   os level = 255
#   preferred master = no

[share]
	comment = Share
	valid users = aaron,nicole
	writeable = yes
	path = /mnt/share
	force create mode = 0755
	force directory mode = 0755

[docs]
	comment = Backup
	valid users = aaron,nicole
	writeable = yes
	path = /mnt/backup/documents.backup
	create mask = 0755
	force directory mode = 0755

```

I made no changes to that server after I got it work last night, why did time cause it to go down?  I would expect that from Windows, not linux.

---

