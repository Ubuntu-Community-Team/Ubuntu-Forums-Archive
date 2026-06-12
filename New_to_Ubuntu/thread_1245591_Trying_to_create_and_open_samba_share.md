---
title: "Trying to create and open samba share"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Pure_Divs on 2009-08-20
Hello all! As you might expect I'm new to Linux and am eager to learn. So any help you can offer would be greatly received ^_^

So, I'm currently in the process of making a file server for the house, undoubtedly this will assume other functions later, but one step at a time. So I have installed Ubuntu-Server, got SSH running and now controlling the box via putty from my desktop.

The other machines on the network are all windows (XP, Vista and 7) and I was informed Samba would be the way to go to get some file sharing online. So i've got samba installed, followed a few bits of advice on threads to get a share up and running but i seem to be missing some key bits of information.

I have modified the etc/samba/smb.conf file so it reads:

[global]
        security = share

[datastore]

        comment = OMG DATAS!!!
        path = /datastore
        readonly = no
        public = yes

i restart samba, and try "smbclient -L localhost" to see if my share appears... sure enough it dosnt.

The path "/datastore" exists, but i see mentions in guides to mounting it, but no actual instructions on how to do it properly. The linux file system is a bit alien to me, so if you have any suggestions on how to better organise the mount/s please spill the beanz.

SO... If you know of any guides to explain the process in full or can help in any way, that would be great.

Thanks in advance,

/Divs

---

### Post by sandyd on 2009-08-20
try
```

sudo apt-get install system-config-samba
sudo system-config-samba
```

ops wait. your on ubuntu server.

perhaps?
```

[Shares]
        path = /patch/to/dir
        writeable = yes
;       browseable = yes
        guest ok = yes


```

you also might want
```

[global]
workgroup = name_of_workgroup
log file = /var/log/samba/log.%m
encrypt passwords = false
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

---

### Post by sandyd on 2009-08-20
nvm. chrome made me double post.

---

### Post by Pure_Divs on 2009-08-20
thanks for the quick reply,

after "smbclient -L localhost" i get:

```
tree connect failed: SUCCESS - 0
```

:(

---

### Post by Pure_Divs on 2009-08-20
This box wont be doing any printing, is the [printing] and [print$] really needed?

---

### Post by sandyd on 2009-08-20
no. if your not printing

---

### Post by Pure_Divs on 2009-08-20
still no joy. I'm assuming that i dont have to worry about mounting anything for these folders to be shared?

---

### Post by sandyd on 2009-08-20
try

smbclient -L IP_ADDRESS_OF_MACHINE

put the external ip address there, not the localhost. 

and perhaps
```

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
        encrypt passwords = no

```

---

### Post by Pure_Divs on 2009-08-20
tried the host IP and loop back ip, i'm guessing i don't need to add the hashed content, as its hashed out.. meaning it int read when the file is run.

Either way, still no joy

---

### Post by sandyd on 2009-08-20
shot in the dark, but have you tried to access the share from a desktop machine?
i got the same error as you. however, i viewed it from another desktop... and i could still see the share and everything inside.

---

### Post by sandyd on 2009-08-20
and i found some more suff...
```

[global]
usershare allow guests = yes
security = share
guest ok = yes
guest account = your_username_here
client lanman auth = yes
client plaintext auth = yes

```
make sure that the directories your sharing are chown'ed to the guest account

p.s. this may sound stupid, but did you restart samba after you changed the config?

---

### Post by sandyd on 2009-08-20
nvm. posted twice AGAIN

---

### Post by jonandrews on 2009-08-21
I have put some step-by-step illustrated guides on networking in a mixed Ubuntu / Windows network on my website:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Pure_Divs on 2009-08-21
it seems that the shares do work from the other machines, despite Samba reporting they don't. my smb.conf simply reads:

```

[global]
        security = share
[datastore]

        comment = Repository for STUFF
        path = /datastore
        writable = yes
        public = yes
        guest ok = yes

```

I will tinker with one of the shares to practice what security options i can add.

Thanks for your help ^_^

---

