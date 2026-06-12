---
title: "Trouble setting up Samba"
date: 2024-01-14
forum: Networking &amp; Wireless
---

### Post by mmcmonster2 on 2024-01-14
So I installed samba with the following commands:
```
$ sudo apt-get install samba smbclient
$ sudo smbpasswd -a myusername
(I didn't give it a password)
$ cat /etc/samba/smb.conf
[global]
   workgroup = WORKGROUP

   map to guest = Bad User
   dns proxy = no

   log file = /var/log/samba/%m
   log level = 1

   server role = standalone server

   map to guest = bad user
   usershare allow guests = yes

   follow symlinks = yes
   wide links = yes
   unix extensions = no

[Media]
   path = /home/myusername/Samba_Media/
   force user = myusername
   available = yes
   guest only = yes
   guest ok = yes
   read only = yes
   browseable = yes
   public = yes
   writable = no
$ sudo service smbd restart
$ sudo ufw allow samba

```

If I run "systemctl status smbd", it says that samba is running.

I am trying to create a simple guest share that I can access from anywhere on my home network.

If I open up the file manager and go to network and try to attach to this samba share, it asks for a password.  I thought it shouldn't because it should be set up as a guest.

What am I doing wrong?

---

### Post by SeijiSensei on 2024-01-15
Use "sudo smbpasswd -a yourusername" to create a Samba password for your account.

---

### Post by Princey on 2024-01-15
Like SeijeSensei pointed to, samba doesn't copy your password like you assumed using the > **sudo smbpasswd -a myusername** command. You actually created a password for samba using that command instead. So, if you want to use the same password for your account, you have to manually specify it using the command given.

---

### Post by mmcmonster2 on 2024-01-16
Actually, what I have done before (and was doing this time) was "sudo smbpasswd -a myusername", and when it asked for a password, I just hit <return> to leave the password blank.

In the past that would create samba with a guest user.

I just tried it again and gave it a password the same as my login password, and then restarted smbd, and it still doesn't work.

I would like to create a guest share that doesn't require a password.

---

### Post by Morbius1 on 2024-01-17
> **mmcmonster2 said:**
> Actually, what I have done before (and was doing this time) was "sudo smbpasswd -a myusername", and when it asked for a password, I just hit <return> to leave the password blank.

In the past that would create samba with a guest user.
No it does not. Samba already has a guest user created by default and it's name is "nobody":

> $ testparm -sv | grep 'guest account'
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

	guest account = nobody


The oddity of your share definition is the "guest only" parameter. If the client user runs Windows and you have that user in your samba password database that user would never be able to access that share.

Is the client user running Windows?

And is the Windows client user's user name also 'myusername' ?

If it is that would explain your symptom.

Windows does something goofy. When it initially contacts your server it passes it's username and local login password - automatically. If the share allows guest access that's not an issue. But if the server has that user name and password set up in samba it does a credentals check. In this case the Windows user has a real password but your samba password is blank.

That would result in the Windows user being prompted for a password - even for a guest share.

I would remove the "only guest" declaration in your share definition then remove everyone in your samba password database. You can get a list from this:
```
sudo pdbedit -L
```

---

