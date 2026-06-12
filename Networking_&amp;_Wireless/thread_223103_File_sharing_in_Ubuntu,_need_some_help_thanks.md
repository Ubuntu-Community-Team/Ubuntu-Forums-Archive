---
title: "File sharing in Ubuntu, need some help thanks"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by aten on 2006-07-25
I have assigned a folder on my Ubuntu computer to shared, now when I find the computer on my Windows PC it is asking me for a user-name and password; In ubuntu I did not specify a password.

Please help.

Thanks A lot!!!
 

I did attach a Screen Shot of what I am talking about...

---

### Post by VirtuAlex on 2006-07-25
I think you have to add samba user
```
smbpasswd -a
```

---

### Post by aten on 2006-07-26
> **VirtuAlex said:**
> I think you have to add samba user
```
smbpasswd -a
```

Im so sorry but im new in this field.

This is what I get:
```
When run by root:
    smbpasswd [options] [username]
otherwise:
    smbpasswd [options]

options:
  -L                   local mode (must be first option)
  -h                   print this usage message
  -s                   use stdin for password prompt
  -c smb.conf file     Use the given path to the smb.conf file
  -D LEVEL             debug level
  -r MACHINE           remote machine
  -U USER              remote username
extra options when run by root or in local mode:
  -a                   add user
  -d                   disable user
  -e                   enable user
  -i                   interdomain trust account
  -m                   machine trust account
  -n                   set no password
  -w PASSWORD          ldap admin password
  -x                   delete user
  -R ORDER             name resolve order
admin@ubuntu:~$
```



Thanks again for all the help

---

### Post by aten on 2006-07-26
Oh yeah I forgot to add, that i don't know what to do after that

---

### Post by VirtuAlex on 2006-07-26
actually
```
sudo smbpasswd -a
```
sudo will ask you for your password and then smbpasswd will ask you to create network password and then you should be all set

---

### Post by aten on 2006-07-26
> **VirtuAlex said:**
> actually
```
sudo smbpasswd -a
```
sudo will ask you for your password and then smbpasswd will ask you to create network password and then you should be all set

well it worked, but on my windows laptop what do I insert in the username box?
See Attachment.

Thanks a lot!!

---

### Post by disciple on 2006-07-26
> **aten said:**
> well it worked, but on my windows laptop what do I insert in the username box?
See Attachment.

Thanks a lot!!
whatever is the username of the account you added on the ubuntu box

lets say you were 'aten@ubuntubox' on the ubuntu machine, by running 'sudo smbpasswd -a', you would have added 'aten' to the list of smb usernames

so the username should be 'aten'
and the password you chose


at least, i think so :-)

---

### Post by VirtuAlex on 2006-07-26
You insert your ubuntu username and the password you just created.

---

### Post by aten on 2006-07-26
> **disciple said:**
> whatever is the username of the account you added on the ubuntu box

lets say you were 'aten@ubuntubox' on the ubuntu machine, by running 'sudo smbpasswd -a', you would have added 'aten' to the list of smb usernames

so the username should be 'aten'
and the password you chose


at least, i think so :-)

When I ran:
```
sudo smbpasswd -a
```

I just was asked for my ubuntu password then I had to assign a password for the network.

No username was assigned.

---

### Post by VirtuAlex on 2006-07-26
> **aten said:**
> No username was assigned.
When you do not specify username on the command line smbpasswd uses your username under which you are logged in. But you can specify any username which already exists in the system, i.e. added through system->administration->users menu. Then you will have to use
```
sudo smbpasswd -a *username*
```

---

