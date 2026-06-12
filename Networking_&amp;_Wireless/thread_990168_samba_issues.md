---
title: "samba issues"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by stlouis1 on 2008-11-22
well, this is my problem. i just moved into the city, where i can get something other than dialup, so naturally, i figured its about time to update my system. everything updated smooth, no crash, i cleared my package cache and that was it. 2 days later,  one of my friends was here, we went to use my xbox running xbmc and noticed i couldn't access my smb shares from my desktop

so i tried restarting smb, my network daemons, the usual things i do when i have that problem, nothing worked. i then noticed that i can't access those shares while trying to browse them from the system sharing them.

but the really wierd thing is that if i boot my XP VM up on that system, i can access the shares from the VM, and i can access the shares from another xp machine on the network, and a vista system, but no luck from any type of linux host

i've tried downgrading smb with no success, so i just reinstalled the new version again, but its wierd. im wondering if its even a samba issue or a dependency or something? like i said, windows machines have no problem, but anything linux based, like the xbox, or my linux system, can barely see the shares let alone access them

my question is WTF, am i the only one, i need help

---

### Post by stlouis1 on 2008-11-23
no one has any suggestion on this issue with samba?

i setup ushare last night as a workaround, to stream via the xbox, but i seem to lack the ability to rewind or fast forward, i can only pause and play

