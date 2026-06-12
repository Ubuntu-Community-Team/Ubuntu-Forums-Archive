---
title: "Samba, Guest directory with permission subdirectory"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by tomtalk24 on 2015-12-07
Hi folks.

I need a little help, I have a backup server nicely setup. Samba doing as it should but I need to setup something simple but secure for each users backup.

Main shared folder (guest access for everyone to see): Network Disk
Sub directory 1 folder (Only user colin can access): Colin Backup
Sub directory 2 folder (Only user tom can access): Tom Backup

Now if I setup samba to share Tom Backup with user tom access and Colin Backup with user access colin I have 2 networked folders. But I want Network Disk to the the folder you visit first with no password prompt, then I click on Tom Backup to enter my password. But if I setup Network Disk as a guest share everyone can access both sub folders with no password prompt at all. 

Is what I'm after (if it makes sense) beyond samba? Or is there a nice way for it to obey folder permission within sub folders? Its all due to keeping backed up data private, and keeping it neat organised in the network neighbourhood (not 1 share per user).

Thanks for you time. Tom.

---

### Post by TheFu on 2015-12-08
Samba data transfers don't use encryption, so if you care about security, Samba is NOT the best choice.

However, on a secure LAN (never WAN), samba's lack of encryption might not be an issue. I use it this way too. Convenience trade-off for a little less security.

Samba has the idea of a user's HOME where the userid used to connect will only be displayed to that specific userid.  It is configured inside the [homes] stanza. This is a special name, just for this purpose.  I think colin and tom are where you want to use this.  Do not use nested samba folders for this.  The home directory for each userid is set in the /etc/passwd file (for simple setups), but LDAP or a DBMS can also hold that data.
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.22.27
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```
The "network disk" is for guests (and everyone else) - is it read-only (you mentioned security) or do you intend for everyone to have write/delete access? I don't allow unauthent
```
[Network_Disk]
   hosts allow = 127.0.0.1 172.22.22.20/28
   hosts deny = 0.0.0.0/0
   comment = Network Disk
   browseable = yes
   path = /data/network_disk
   guest ok = yes
   read only = yes
   directory mask = 0555
   file mask = 0444
```

That should get you started.  The default **[global]** section for the /etc/samba/smb.conf should be fine, provided the workgroup is set correctly and ```
server role = standalone server
```

A few tips.  Don't use spaces in any names, except comments.
Do not next shared directories.
```
/home/tom
/home/colin
/data/network_disk

```
See how network_disk isn't anywhere near /home? Nested directories can cause issues.
Userids will need to be manually added to the samba-password file using **smbpasswd** before access to the home directories are allowed.

Hope this all makes sense.  BTW, if the workstations are Windows, then samba makes sense, but if they are OSX or Linux, samba is NOT the best solution.

---

