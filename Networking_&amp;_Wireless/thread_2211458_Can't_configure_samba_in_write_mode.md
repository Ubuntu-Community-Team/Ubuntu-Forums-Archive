---
title: "Can't configure samba in write mode"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2014-03-16
Hello, I'm having trouble configuring samba correctly, I've tried countless options and I'm able to read, but I can't configure it to be able to write. My last attempt was to remove any reference to passwords, which is why that error has occurred but it made no difference to me being able to read or write anything. 

Can anyone see what I need to change?

Thank you for any help. 

```

root@banana:/mnt/md0# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[movies]"
Processing section "[tv_shows]"
Processing section "[flac_music]"
Processing section "[mp3_music]"
Processing section "[pictures]"
Processing section "[documents]"
Loaded services file OK.
ERROR: the 'unix password sync' parameter is set and there is no valid 'passwd program' parameter.
Server role: ROLE_STANDALONE
[global]
	workgroup = ORCHARD
	server string = %h server
	map to guest = Bad User
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[movies]
	comment = Banana Movies Share
	path = /mnt/md0/movies
	write list = root, rhys, xbmc
	read only = No
	create mask = 0775
	guest ok = Yes

[tv_shows]
	comment = Banana TV Shows Share
	path = /mnt/md0/tv_shows
	write list = root, rhys, xbmc
	read only = No
	create mask = 0775
	guest ok = Yes

[flac_music]
	comment = Banana Flac Music Share
	path = /mnt/md0/flac_music
	write list = root, rhys, xbmc
	read only = No
	create mask = 0775
	guest ok = Yes

[mp3_music]
	comment = Banana MP3 Music Share
	path = /mnt/md0/mp3_music
	read only = No
	create mask = 0775
	guest ok = Yes

[pictures]
	comment = Banana Picture Share
	path = /mnt/md0/pictures
	read only = No
	create mask = 0775
	guest ok = Yes

[documents]
	comment = Banana Documents Share
	path = /mnt/md0/documents
	read only = No
	create mask = 0777
	guest ok = Yes

```

---

### Post by tfrue on 2014-03-17
Try either removing the "write list= " option, or at least "comment" them out, or try and add "valid user= chris " for example. You would need to replace chris with an actual user on the local system and that you wanted to access the share. 

You would also need to add chris ( Or whichever user you decided to use) with "smbpasswd" so the valid user= option will work. Type:
```
sudo smbpasswd -a chris
(Enter desired password)
(Re-enter password)
sudo service smbd restart;sudo service nmbd restart

```

That will add the user, and then restart the samba services just to be safe.

Hope that helps, 
Chris

---

### Post by tfrue on 2014-03-17
I believe that the "write list= " is directed at only allowing groups, so if you are wanting to use usernames, then do the smbpasswd -a command I previously showed with the "valid user= " commands.

It also seems a bit pointless to make the share guest ok, but only allow certain groups to access it (With the write list). What I would do is remove the "create mask= " and "write list= " while adding "writeable= yes" "browseable= yes" and see if you can access the share. If you can, then start adding other options seeing where it fails and succeeds. 

Hope this helps, 
Chris

---

### Post by tfrue on 2014-03-17
Also, make sure the proper permissions are set up on the /mnt/md0/ directories like /movies and /tv_shows. For a complete open share on all the directories under the /mnt/md0/, then type:
```

sudo chmod -R 0777 /mnt/md0/* 
```

Chris

---

### Post by AmbiguousOutlier on 2014-03-17
> **tfrue said:**
> Also, make sure the proper permissions are set up on the /mnt/md0/ directories like /movies and /tv_shows. For a complete open share on all the directories under the /mnt/md0/, then type:
```

sudo chmod -R 0777 /mnt/md0/* 
```

Chris

I needed to;

```
chown nobody.nogroup /mnt/md0
```

---

### Post by tfrue on 2014-03-17
Did that resolve your issues?

EDIT: Sorry, didn't notice the SOLVED at the top, my browser crashed and reloaded and I didn't see it.

---