apparently there may be a bug in libupnp according to this link which explains the problem i mentioned, its not marked as critical, no fix. at least it sort of works for now
[http://xbmc.org/trac/ticket/4046](http://xbmc.org/trac/ticket/4046)

---

### Post by stlouis1 on 2008-12-04
thought i would bump again. i have some log info, not sure it helps

this is from the xbmc log
```
01:19:37 M: 33660928   ERROR: SMBDirectory->GetDirectory: Unable to open directory : 'smb://xbox:xbox@URMOM-PC/Shared'
                             unix_err:'2' nt_err : 'c0000022' error : 'Access denied'
01:19:38 M: 33660928   ERROR: SMBDirectory->GetDirectory: Unable to open directory : 'smb://xbox:xbox@URMOM-PC/Stuff'
                             unix_err:'2' nt_err : 'c0000022' error : 'Access denied'

```

this is from my samba log folder, the file was xbox.log, im guessing it makes a log file per host name that tries to connect?
```

[2008/12/04 01:03:14,  0] smbd/password.c:authorise_login(865)
  authorise_login: rejected invalid user nobody
[2008/12/04 01:13:00,  0] lib/util_sock.c:read_socket_with_timeout(939)
[2008/12/04 01:13:00,  0] lib/util_sock.c:get_peer_addr_internal(1607)
  getpeername failed. Error was Transport endpoint is not connected
  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2008/12/04 01:13:40,  0] lib/util_sock.c:read_socket_with_timeout(939)
[2008/12/04 01:13:40,  0] lib/util_sock.c:get_peer_addr_internal(1607)
  getpeername failed. Error was Transport endpoint is not connected
  read_socket_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2008/12/04 01:19:33,  0] smbd/password.c:authorise_login(865)
  authorise_login: rejected invalid user nobody
[2008/12/04 01:19:42,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/04 01:19:42,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused

```

this is part of a log from a windows machine,i cut out some of the repetitive lines
```

[2008/12/01 17:23:52,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Movies initially as user tris (uid=501, gid=501) (pid 9496)
[2008/12/01 17:24:18,  0] smbd/password.c:authorise_login(865)
  authorise_login: rejected invalid user nobody
[2008/12/01 17:24:18,  0] smbd/password.c:authorise_login(865)
  authorise_login: rejected invalid user nobody
[2008/12/01 17:24:18,  0] smbd/password.c:authorise_login(865)
  authorise_login: rejected invalid user nobody
[2008/12/01 17:24:20,  0] smbd/nttrans.c:call_nt_transact_ioctl(2019)
  call_nt_transact_ioctl(0x900eb): Currently not implemented.
[2008/12/01 17:37:48,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/01 17:37:48,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/02 02:58:53,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/02 03:05:00,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Movies
[2008/12/02 15:01:28,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Shared initially as user tris (uid=501, gid=501) (pid 9737)
[2008/12/02 15:01:28,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Stuff initially as user tris (uid=501, gid=501) (pid 9737)
[2008/12/02 15:01:28,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Music initially as user tris (uid=501, gid=501) (pid 9737)
[2008/12/02 15:01:28,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Movies initially as user tris (uid=501, gid=501) (pid 9737)
[2008/12/02 15:10:22,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Shared
[2008/12/02 15:10:22,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Stuff
[2008/12/02 15:10:22,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Music
[2008/12/02 15:10:22,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Movies
[2008/12/03 11:51:41,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Shared initially as user tris (uid=501, gid=501) (pid 32096)
[2008/12/03 11:51:41,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Stuff initially as user tris (uid=501, gid=501) (pid 32096)
[2008/12/03 11:51:41,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Music initially as user tris (uid=501, gid=501) (pid 32096)
[2008/12/03 11:51:41,  1] smbd/service.c:make_connection_snum(1190)
  tristan (::ffff:192.168.1.14) connect to service Movies initially as user tris (uid=501, gid=501) (pid 32096)
[2008/12/03 12:05:41,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/03 12:26:41,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/03 18:51:41,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/03 18:51:41,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/12/03 18:58:49,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Movies
[2008/12/03 18:58:50,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Music
[2008/12/03 18:58:50,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Stuff
[2008/12/03 18:58:50,  1] smbd/service.c:close_cnum(1401)
  tristan (::ffff:192.168.1.14) closed connection to service Shared

```


this stuck out to me in teh samba.log
```

[2008/11/10 12:16:10,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2008/11/10 12:16:10,  0] nmbd/nmbd.c:process(646)
  Got SIGHUP dumping debug info.
[2008/11/10 12:16:10,  0] nmbd/nmbd_workgroupdb.c:dump_workgroups(281)
  dump_workgroups()
   dump workgroup on subnet    192.168.1.16: netmask=  255.255.255.0:
  	SERGEINC(1) current master browser = URMOM-PC
  		URMOM-PC 40849a03 ()
  		TRISTAN 40011003 ()
[2008/11/10 12:16:10,  0] nmbd/nmbd_serverlistdb.c:write_browse_list(361)
  write_browse_list: Fatal error - cannot find my workgroup WORKGROUP
[2008/11/10 12:16:10,  1] smbd/server.c:open_sockets_smbd(645)
  Reloading services after SIGHUP
[2008/11/10 12:16:10,  1] printing/printing.c:start_background_queue(1436)
  Reloading services after SIGHUP
[2008/11/10 12:16:10,  0] printing/print_cups.c:cups_connect(68)

```

i dont know what else i can provide at this point

---

### Post by superprash2003 on 2008-12-04
in your terminal type smbtree and post output

---

### Post by stlouis1 on 2008-12-04
```
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK

```

---

### Post by stlouis1 on 2008-12-04
bump?

---

### Post by superprash2003 on 2008-12-05
your samba seems messed up , you might want to reconfigure it [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by stlouis1 on 2008-12-05
i have reconfigured it, windows machines can use the shares just fine, why not the linux machine hosting the shares, or the xbox?

heres my smb.conf if it helps
```


[global]
   workgroup = SERGEINC
netbios name = URMOM-PC
   security = share
   log file = /var/log/samba/%m.log
   max log size = 50
   dns proxy = no 

[Shared]
path = /home/share
comment = shared
valid users = urmom tris Lorraine xbox
write list = urmom tris Lorraine xbox
admin users = urmom
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = yes
printable = no
share modes = no
locking = no

[Music]
path = /home/Music
comment = music
valid users = urmom tris Lorraine xbox
read only = yes
available = yes
browseable = yes
writable = no
guest ok = no
public = yes
printable = no
share modes = no
locking = no

[Movies]
path = /home/movies
comment = movies
valid users = urmom tris Lorraine xbox
read only = yes
available = yes
browseable = yes
writable = no
guest ok = no
public = yes
printable = no
share modes = no
locking = no

[Stuff]
path = /home/stuff
comment = Stuff
valid users = urmom tris Lorraine xbox
read only = yes
available = yes
browseable = yes
writable = no
guest ok = no
public = yes
printable = no
share modes = no
locking = no

```

---

### Post by bab1 on 2008-12-05
You have configured **[COLOR="Blue"]share[/COLOR]** security ```
[global]
   workgroup = SERGEINC
netbios name = URMOM-PC
   security = share [COLOR="Blue"]<--- here[/COLOR]
   log file = /var/log/samba/%m.log
   max log size = 50
   dns proxy = no 
```

Then you have required **[COLOR="Red"]user[/COLOR]** security ```
[Shared]
path = /home/share
comment = shared
valid users = urmom tris Lorraine xbox [COLOR="Red"]<--here[/COLOR]

```

That is why you are getting this:```


Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK


```

You can either remove the valid user directive or set the share security to user.

---

### Post by stlouis1 on 2008-12-05
seems that helps, actually, if i set it to user, i can't access the shares still. 

but if i leave it shared and comment out the valid user lines, it works. but thats leaving it kind of open no?

---

### Post by stlouis1 on 2008-12-05
seems that helps, actually, if i set it to user, i can't access the shares still. 

but if i leave it shared and comment out the valid user lines, it works. but thats leaving it kind of open no?

i also still get this
```
[urmom@urmom-pc ~]$ smbtree
Password:
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
```

is that normal?

---

### Post by bab1 on 2008-12-05
Well we seem to be on the right path.  Now it seems clear that the client has no login.  Are you using a no login host (XP home or W95/98 )?

If so then you are going to have to leave the security level at share.  This means that there is no checking for ID (authenticating), but you still have the file permissions to provide protection (authorization).

---

### Post by stlouis1 on 2008-12-05
theres 3 windows PC's, 2 vista, 1 XP, they all have logins and passwords on them, the 2 vista have the same login, Lorraine with password, the other XP machine has its own login, tris plus password.

we never used to have passwords on them until maybe a year ago when i had to add passwords to get sharing working again, i dont remember off hand

but even before i changed the smb.conf just now, the windows PC's could connect to the shares fine

then i have 3 xbox's with XBMC using login name and password "xbox". its the xbox's that couldn't connect to the shares before i just changed it. and my linux box

this is what im not understanding. windows PC's could access it, but not the xbox or linux PC, and the shares are hosted on the linux PC

but right now with the valid user lines commented out in my smb.conf and the security level set to share, everything works, its just left open. but everything used to work before any of these changes regardless, something was updated i think that broke it. because i had just moved to the city where i got highspeed and updated, the last updates before that were maybe 2 months ago now

---

### Post by bab1 on 2008-12-05
> **stlouis1 said:**
> theres 3 windows PC's, 2 vista, 1 XP, they all have logins and passwords on them, the 2 vista have the same login, Lorraine with password, the other XP machine has its own login, tris plus password.

we never used to have passwords on them until maybe a year ago when i had to add passwords to get sharing working again, i dont remember off hand

but even before i changed the smb.conf just now, the windows PC's could connect to the shares fine
If I get your drift, the Windows hosts are well behaved clients of the Samba sever.  All is well with them.  :-)
> 

then i have 3 xbox's with XBMC using login name and password "xbox". its the xbox's that couldn't connect to the shares before i just changed it. this is what im not understanding. windows PC's could access it, but not the xbox or linux PC, and the shares are hosted on the linux PCWell I'm no xbox expert, but I'll bet that there is no samba client built into the OS or XBMC.  Have you installed the samba client on the Linux box?  If the host is Ubuntu you can do this from Synaptics.  The package is smbclient>  

but right now with the valid user lines commented out in my smb.conf and the security level set to share, everything works, its just left open. but everything used to work before any of these changes regardless, something was updated i think that broke it. because i had just moved to the city where i got highspeed and updated, the last updates before that were maybe 2 months ago now
Yes, the updates that may have changed have to do with the way Nautilus handles the mounting of Samba shares.  If you are running this at home I would not worry about authentication.  The only users ore those that you know.  You should and I am sure you are running a perimeter FW in the router to keep strangers out.

---

### Post by stlouis1 on 2008-12-06
i'm pretty sure that XBMC has a smb client built into it, its open source after all, and it can add windows shares as media locations, im pretty sure its got some sort of smb client built into it.

and i used to be able to browse my network from this machine before, now sometimes it will see my workgroup, other times not, then something it will see the computers, othertime it will say the "smb://workgroup" as a path doesn't exist, but it will never show me the computers in my workgroup now, or let me browse a machine if i know the host name or ip address. the xbox as well can't browse the network, but if i give it a specific path like the ones that were already configured, like "smb://urmom-pc/movies" its fine, but if i try to browse teh workgroup from there, no go

somethings just screwed now, but the windows machines don't seem to be affected at all regardless

---

### Post by superprash2003 on 2008-12-06
have you added samba users to the file /etc/samba/smbusers ??

---

### Post by stlouis1 on 2008-12-07
yes, i've added samba users. if i go to the windows machine upstairs and map a drive as a different user, the xbox login works from there. but not from the xbox

---

### Post by Dilutu on 2008-12-07
Guess I am in the same boat.Every thing used to work fine until a few days ago and now the only machine that can access my ubuntu shared folders is my winxp computer...But no joy from  debian etch or ubuntu to themselves or xp...I even tried reinstalling my debian etch box and still no luck...

---

### Post by stlouis1 on 2008-12-14
i've sort of got mine resolved, not the way i would have preferred, but its working now.

i had to change security to shared, rather than user. now everything works

im wondering if its an issue with smbclient, because im pretty sure thats what xbox media center uses since its open source, and linu obviously.

my reason behind thinking that, is because when i was looking at the logs between the xbox and samba on my computer, it seemed that the smbclient wasnt sending the username and password and thats why it was being rejected and not connecting.

but i really know nothing about the inner workings, so thats just a guess. but i ran updates today on one of my boxes and there was a new version of smbclient installed, which is another reason why im guessing thats where the problem was

---

