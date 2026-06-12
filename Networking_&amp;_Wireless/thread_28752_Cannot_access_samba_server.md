---
title: "Cannot access samba server"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by g-joey on 2005-04-21
Hi,

although I have read many threads and how-to's about this topic, I still cannot access my Samba share from any Windows PC. Here's the relevant part of my smb.conf:

 > [Download]
read only = no
guest ok = yes
browseable = yes
available = yes
public = yes
path = /data/shares/Download
comment = Software
create mask = 666
directory mask = 777 

All I get when I try to access the Download share is a login dialog. How can I get rid of it?

TIA, Joe

---

### Post by siebzehn on 2005-04-21
[QUOTE=g-joey]Hi,


All I get when I try to access the Download share is a login dialog. How can I get rid of it?

TIA, Joe[/QUOTE]

Hello.

You have to create accounts (in the linux box) for the users that need to use the share.

First:


sudo adduser *username*   and follow the instuctions

sudo smbpasswd -a *username* 

Then restart the samba server with     sudo /etc/init.d/samba restart

---

### Post by g-joey on 2005-04-22
[QUOTE=siebzehn]You have to create accounts (in the linux box) for the users that need to use the share.[/QUOTE]

Hi siebzehn,

what if I just want **all** users to have access to the shares? Do I really have to know all the names and create an account for everyone? That would be rather laborious...

//Joe

---

### Post by segrewb on 2005-04-22
Try this:

[Download]
path = /data/shares/Download
read only = Yes
guest ok = Yes

Restart as shown above.

Then you will not have login.  Just use network neighborhood to see directory.

If this doesn't do it, you will need to show the global setting as well.  ;-)  In order to help pin point problem.

Segrewb

---

### Post by siebzehn on 2005-04-22
[QUOTE=segrewb]Try this:

[Download]
path = /data/shares/Download
read only = Yes
guest ok = Yes

Restart as shown above.

Then you will not have login.  Just use network neighborhood to see directory.

If this doesn't do it, you will need to show the global setting as well.  ;-)  In order to help pin point problem.

Segrewb[/QUOTE]
 Yes you can eliminate the user authorization, but I think you won't be able to access the home directories in the ubuntu server from the windows machines.  Using the authorization samba shares each user's home directory by default, this way each user can acces his home directory after logging in.  I find this very useful in my network.

---

### Post by segrewb on 2005-04-22
I agree 100% and would never do this.  However I assume he has a controlled local network and just wants himself, his friends, and the public (everyone)  to be able to access this share,  no logins, no home directory access, no security, etc.

Segrewb

---

### Post by siebzehn on 2005-04-25
[QUOTE=segrewb]I agree 100% and would never do this.  However I assume he has a controlled local network and just wants himself, his friends, and the public (everyone)  to be able to access this share,  no logins, no home directory access, no security, etc.

Segrewb[/QUOTE]
 Then the best thing would be to use the same configuration Windows uses, meaning no user level access.  But maybe, just maybe if  you think this is the best setup is just because you have never tried the home shares.  I would give it a try...

---

### Post by g-joey on 2005-04-25
[QUOTE=segrewb]I assume he has a controlled local network and just wants himself, his friends, and the public (everyone) to be able to access this share, no logins, no home directory access, no security, etc.[/QUOTE]
Hi segrewb,

you're right, that's exactly what I want to do.

I have extracted the *global* and *download* section of my *smb.conf*, maybe this will help you to help me :)

 > [global]
log file = /var/log/samba/log.%m
restrict anonymous = no
ldap ssl = No
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
obey pam restrictions = yes
null passwords = yes
domain master = no
passdb backend = tdbsam guest
passwd program = /usr/bin/passwd %u
dns proxy = no
server string = My Server
max protocol = NT
invalid users = root
workgroup = foobar
server signing = Auto
security = share
syslog = 0
preferred master = no
panic action = /usr/share/samba/panic-action %d
max log size = 1000
case sensitive = no
msdfs proxy = no
read only = no

