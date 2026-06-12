---
title: "login free samba"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Sigudian on 2007-03-22
hi, you know how windows file sharing works, you find the computer either while browsing network places, or typing in to the address line. well samba has the same concept, but thats just peachy.

**But you know how windows by default asks for no password or user-name what so ever? I have been trying to configure samba to do just that... or not do that, if you know what i mean, i just want samba not to ask for password or user-name.**

I mean, if you first share a file on the network, its for others to download, not for others to not to download, i know that a password can be useful for some purposes, but not for mine.

---

### Post by dmizer on 2007-03-23
post your smb.conf file.

alternatively:

you could just configure windows to remember the username/password for you so you don't have to type it.
-or-
make sure that your windows username is added to your ubuntu box so that it doesn't require authentication.

---

### Post by Matthamilton23 on 2007-03-25
I have the same problem only I am not sure what password that the prompt is asking for could you clarify?

---

### Post by dmizer on 2007-03-25
for password protected shares, you will have to add both the ubuntu username, and the username for the computer you want to connect with. (password protected shares in windows work the same way).

to add yourself as a samba user:
```
sudo smbpasswd -L -a ubuntu_username
sudo smbpasswd -L -e ubuntu_username
```

to add your remote computer as a samba user:
```
sudo useradd -s /bin/true windows_user
sudo smbpasswd -L -a windows_user
sudo smbpasswd -L -e windows_user
```

*where "ubuntu_username" and "windows_user" need to be replaced with your actual usernames for the respective machines.

then make sure that your ubuntu computer and your windows computer are both a part of the same workgroup.  after this, you will no longer be challenged for username and password when accessing the share. you MIGHT be challenged the first time you attempt to access the share.  if that is the case, just use your windows username and password.

---

### Post by stuntgp2000 on 2007-03-25
hi, here is what I do to create a public folder that's available for everyone to browse, download from/to within my local network.


1) first of all we should create our public directory in /opt/shares/ and then give everyone the right to write into it, open terminal and write this

```
sudo mkdir /opt/shares/public
sudo chmod 777 /opt/shares/public/
```

2) now it's time to configure samaba to use our folder as a public share
```
gksu gedit /etc/samba/smb.conf
```

find "security = user" without quotes, uncomment it and change it to "security = share"  without quotes 


then go to the end of that file and add this into it:

```

[Public Share]
        comment = Public Share
        path = /opt/shares/public/
	public = yes
	writable = yes
        browseable = yes
        guest ok = yes
	available = yes
	guest account = nobody
	force user = nobody
    	force group = nogroup
    	create mask = 0777
    	directory mask = 0777

```

save the file and back into terminal write this to reload samaba with our new configuration

```
sudo /etc/init.d/samba reload
```

I hope this was useful.

---

