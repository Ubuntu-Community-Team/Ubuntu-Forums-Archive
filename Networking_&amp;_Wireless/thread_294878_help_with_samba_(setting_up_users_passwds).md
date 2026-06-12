---
title: "help with samba (setting up users passwds)"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by boast on 2006-11-07
I'm having trouble setting up samba shares with passwords. I've followed many different guides, but I still get 'wrong password' when trying to get in the folder.

my samba setup is in /usr/local/samba/

---

### Post by maxpower on 2006-11-07
Can you elaborate on what you have done and post the relevant sections from your smb.conf?

mAx

---

### Post by boast on 2006-11-07
have done

sudo smbpasswd -a user
sudo smbpasswd -e user
sudo /usr/local/samba/bin/smbpasswd -a user
sudo /usr/local/samba/bin/smbpasswd -e user

```
[global]
        workgroup = WORKGROUP
        encrypt passwords = yes
	security = user
        username map = /usr/local/samba/bin/smbusers
        smb passwd file = /usr/local/samba/bin/smbpasswd

[public]
        comment = public
        path = /samba/
        public = yes
        writable = yes
        printable = no
  	create mask = 0777
  	directory mask = 0777
	force user = nobody
  	force group = nogroup

[cdrom]
	path = /media/cdrom
	read only = yes
	browseable = yes
	locking = no
	public = yes
	force user = nobody
	force group = nogroup

[downloads]
        comment = downloads
        path = /home/user/Downloads
        public = yes
        writable = no
        printable = no
  	create mask = 0777
  	directory mask = 0777
	force user = nobody
	force group = nogroup
	valid users = user

```

 gksudo gedit /etc/samba/smbusers
              with ```
 local_user = user
system_username = user

``` inside

and i think thats it for the most part

---

### Post by maxpower on 2006-11-07
Why do you have Samba in /usr/local/? Where did you install it from?  It may be that you are configuring your /usr/local samba but the service is running from /usr.  Where does the smb.conf that you posted reside?  ow are you starting Samba?

mAx

---

### Post by boast on 2006-11-07
i have two installations of samba (never bothered uninstalling one as it would cause me woes.)

i know it's the /usr/local/samba thats running, because thats were my smb.conf is thats being used.

/usr/local/samba/lib/smb.conf

---

### Post by maxpower on 2006-11-07
Well, if you are running the /usr/local Samba, it won't be looking in /etc/samba for its configs.  Therefore I believe your /etc/samba/smbusers file is not being used.  You might want to try creating the file in /usr/local/samba/lib as that is where your smb.conf resides.

---

### Post by boast on 2006-11-07
did. no luck =\

---

