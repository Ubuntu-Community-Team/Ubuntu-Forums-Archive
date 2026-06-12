---
title: "Creating Shares and permissions"
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by mirdragon on 2016-02-29
I've finally got my system running and have created some shares so can access via windows and other devices. I was originally getting an error when writing to the share even though had set this to read/write access.

Within WebMin I had to set permissions (0777) on the folder through FileManager before I could write  to the folder is this correct or should I have just be able to do it via the windows sharing under samba

thanks

---

### Post by afrugh on 2016-03-02
I was trying that samba today ! :D

I have ubuntu 15.10 wily but with ubuntu server guide (c)2014 as I couldn't find the new guide.

If you follow the instructions in that one chapter 18, you will experience some troubles.

In 15.10 *smb.conf *I could not find* security = user* so I didn't do it
*restart *does not work so u need to do it with *servcice smbd restart* and no need *restarting nmbd*

and *sudo chown nobody:nogroup /$path* also not working and it goes crazy as nothing works at all: permission denied all the time ! It doesn't matter you do *sudo *or not.

So  I created one directory in home (the same directory I added in *smb.conf*), then  *chmod o+w dirName*

It works fine.

---

### Post by Bucky Ball on 2016-03-02
*Thread moved to **Networking & Wireless**.*

---

### Post by Morbius1 on 2016-03-03
> **afrugh said:**
> 
In 15.10 *smb.conf *I could not find* security = user* so I didn't do it
You didn't need to do it since it's the default setting. The author of that HowTo is apparently unaware of that:
> tester1@vub1510:~$ testparm -sv | grep security
Load smb config files from /etc/samba/smb.conf
...
    security = USER

> and *sudo chown nobody:nogroup /$path* also not working and it goes crazy as nothing works at all: permission denied all the time ! It doesn't matter you do *sudo *or not.
The problem with that howto - and I'm being kind here - is that it needs to be used in the strict context of it's original assumption:
> This section      covers setting up a Samba server to share files with Windows clients.           The server will be configured to share files with any client on the network without prompting for a password.
** He has you create a folder - /srv/samba/share
** Makes the share guest read / writeable
** Then sets ownership to nobody:nogroup

 Abridged version: When the Windows user access the share his user name on Windows is automatically transmitted to the server. Since that user name is not in the samba password database "map to guest = Bad User" will convert that name to the guest user account. "guest account = nobody" ( don't look for this in smb.conf it's in the defaults ) will then set that user to "nobody". Since the ownership of the folder has already been set to "nobody" the permissions of that folder really could be set to 700 at this point.

There's two basic situations where that HowTo fails:

[1] The instant you set up another share and this time make it private so that a user must pass credentials to access that user is no longer a "Bad User" so he is no longer "nobody" but is in fact somebody. Write access will be denied to this user.

[2] At best this is a HowTo for a samba Server ( with a big "S" ). If people use this in a home network so Sally can share files with Sam you end up in a situation where Sam can access the Samba share but Sally cannot access the shared folder since she is not "nobody"
> *restart *does not work so u need to do it with *servcice smbd restart* 
You are correct. The restart as described in the HowTo will not work in 15.10 because 15.10 is in a more or less transitional state to systemd and systemd likes to do a "sudo systemctl restart smbd'
>   and no need *restarting nmbd*
Well, the only reason he has you restart nmbd is because he thinks he is resetting the workgroup name - completely unaware that that too is in the defaults:
> tester1@vub1510:~$ testparm -sv | grep workgroup
Load smb config files from /etc/samba/smb.conf
...
    workgroup = WORKGROUP

---

