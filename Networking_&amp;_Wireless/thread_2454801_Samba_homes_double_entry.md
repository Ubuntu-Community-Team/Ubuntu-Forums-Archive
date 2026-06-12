---
title: "Samba homes double entry"
date: 2020-12-06
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2020-12-06
I want to share my home directory with Samba on Ubuntu 20.04.  I added the below config to smb.conf and now I am seeing two entries, one called **homes** and the other called **elliott**.  Is this normal?  I thought it should show only one entry for this.  I guess if this is intended behavior then I will add a specific share just for my own user instead.

```
$ smbclient -L localhost -U elliott
Enter WORKGROUP\elliott's password: 


    Sharename       Type      Comment
    ---------       ----      -------
    tank            Disk      
    homes           Disk      all homes
    IPC$            IPC       IPC Service (hercules server (Samba, Ubuntu))
    elliott         Disk      all homes
SMB1 disabled -- no workgroup available

```

```
[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   server role = standalone server
   security = user
   obey pam restrictions = yes
   map to guest = bad user

[homes]
  comment = all homes
  browseable = yes
  read only = no
  create mask = 0700
  directory mask = 0700
  valid users = %S

```

---

### Post by TheFu on 2020-12-06
Yes, that's what I see.
May want a different file create mask, BTW, so every file doesn't get marked as executable.

---

### Post by Morbius1 on 2020-12-06
You are seeing the "double" entry because of the way you set up the special [homes] share and the way you are accessing it with smbclient.

[homes] as designed was not meant to be "browseable". It was a shortcut for the server administrator to create a share for everyone on the network.

If I have 20 clients to the server and I want them to each have a share accessible only to them individually I would have to create a share for each one of them then manage that by creating or deleting a share when clients are added or deleted from the network.

With a [homes] share all I have to do is create a local user and the share for an individual's share is created spontaneously and with a label that matches his username - but only when asked for by the client.

A Windows client passes the current users username automatically and without the users knowledge when he accesses a server so all he would see is his own share. A Linux client does not do that because Linux thinks that is goofy so instead he would have to ask for his own share explicitly either as a //host/user-name in fstab, a smb://host/user-name in the Linux file manager, or as you have done with a [highlight]-U elliott[/highlight] in smbclient.

Since you forced the [homes] share to be browseable you are seeing both.

---

