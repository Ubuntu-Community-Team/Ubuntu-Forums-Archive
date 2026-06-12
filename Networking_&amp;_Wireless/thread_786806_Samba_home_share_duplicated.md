---
title: "Samba home share duplicated"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Ryandor on 2008-05-08
I've finally gotten samba working 100% but there's just one little annoyance: My Home Directory shows up twice when viewing in Windows.

[IMG]http://www.ryandor.com/xtra/2008-05-08_094656.png[/IMG]

While not a huge issue, I'd like to hide the "homes" entry.
Is this a windows thing, or is there a way to hide it?
smb.conf below (also, any optimization suggestions welcome)

Thanks,
Ryandor

```

[global]
	log file = /var/log/samba.log
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	null passwords = no
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = smbpasswd
	wins support = no
	dns proxy = no
	netbios name = P3000-X
	invalid users = root
	workgroup = RYGROUP
	create mode = 0700
	security = user
	syslog = 1
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 0755
	pam password change = no
	log level = 3 

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
[torrent]
	create mask = 0700
	security mask = 0700
	comment = Shared Directories
	writable = no
	path = /home/shared/torrent
	available = yes
	browsable = yes
	public = yes
[data]
	create mask = 0777
	security mask = 0777
	comment = Data Share
	available = yes
	writable = yes
	browsable = yes
	public = yes
	path = /media/data


```

---

### Post by jetsam on 2008-05-08
Try setting **browsable = yes** to ```
browsable = no
``` under your [homes] share definition and then restarting samba.  You should still see the  justin entry in network neighborhood if you're logged on as justin, but not the homes entry.  

Sometimes network neighborhood remembers things you don't want it to.  You may need to manually delete the homes link on windows afterwards to get it to go away.

---

### Post by Ryandor on 2008-05-08
Thank you. That did the trick. Sometimes it's the simple things that get by me.

-Ryandor

---

