---
title: "samba: access denied to public shares"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by goofdawg on 2007-03-06
Hello all.

All I want to do is get samba to share a folder publicly, so users can access it without logging in. From Windows, I can browse the machine's shares, but when I try to access the share, it says access is denied. Using "smbpasswd" i made an account "Guest" with no password because I think that's what windows uses to try to access the folders. This is driving me nuts, any input is very appreciated.

Here's my smb.conf:

[global]
security = user
restrict anonymous = no
guest ok = yes
domain master = no
preferred master = no
netbios name = Diesel
workgroup = Actioncommunism
server string = Diesel
max protocol = NT
ldap ssl = No
server signing = Auto

log file = /var/log/samba/log.master
max log size = 2000

#My public directory
[ftp]
case sensitive = no
msdfs proxy = no
read only = yes
path = /myfiles/

---

### Post by Mr. C. on 2007-03-07
There's a Samba HowTo here in the forums; it walks you through the steps.

If you decide to use no password, you'll have to change the correct options in smb.conf.

Read:

$  man  smb.conf

and search for guest

MrC

---

### Post by gradedcheese on 2007-03-07
> 
#My public directory
[ftp]
case sensitive = no
msdfs proxy = no
read only = yes
path = /myfiles/
**users = guest**


that is, when you want a user specified, you need to do so in the share config.  however this is different from the "guest ok = yes" part of it, but it might work (I'm assuming the user you made is literally 'guest')

---

### Post by goofdawg on 2007-03-08
ok, i reread the howto and the manual file. the howto doesn't say much about allowing guest users. this is my new smb.conf based on the one in the howto post, but it still doesn't work.

if anybody can spot my error, please tell me

```
[global]
    netbios name = Diesel
    server string = Diesel
    workgroup = Actioncommunism
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    guest ok = yes
    guest account = guest
    browseable = yes

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /myfiles/
    browseable = yes
    read only = yes
    guest ok = yes

```

---

### Post by Mr. C. on 2007-03-09
A couple of things, and this will be working fine.

1) Its probably going to be easier for you if workgroup is the same name on all the systems.  Windows XP defaults to WORKGROUP I belive, so unless you've changed your PCs, make the all the same.  Your guests will find them faster.

2) Your guest account is set to "guest".  I'd suggest changing guest to something like "smbguest" so that it will be clearer later.  Either way, did you create a "guest" group in /etc/group?  As you see below, with the name "guest" its a bit hard to tell what is your choice in values, vs. a command argument.  I"m going to use smbguest; change it if you want:

# groupadd smbguest
# useradd -g smbguest-d /dev/null -s /bin/false smbguest

3) You used the path /myfiles.  Its a very bad idea to put your share in the root directory, and not just for security reasons.  Don't use / as a dumping ground, it is too important in Unix/Linux.  If you care to know why, let me know and I'll explain.  Move that directory to somewhere like /home/guest.  

4) Make sure the /home/guest permissions are sufficient.  Try 755 if the share is going to be read-only, 777 otherwise.

5) Restart samba once these changes are made.  You don't need any smb passwords for this setup.

# /etc/init.d/samba restart

Now, browse your shares.  Note, Windows Networking can be very slow to converge on name changes.  If you changed your workgroup name, you may have to browse via IP address temporarily until the "master browser" catches up ( a major annoyance ).  Try (with your IP):

\\191.168.0.1

in Windows to browse the share if it doesn't show up.

Enjoy the browsing,
MrC

---

### Post by discord2000 on 2007-03-10
My first post! \o/

I had the same issue and fixed it by changing the security option to 'share' instead of the default 'user'

My smb.conf:
```
[global]
        security = SHARE

[MP3]
        path = /media/exthdd/Audio/MP3
        guest ok = Yes
```

Pretty basic, eh? Works a treat.

---

### Post by goofdawg on 2007-05-22
Still can't get guest access to work, no matter what! My smb.conf has been stripped down to the following:

```

[global]
  security = SHARE

[lacie]
  path = /media/LACIE
  guest ok = Yes

```

I can browse to the machine from an XP box, but when I double click on the share name I get: "\\computer\lacie is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
Network access is denied."

Any help much appreciated, this problem is driving me nuts.

---

### Post by noMScraig on 2007-05-25
I am with you...have tried everything...and get access is denied error...

bump

---

### Post by goofdawg on 2007-05-26
I'm sure somebody knows how to fix this... anybody?

bump

---

### Post by ruy_lopez on 2007-05-26
Create a world readable folder on your Ubuntu desktop. In smb.conf replace the Lacie pathname with the pathname of the new folder. (restart samba) Then try accessing the folder from Windows, see what happens. Just a quick test.

---

### Post by Nythain on 2007-05-26
i've found the minimal approach to smb.conf works best... here's what mine looks like, and it does what you want it to, so modify to suit your set up and it should do the trick
```

[global]
workgroup = WORKGROUP
security = share

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[stuff]
case sensitive = no
guest ok = yes
path = /data/
read only = no

```
notice the lack of size and excess crap options

---

### Post by discord2000 on 2007-07-18
Sorry for not replying sooner :)

I was getting access denied message at first because my shares were located on an NTFS partition and it was by default mounted with the wrong permissions. You may need to change your  /etc/fstab as I did.

---

### Post by Hekt0 on 2007-12-04
Hi All,

In my case it was enough to comment out the lines "msdfs proxy" like this:
-------
# msdfs proxy = no
-------

Important: it is not enough to set it to the different value, the whole line must be commented as such.

Good luck!

---