[Download]
read only = no
guest ok = yes
browseable = yes
available = yes
public = yes
path = /data/shares/Download
comment = Software
create mask = 666
directory mask = 777


---

### Post by siebzehn on 2005-04-25
[QUOTE=g-joey]Hi segrewb,

you're right, that's exactly what I want to do.

I have extracted the *global* and *download* section of my *smb.conf*, maybe this will help you to help me :)[/QUOTE]
 Your smb.conf seems about right for the configuration you want.  Just check the Workgroup name and make sure you have the same setup in your windows clients.  Just to add a little more security, put the following line in the global section:

hosts allow = 192.168.

This is only if you use a 192.168 class network

Now, when the sign in box appears, just leave it blank and press ENTER.  Tell me what happens.

Another thing, make sure the path is the desired onw   /data/...   )  and make sure you set the right permissions for the directory

---

### Post by siebzehn on 2005-04-25
[QUOTE=siebzehn]Your smb.conf seems about right for the configuration you want.  Just check the Workgroup name and make sure you have the same setup in your windows clients.  Just to add a little more security, put the following line in the global section:

hosts allow = 192.168.

This is only if you use a 192.168 class network

Now, when the sign in box appears, just leave it blank and press ENTER.  Tell me what happens.

Another thing, make sure the path is the desired onw   /data/...   )  and make sure you set the right permissions for the directory[/QUOTE]
 Also, remember to restart the samba services after modifying smb.conf

Do this:

sudo /etc/init.d/samba restart

---

### Post by stoneguy on 2005-04-25
I'm a fan of putting /home on its own partition to preserve anything I want to save across reinstalls. So if you put Download in /home/someuser/Download instead, one more tweak to the [Download] section is to add these 3 lines:

forceuser = *someuser*
forcegroup = * associated group*
nt acl support = no

These will lock file and subdirectory ownership to a linux user for administration at the server.

(Based on example in Terpstra's _Samba-3 By Example_)

---

### Post by g-joey on 2005-04-26
[QUOTE=siebzehn]Just to add a little more security, put the following line in the global section:
hosts allow = 192.168.[/QUOTE]Yes, I already had that entry in my [global] section, but removed it during the tests.

[QUOTE=siebzehn]Another thing, make sure the path is the desired one /data/... ) and make sure you set the right permissions for the directory[/QUOTE]How stupid can one be? Both things were wrong on my server, though I'm absolutely sure I had set them correctly in the beginning. ](*,)

The permissions must have been changed when I copied the contents of my Windows share to the Linux share... But I cannot imagine why I have suddenly chosen a different path for the directory?!

Anyway, thanks a lot to anyone who helped me!

//Joe

---

### Post by siebzehn on 2005-04-27
[QUOTE=g-joey]Yes, I already had that entry in my [global] section, but removed it during the tests.

How stupid can one be? Both things were wrong on my server, though I'm absolutely sure I had set them correctly in the beginning. ](*,)

The permissions must have been changed when I copied the contents of my Windows share to the Linux share... But I cannot imagine why I have suddenly chosen a different path for the directory?!

Anyway, thanks a lot to anyone who helped me!

//Joe[/QUOTE]
 That happened to me once, that's how I know it can be a problem ;)

Happy sharing

---

### Post by jag_rulz on 2006-07-18
Hello.

I had the same problem for a number of months

make a user (sharer) and a group (sharer). go to the directory where the share is (/myshares/share1) and do 
[jag@linux /]$ chown sharer:sharer /myshares/share1
[jag@linux /]$ chown sharer:sharer /myshares/share1/*

add these lines to [global]

security = share
guest ok = yes
guest only = yes
guest account = ftp
nt acl support = no

add these lines to each share (in this case share1)
[share1]
comment = this is called share1
path = /myshares/share1
force user = sharer
force group = sharer

---

