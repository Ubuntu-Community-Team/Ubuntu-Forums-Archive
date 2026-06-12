---
title: "Problem with samba"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by banexx on 2006-10-31
Hi,

I have just made a clean Ubuntu 6.10 installation on my computer. I am now trying to install samba so that my other ubuntu/windows machine can log on to this machine.

I have 
```
sudo apt-get install samba samba-common
sudo nano /etc/samba/smb.conf
```

and my smb.conf file looks like this
```

[global]
  workgroup = MSHOME
  ;netbios name = banexx-server
  security = USER

[private]
  path = /home/banexx
  browseable = Yes
  valid users = banexx
  writelist = banexx

```

I have also added the user like this
```
sudo smbpasswd -a banexx
``` 
and added the username to /etc/samba/smbusers

My problem is that when I try smb://<my_lan_ip> in nautilus, I get this error "The folder contents could not be displayed."

What am I doing wrong?

---

### Post by bmillsap on 2006-10-31
Possibly silly question, but have you restarted samba since you modified the config file and added the user?

edited to add: also, installed the smbfs package?  You might need that to be a client of a samba share.

---

### Post by bswilson on 2006-10-31
You forgot the third slash.

```
smb:///<my_lan_ip>
```

Your post only had 2 slashes behind smb:...

---

### Post by banexx on 2006-10-31
Yes, I have restarted samba and yes I have installed sshfs.

If i try ```
smb:///<my_lan_ip>
``` I get the error "Couldn't display "smb:///192.168.1.9". The location is not a folder"

---

### Post by dannyboy79 on 2006-10-31
do yourself a huge favor and go to a terminal, type in man smb.conf. read the whole thing and by the end you'll be helping other's set up samba. To give you some hints, security = user is the default so you don't need that. if you want a samba description from within winbloz, you need to remove the ; from before your netbios name line. also, you ddin't need to open smbusers since you aren't using that option within your smb.conf. when you did sudo smbpasswd -a blah, that was enough and your username was added to the passwd database. you could always try to see what happens when you do smbclient -L youriphere   , if when you enter the password you chose doesn't work than you know you did somehthing wrong. or what do these things tell you, smbtree? or findsmb.

---

### Post by dannyboy79 on 2006-10-31
> **banexx said:**
> Yes, I have restarted samba and yes I have installed sshfs.

If i try ```
smb:///<my_lan_ip>
``` I get the error "Couldn't display "smb:///192.168.1.9". The location is not a folder"

where are you typing this into? are you trying nautilus cause if you trying this at a terminal line than of course you gonna get this. it is smb:// not smb:/// I know that for sure! this is another great link to help you out. [http://www.oreilly.com/catalog/samba/chapter/book/appd.pdf](http://www.oreilly.com/catalog/samba/chapter/book/appd.pdf)

---

