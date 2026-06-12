---
title: "Samba and Permissions (Feisty)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by dpneal on 2007-06-19
Samba permissions are making me tear my hair out.

I have Samba working on my Feisty box.  The folder that I have shared is visible and writeable to my virtualbox XP guest.  All is well so far.

The trouble is that my user account doesn't have write access to the files I create in the shared folder from within the virtualbox XP guest.

Here's my smb.conf:

```


[global]
workgroup = WORKGROUP
netbios name = UBUNTU
security = SHARE
auth methods = guest
domain master = No
wins support = Yes

[SHAREDFOLDER]
comment = Home
path = /home/me/Samba
read only = No
guest ok = Yes


```

Suggestions?  I'd like to keep security as SHARE and not have to deal with user authentication if this is possible.  I'm a permissions lightweight. :-p

---

### Post by conjur3r on 2007-06-20
Samba user accounts are not tied into system user accounts.  This means that you'll need to create an appropriately named samba user with:

# smbpasswd USERNAME

Now to specify that a share can be writable and only to those listed:

```

writable = yes
valid users = USERNAME

```

This should be under which ever share you wish (eg, from your example, SHAREDFOLDER).

Edit: You could also look at:
```

write list = USERNAME

```

---

### Post by dmizer on 2007-06-20
modify your share like so:
```
[SHAREDFOLDER]
comment = Home
path = /home/me/Samba
browseable = yes
read only = No
guest ok = Yes
create mask = 0644
directory mask = 0755
force user = me
force group = me
```
and change "wins support" to no (this option is for a static network, and is only needed if there is not a windows computer active on the network)

add the following lines under [global]
```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
name resolve order = hosts wins bcast
```

edit:
sorry, forgot to mention that you'll have to add your ubuntu user id to the samba group like so:
```
sudo smbpasswd -L -a me
sudo smbpasswd -L -e me
```

---

