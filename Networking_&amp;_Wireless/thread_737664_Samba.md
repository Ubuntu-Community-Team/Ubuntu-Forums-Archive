---
title: "Samba"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2008-03-27
I've got O'Reilly's Using Samba book, Samba fro Dummies, Linux+, PC World's Linux Solutions, & Ubuntu Linux Bible. You'd think that  I can get my samba file server to work like I want it.

1. This is the primary file server on the workgroup network. Name resolution seems to be iffy, so I'd like to make it the primary master with OS level higher than all the other XP machines. Findint the share by IP is far more reliable than my name, but I'd like to get the name to work as well.

2. There are four shares, "Open" should be wide open for anyone to put anything in it. No restrictions. "Media" should be read only for everyone. "Mandi" should be a share for user named mandi to have rwx but not browesable for other users. Tony" should be a share for user named tony to have rwx but not browesable for other users.

Please help me design a smb.conf that functions properly.

My attempt includes

```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
prefered master = yes
local master = yes
os level = 33
encrypt password = yes

[Open]
path = /media/md3/shares/open
guest ok = yes
browseable = yes
read only = no
public = yes

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
valid users = mandi

```

Thanks

---

### Post by Eiríkr on 2008-03-27
Your global options look good.  You might try adding [font=courier]domain master = yes[/font] as well to see if that improves name resolution reliability.  

To properly set up guest access for your [font=courier][Open][/font] share,, you'll also want to add the [font=courier]guest account = USERNAME[/font] global option to specify which Ubuntu username will act as the guest user.  If this isn't specified, it defaults to the "nobody" user, which is generally very limited.  Make sure that whatever username you use for this has the needed filesystem permissions on the shared directory.  

You'd do the same for your proposed [font=courier][Media][/font] share, only you would leave the [font=courier]read only[/font] share definition option set to "yes" (the default, so you can leave it out if you want), and also make sure the guest user only has read / execute permissions on the shared directory.  

For the two user-specific shares, what you have here for [font=courier][mandi][/font] looks pretty good.  You can set the [font=courier]browsable[/font] option to "no" to keep people from seeing it, but then even the specific users will have to know it's there -- they won't see it either.  But even if [font=courier]browsable = yes[/font], only those users with read / execute permissions on the shared directory will be able to open it anyway, and with the [font=courier]valid users[/font] option, you can limit that entirely to just the listed usernames.  Again, make sure those usernames have the required permissions on the filesystem, as filesystem permissions are the ultimate delimiter -- you can have [font=courier]writable = yes[/font] in your smb.conf file, but if the relevant username has no write permissions on the shared directory, they won't be able to write.  

----------

As you first set up your Samba server, start with a simple share open to everyone so you can check for the obvious "is it visible" and "can I get into it" tests.  This looks like what you're doing, which is good.  :)  Then once you have name resolution and share visibility figured out, proceed to defining the specific shares with the more finely tuned options you're looking for.  The man page is a great resource while you work on this.  You can either type [font=courier]man smb.conf[/font] in a terminal, or view the online page [here]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  

HTH,

Eiríkr

---

### Post by ant2ne on 2008-03-29
smb.conf
```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
prefered master = yes
local master = yes
domain master = yes
os level = 33
encrypt password = yes
guest account = guest


[Open]
path = /media/md3/shares/open
guest ok = yes
guest account = guest
browseable = yes
read only = no
public = yes

[ant2ne]
path = /media/md3/shares/ant2ne
browseable = yes
read only = no
valid users = ant2ne

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
valid users = mandi

[Media]
path = /media/md3/shares/media
guest ok = yes
browseable = yes
read only = no

```

smbpasswd
```
ant2ne@2ne-buntu:/media/md3/shares$ sudo cat /etc/samba/smbpasswd

ant2ne:1000:AAD3B435B51404EEAAD3B435B51404EE:31D6CFE0D16AE931B73C59D7E0C089C0:[UX         ]:LCT-47EA3869:
mandi:1001:55D8DFF289AFEBED5E57FC0295493699:FC97783B546CC1C1DD35503CFAB446FD:[U          ]:LCT-47EAEA25:
ant2ne@2ne-buntu:/media/md3/shares$ 

```

permissions
```
ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 32
drwxr-xr-x  4 ant2ne root   4096 2008-03-25 16:58 ant2ne
drwxrwxrwx  2 ant2ne root   4096 2008-03-24 19:56 boys
drwxrwxrwx 10 ant2ne root   4096 2008-03-24 19:50 mandi
drwxr-xr-x  8 ant2ne root   4096 2008-03-24 21:13 media
drwxr-xr-x 10 ant2ne root   4096 2008-03-24 19:46 MSwin.stuff
drwxrwxrwx  3 ant2ne root   4096 2008-03-26 18:19 open
drwxr-xr-x  2 ant2ne root   4096 2008-03-24 19:56 temp
drwxr-xr-x 17 ant2ne ant2ne 4096 2008-03-29 09:53 WinMy
ant2ne@2ne-buntu:/media/md3/shares$
``` 

results
Logged in as Mandi on an XP-VM RAID1 File Server (2ne-buntu) does show up in my workgroup list. But I can't bowse a list of shares, not even the Open share.
```
\\2ne-buntu is not accessible. You might not have permission to use th network resource. Contact the administrator of the server to find out if you have access permissions.

The network path was not found.
```

---

### Post by Eiríkr on 2008-03-30
Looking over your smb.conf file, I noted the following:

[B][Open]
   guest account = guest[/B]

This parameter is only allowed in the [global] section, and might be screwing up your share definition.

You might also consider adding the line **wins support = yes** to your [global] section; this might help with name resolution.  

----------

From my XP machine, here's what my shares look like from the command line:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\>net view
Server Name            Remark

-------------------------------------------------------------------------------
\\WINXP                WINXP
\\UBUNTU               UBUNTU server
The command completed successfully.


C:\>net view ubuntu
Shared resources at UBUNTU

UBUNTU server

Share name        Type  Used as  Comment

-------------------------------------------------------------------------------
UserA's Documents Disk  Z:
UserB's Documents Disk
Music             Disk  M:
shared            Disk           Shared directory with forced group.
The command completed successfully.


C:\>
```

Do these commands work for you from your XP machines?

Cheers,

Eiríkr

---

### Post by ant2ne on 2008-03-30
added wins support = yes & guest account = guest only exists in global section.

New smbpasswd 
```
ant2ne@2ne-buntu:/media/md3/shares$ sudo cat /etc/samba/smbpasswd

ant2ne:1000:AAD3B435B51404EEAAD3B435B51404EE:31D6CFE0D16AE931B73C59D7E0C089C0:[UX         ]:LCT-47EA3869:
mandi:1001:55D8DFF289AFEBED5E57FC0295493699:FC97783B546CC1C1DD35503CFAB446FD:[U          ]:LCT-47EAEA25:
guest:0:A0E150C75A17008EAAD3B435B51404EE:823893ADFAD2CDA6E1A414F3EBDF58F7:[U          ]:LCT-47EF955B:
ant2ne@2ne-buntu:/media/md3/shares$
```

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\mandi>net view
Server Name            Remark

-------------------------------------------------------------------------------
\\2NE                  Samba 3.0.26a
\\2NE-BUNTU            RAID1 File Server
\\CYGNE1000
\\CYGNE3               Mandi Laptop
\\XP-VM-01
The command completed successfully.


C:\Documents and Settings\mandi>net view 2ne-buntu
System error 53 has occurred.

The network path was not found.


C:\Documents and Settings\mandi>
```

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\mandi>ping 2ne-buntu

Pinging 2ne-buntu.CYGNEHOME [192.168.1.100] with 32 bytes of data:

Reply from 192.168.1.100: bytes=32 time<1ms TTL=64
Reply from 192.168.1.100: bytes=32 time<1ms TTL=64
Reply from 192.168.1.100: bytes=32 time<1ms TTL=64
Reply from 192.168.1.100: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.1.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\Documents and Settings\mandi>
```

---

### Post by Iowan on 2008-03-30
Referencing my (somewhat dated) Samba Unleashed book, there's a section on **map to guest=**.  Default is **Never** (Other options are **Bad User** and Bad **Password**).  > If it's **Never**, no share is guest accessible unless it's **guest only=yes.**

---

### Post by ant2ne on 2008-03-30
Plot thickins

On a whim I tried to remove --purge samba and reinstall. This is what I got. ```
ant2ne@2ne-buntu:/media/md3/shares$ sudo apt-get install samba samba-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba samba-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7220kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 112994 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_3.0.26a-1ubuntu2.3_amd64.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_3.0.26a-1ubuntu2.3_amd64.deb) ...
Setting up samba-common (3.0.26a-1ubuntu2.3) ...

Setting up samba (3.0.26a-1ubuntu2.3) ...
Generating /etc/default/samba...
tdbsam_open: Converting version 0 database to version 3.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
Importing account for root...ok
Importing account for daemon...ok
Importing account for bin...ok
Importing account for sys...ok
Importing account for sync...ok
Importing account for games...ok
Importing account for man...ok
Importing account for lp...ok
Importing account for mail...ok
Importing account for news...ok
Importing account for uucp...ok
Importing account for proxy...ok
Importing account for www-data...ok
Importing account for backup...ok
Importing account for list...ok
Importing account for irc...ok
Importing account for gnats...ok
Importing account for nobody...ok
Importing account for dhcp...ok
Importing account for syslog...ok
Importing account for klog...ok
Importing account for messagebus...ok
Importing account for hplip...ok
Importing account for avahi-autoipd...ok
Importing account for avahi...ok
Importing account for haldaemon...ok
Importing account for gdm...ok
Importing account for ant2ne...ok
Importing account for mandi...ok
Importing account for guest...ok
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons                                                [ OK ] 

ant2ne@2ne-buntu:/media/md3/shares$ 
```

I wasn't observant on my original install, so I don't know if I got this error then. But it seems that each time I try to remove and install I get this error, so it is a good chance. Now what?

---

### Post by ant2ne on 2008-03-30
Ok, I feel like I'm talking to myself here, but...

I removed and re-installed with synaptic and suddenly samba works. Sort of. ant2ne works as he should.  mandi can access only the open and media, and guest can't see anything. So this is some mild progress. How do I troubleshoot users?

---

### Post by Iowan on 2008-03-30
> **ant2ne said:**
> Ok, I feel like I'm talking to myself here, but...Keep talking - I check back periodically (not that I'm gonna be able to fix the problem). If nothing in the smb.conf or filesystem has changed...
Try adding **guest only=yes** to **open**
**sudo chown mandi /media/md3/shares/mandi** - right now **ant2ne** is the owner.

But **ant2ne** is owner of **media** and **open**, too...

---

### Post by ant2ne on 2008-03-30
I created a user mkc. 

sudo smbpasswd -a mkc
sudo smbpasswd -e mkc

I created a group sambausers and put guest, ant2ne, mkc & mandi in it. mkc has the exact same problems that mandi does. That is, no access to anything.

ant2ne still behaves as he should.

```
ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 32
drwxr-xr-x  4 ant2ne sambausers 4096 2008-03-30 18:06 ant2ne
drwxrwxrwx  2 ant2ne sambausers 4096 2008-03-24 19:56 boys
drwxrwxrwx 10 mandi  sambausers 4096 2008-03-24 19:50 mandi
drwxr-xr-x  8 ant2ne sambausers 4096 2008-03-30 18:07 media
drwxr-xr-x 10 ant2ne sambausers 4096 2008-03-24 19:46 MSwin.stuff
drwxrwxrwx  3 ant2ne sambausers 4096 2008-03-30 18:06 open
drwxr-xr-x  2 ant2ne sambausers 4096 2008-03-24 19:56 temp
drwxr-xr-x 17 ant2ne sambausers 4096 2008-03-29 09:53 WinMy
ant2ne@2ne-buntu:/media/md3/shares$ 
```

current smb.conf
```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
prefered master = yes
local master = yes
domain master = yes
os level = 33
encrypt passwords = yes
guest account = guest


[Open]
path = /media/md3/shares/open
guest ok = yes
guest only = yes
browseable = yes
read only = no
public = yes

[ant2ne]
path = /media/md3/shares/ant2ne
browseable = yes
read only = no
valid users = ant2ne,mkc

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
valid users = mkc,ant2ne

[Media]
path = /media/md3/shares/media
guest ok = yes
browseable = yes
read only = yes
valid users = @sambausers
write list = ant2ne,mandi
```

---

### Post by Iowan on 2008-03-30
> **ant2ne said:**
>  mkc has the exact same problems that mandi does. That is, no access to anything. **mandi** now has access to nothing?  I notice mandi is no longer a valid user for the [mandi] share, but  should have access to [Media] and [Open].

BTW, I presume you restarted Samba after editing the smb.conf file?

---

### Post by ant2ne on 2008-03-30
i seem to have a lot of these

 cat /var/log/samba/log.smbd


```
[2008/03/30 20:54:05, 0] smbd/service.c:make_connection_snum(1003)
  '/media/md3/shares/open' does not exist or permission denied when connecting to [Open] Error was Permission denied
[2008/03/30 20:54:05, 0] smbd/service.c:make_connection_snum(1003)
  '/media/md3/shares/open' does not exist or permission denied when connecting to [Open] Error was Permission denied
[2008/03/30 20:54:05, 0] smbd/service.c:make_connection_snum(1003)
  '/media/md3/shares/open' does not exist or permission denied when connecting to [Open] Error was Permission denied
[2008/03/30 20:54:26, 1] smbd/service.c:make_connection_snum(1033)
  xp-vm-01 (192.168.1.125) connect to service Media initially as user ant2ne (uid=1000, gid=1000) (pid 31665)
[2008/03/30 20:54:37, 1] smbd/service.c:close_cnum(1230)
  xp-vm-01 (192.168.1.125) closed connection to service Media
ant2ne@2ne-buntu:/media/md3/shares$ 
```

---

### Post by Eiríkr on 2008-03-30
Given your current smb.conf file, you have no [font=courier]guest account[/font] option included in your [font=courier][global][/font] section, meaning Samba will fall back to the default "nobody" account, which only has filesystem permissions on the [font=courier]./boys[/font], [font=courier]./mandi[/font], and [font=courier]./open[/font] directories (as part of the "other" permissions grouping, the final "rwx" triplet shown in your [font=courier]ls -l[/font] results).  

For Samba setups using guest access, you need to set the [font=courier]map to guest[/font] option, as noted in [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPTOGUEST") (emphasis mine):

> **Note that this parameter is needed to set up "Guest" share services when using *[FONT="Courier New"]security[/FONT]* modes other than share and server.** This is because in these modes the name of the resource being requested is *not* sent to the server until after the server has successfully authenticated the client so the server cannot make authentication decisions at the correct time (connection to the share) for "Guest" shares. This parameter is not useful with *[FONT="Courier New"]security = server[/FONT]* as in this security mode no information is returned about whether a user logon failed due to a bad username or bad password, the same error is returned from a modern server in both cases.

Since you are using a "user" security mode, it sounds like you'll need to set this option.  

Within your share definitions, I think usernames need to be separated by a comma *and* a space, at least judging from the examples shown for the [[FONT=courier]valid users[/font]]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VALIDUSERS") and [[FONT=courier]write list[/FONT]]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITELIST") options.

HTH,

Eiríkr

---

### Post by ant2ne on 2008-03-31
```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
prefered master = yes
local master = yes
domain master = yes
os level = 33
encrypt passwords = yes
guest account = guest
map to guest = bad password


[Open]
path = /media/md3/shares/open
guest ok = yes
guest only = yes
browseable = yes
read only = no
public = yes

[ant2ne]
path = /media/md3/shares/ant2ne
browseable = yes
read only = no
valid users = ant2ne, mkc, mandi

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
;valid users = mkc

[Media]
path = /media/md3/shares/media
guest ok = yes
browseable = yes
read only = yes
valid users = @sambausers
write list = ant2ne, mandi
```

that doesn't seem to change anything. My windows user somebloke, who doesn't exist on the linux machine can browse to and view the shares, but can not navigate to any of the shared 'folder's. Oddly, when I try to access ant2ne share, it prompts me for a user name and password. The rest it merely says "blah blah permissions to use blah blah access permissions blah blah network path not found."  Mandi still can't do anything. ant2ne can access anything except the open share. Go figure.

I would really like to get this stuff figured out. In my opinion wine and samba will be keys to beginning of the end of Windows, and the rise of Linux.  I'm not giving up anytime soon. I'll be a samba expert before it is through. Ya'll might be tired of me talking though.

---

### Post by ant2ne on 2008-03-31
Plot thickins.

I can't print to my windows xp home print server. If I goto Places -> Network -> Windows Network I see nothing. I can't Places-> Connect to Server any machine except my other (old) linux samba server box. Windows hates me.

My firewall is on Permissive by default for outbound traffic.

Ideas?

---

### Post by Eiríkr on 2008-04-01
For the [font=courier]map to guest[/font] option, try using the value [font=courier]Bad User[/font] instead.  

> **ant2ne said:**
> that doesn't seem to change anything. My windows user somebloke, who doesn't exist on the linux machine can browse to and view the shares, but can not navigate to any of the shared 'folder's. Oddly, when I try to access ant2ne share, it prompts me for a user name and password. The rest it merely says "blah blah permissions to use blah blah access permissions blah blah network path not found."  

This part makes sense, actually -- guest access as you have it configured currently allows guests to see the shared folders, but of your four share definitions, [font=courier][Open][/font], [font=courier][ant2ne][/font], [font=courier][mandi][/font], and [font=courier][Media][/font], only [font=courier][Open][/font] allows guest access.  The problem here is that you have no [font=courier][global][/font] option specifying which guest account to use -- so the server defaults to the "nobody" username, which is practically guaranteed to have none of the filesystem permissions required to read / write / execute that shared directory (/media/md3/shares/open).  Forgetting to specify the guest user account is probably *the* most common error in any guest-access Samba setup.  The upshot is that your Windows user "somebloke" can see the shares, but the underlying guest account user "nobody" cannot open any of them.  

The bit about the [font=courier][ant2ne][/font] share requesting login authentication also makes some sense, as this is the only share fully locked down with a username-defined valid users list.  (Though theoretically Samba should also prompt for login and password for the [font=courier][Media][/font] share too... :confused:)


> **ant2ne said:**
> Mandi still can't do anything. 

Does this username have the required filesystem permissions to actually access the shared [font=courier]/media/md3/shares/mandi[/font] directory?  If so, how are you trying to access?  If via XP, XP is overly aggressive in caching share login authentication data, and it's possible you're trying to authenticate with different credentials than you intend.  Have a look at [thread=720889]KennedyM's HOWTO[/thread] regarding the required alterations to ensure Windows stops being so godawful.  


> **ant2ne said:**
> ant2ne can access anything except the open share. Go figure.

User ant2ne cannot access the [font=courier][Open][/font] share because this share is defined with the option [font=courier]guest only = yes[/font], which means you aren't accessing as "ant2ne", but rather as the guest user -- "nobody" in this case -- and are therefore subject to whatever filesystem permissions the guest user has to the shared directory (probably none in this case).  


> **ant2ne said:**
> I would really like to get this stuff figured out. In my opinion wine and samba will be keys to beginning of the end of Windows, and the rise of Linux.  I'm not giving up anytime soon. I'll be a samba expert before it is through. Ya'll might be tired of me talking though.

Good luck!  I'm being serious, not facetious.  :)  And go right ahead and post.  For reference, the [online man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") is an indispensable resource as you work on building up your Samba expertise.  Welcome to the fold, and may you be Windows-free as soon as possible!  :D

(NB -- If you have no Windows machines to share with, NFS or SFTP offer much easier and more Unixy ways of sharing files.  It's only Windows that requires all the fugly complexity of Samba.)

Cheers,

Eiríkr

---

### Post by ant2ne on 2008-04-02
I was on driving my way home from class and talking to my wife who was at home. We were just chatting along when she said, "Why did the printer just print?" I said "I dunno that is weird." She goes and looks at the page and it was an Ubuntu test page. I assume it was the one I sent on the day of my last post.

My current smb.conf
[open] no longer had guest only
map to guest is now bad user

```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
prefered master = yes
local master = yes
domain master = yes
os level = 33
encrypt passwords = yes
guest account = guest
;map to guest = bad password
map to guest = bad user


[Open]
path = /media/md3/shares/open
guest ok = yes
;guest only = yes
browseable = yes
read only = no
public = yes

[ant2ne]
path = /media/md3/shares/ant2ne
browseable = yes
read only = no
valid users = ant2ne, mkc, mandi

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
valid users = mkc, mandi

[Media]
path = /media/md3/shares/media
guest ok = yes
browseable = yes
read only = yes
valid users = @sambausers
write list = ant2ne, mandi
```

These permissions should throw the doors wide open for everyone.  ant2ne, guest, mandi, mkc are all linux users who belong to the group sambausers. (I don't know of a CLI to gie me proof of this, but the GUI says so.)
> ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 32
drwxr-xr-x  4 ant2ne sambausers 4096 2008-03-30 18:06 ant2ne
drwxrwxrwx  2 ant2ne sambausers 4096 2008-03-24 19:56 boys
drwxrwxrwx 10 mandi  sambausers 4096 2008-03-24 19:50 mandi
drwxr-xr-x  8 ant2ne sambausers 4096 2008-03-30 18:07 media
drwxr-xr-x 10 ant2ne sambausers 4096 2008-03-24 19:46 MSwin.stuff
drwxrwxrwx  3 ant2ne sambausers 4096 2008-03-30 18:06 open
drwxr-xr-x  2 ant2ne sambausers 4096 2008-03-24 19:56 temp
drwxr-xr-x 17 ant2ne sambausers 4096 2008-03-29 09:53 WinM

[http://ubuntuforums.org/showthread.php?t=720889](http://ubuntuforums.org/showthread.php?t=720889) Since I'm running a VM as my XP Client, i went ahead and made those changes. That seems like a band aid fix, and I don't like band aid fixes. I like things to just work. I suppose it would be easy enough to write a Win batch script to make this tweak.

Logged in with SomeBloke: Had no access to [open] or [media]. He was prompted for a Username and Password to access [Mnadi] and [ant2ne].  [Mandi] Failed every password, [ant2ne] passed with ant2ne's password.

Logged in with Mandi: Everything was not accessible immediatly. It never prompted me for a username and password

Logged in with ant2ne: Got into everything except mandi without a password prompt. [mandi] prompted for a password but didn't take anything.



> Windows-free as soon as possible! 
Me, I am Windows free, my wife (mandi) isn't. And i'm surrounded by Windows at my work place. I'm responisble for around 1000 Dells running Windows. I wish they were all Ubuntu machines. 


I think that the XP cache fix helped. But was not the solution to my problem. What next?

---

### Post by Eiríkr on 2008-04-03
CLI way of checking group membership:
```
grep GROUPNAME /etc/group
```
Or just [font=courier]cat /etc/group[/font] to see all groups and memberships.  

----------

Looking over your conf file:

**[global]**

Looks like you have a typo -- there should be two Rs in "prefe**_rr_**ed" for your [font=courier][preferred master]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PREFERREDMASTER") = yes[/font] line.  

For [font=courier][map to guest]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPTOGUEST")[/font], the man page section uses title case for the value.  So rather than "bad user", try "Bad User" and see if that works any better when accessing via the SomeBloke username.  


**[Open]**

Minor quibble, but you've got both [font=courier][guest ok]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK") = yes[/font] and [font=courier][public]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PUBLIC") = yes[/font].  These are synonyms, and you only need one or the other.  Having both is probably okay, so long as they don't contradict.  


[B][ant2ne]
[mandi][/B]

These both look fine.  User ant2ne's failure to access the [mandi] share actually makes sense here, since ant2ne is not included in the share's [font=courier]valid users[/font] list.  However, user Mandi's failure to access anything is most puzzling; all I can think is that it might be a Windows caching problem, especially given the lack of any authentication prompt.  Was user Mandi prompted for username and password after clearing out the cache?  Or, is there any chance the username might have been disabled in the Samba password file?  (Run [font=courier]grep -i mandi /etc/samba/smbpasswd[/font] to make sure the username is in there.)


**[Media]**

Here, you have both [font=courier]guest ok = yes[/font], and [font=courier]valid users = @sambausers[/font], which would seem to be contradictory.  The [font=courier]valid users[/font] option restricts access to just those users, excluding guests.  I don't know which option takes precedence, but I suspect this might be the cause of some of the strange behaviour.  Try deleting (or commenting out) one of these two lines.

----------

HTH,

Eiríkr

---

### Post by timn91 on 2008-04-06
> **ant2ne said:**
> ```
mandi:1001:55D8DFF289AFEBED5E57FC0295493699:FC97783B546CC1C1DD35503CFAB446FD:[U          ]:LCT-47EAEA25:
```
ha ha your password is [color=blue]everclear[/color]

---

### Post by ant2ne on 2008-04-07
> **timn91 said:**
> ha ha your password is [color=blue]everclear[/color]

That is correct, her password is everclear. I know, it is dumb. Can you get ant2ne's?

---

### Post by ant2ne on 2008-04-08
Same results. Mandi can't do anything, Ant2ne can do anything except [mandi]. ant2ne is prompted for a password to access [mandi] but using mandi's loggin and password fails. I then added ,ant2ne to the valid user lists of [mandi] and he had access. It seems ant2ne is working perfectly. Somebloke can't access anything except [ant2ne] because he is prompted for user name and password, which I supply. mandi can't access anything either. Not even mandi and not even ant2ne

> ant2ne@2ne-buntu:~$ sudo grep -i mandi /etc/samba/smbpasswd
mandi:1001:55D8DFF289AFEBED5E57FC0295493699:FC97783B546CC1C1DD35503CFAB446FD:[U          ]:LCT-47F0430F:
ant2ne@2ne-buntu:~$ 

Current smb.conf
```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
security = user
preferred master = yes
local master = yes
domain master = yes
os level = 33
encrypt passwords = yes
guest account = guest
;map to guest = bad password
map to guest = Bad User


[Open]
path = /media/md3/shares/open
guest ok = yes
;guest only = yes
browseable = yes
read only = no

[ant2ne]
path = /media/md3/shares/ant2ne
browseable = yes
read only = no
valid users = ant2ne, mkc, mandi

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no
valid users = mkc, mandi, ant2ne

[Media]
path = /media/md3/shares/media
guest ok = yes
browseable = yes
read only = yes
;valid users = @sambausers
write list = ant2ne, mandi
```

---

### Post by Eiríkr on 2008-04-08
You say "somebloke" can only access [ant2ne]; is this because you are logging in with the "ant2ne" username?  If "somebloke" logs in as "somebloke", he should *only* have access to [Open] and [Media] (where "guest ok = yes"), and then only with whatever permissions have been granted to username "guest".  

The fact that ant2ne logging in from Windows and using mandi's username and password fails out would seem to suggest that the "mandi" account might have been disabled somehow in the Samba password file.  Just in case, try the following to enable:
```
sudo smbpasswd -e mandi
```

Note from the **smbpasswd** man page:
> -e
This option specifies that the username following should be **enabled** in the  local  smbpasswd  file,  if  the account was previously disabled. If the account was not disabled this option has no effect. Once the account is enabled then the user will  be  able  to authenticate via SMB once again.

If  the  smbpasswd  file is in the &#8217;old&#8217; format, then smbpasswd will FAIL to enable the account. See **smbpasswd**(5) for details on the &#8217;old&#8217; and new password file formats. 

This option is only available when running smbpasswd as root.

If your smbpasswd file is a copy from an old installation, you might run into problems, but otherwise you should be fine.

Cheers,

Eiríkr

---

### Post by ant2ne on 2008-04-09
Yes, somebloke is prompted for ant2ne's user name password which i supply.

```
ant2ne@2ne-buntu:~$ sudo smbpasswd -e mandi
[sudo] password for ant2ne:
Sorry, try again.
[sudo] password for ant2ne:
Enabled user mandi.
ant2ne@2ne-buntu:~$ 

```(notice the fat fingers.)
I have done this multiple times; but for you I did it again. And still  mandi can still NOT access anything.

I've been thinking... In my Server03 class, we discussed Share permissions and NTFS permissions. And how most admins ignore the share permissions and focus on the NTFS permissions. I don't know how this would apply in a workgroup setting, but could I (should I) do the same thing with Samba? Open up all of the smb.conf restrictions, but restrict the shares by file system permissions? That seems to make sense to me. (maybe I'm trying to take the easy way out, DOH!!)

That still doesn't explain why mandi can't access the open or media shares.

---

### Post by Eiríkr on 2008-04-10
I don't suppose you've also tried removing the smbpasswd file (mv-ing it to back it up in case you need it later, naturally :)) and rebuilding it from scratch?

And as for file system perms versus Samba perms, I generally feel it's best to start with the filesystem perms, and then use any Samba perms on top as the icing, such as the way it's much easier to force group ownership via Samba than via the filesystem (it's possible via the filesystem, but you either need to cludge it and alter everyone's umask, or go whole-hog and install and set up ACLs and then hope that all your clients can work with those too -- especially bothersome for NFS in group situations).  

With that in mind, can user mandi access anything in the shared directory directly, i.e. right there on the server, and not through Samba?

Very puzzling, I'll certainly grant you that.  :shock:

Eiríkr

---

### Post by ant2ne on 2008-04-11
```
ant2ne@2ne-buntu:/etc/samba$ pwd
/etc/samba
ant2ne@2ne-buntu:/etc/samba$ sudo mv smbpasswd smb.passwd.old
ant2ne@2ne-buntu:/etc/samba$ ls
dhcp.conf  gdbcommands  smb.conf  smb.conf~  smb.passwd.old
ant2ne@2ne-buntu:/etc/samba$ cat smbpasswd
cat: smbpasswd: No such file or directory
ant2ne@2ne-buntu:/etc/samba$ 
 
```Then restarted samba

```
ant2ne@2ne-buntu:/etc/samba$ ls
dhcp.conf  gdbcommands  smb.conf  smb.conf~  smbpasswd  smb.passwd.old

```


```
ant2ne@2ne-buntu:/etc/samba$ sudo smbpasswd -a mandi
New SMB password:
Retype new SMB password:
Added user mandi.
ant2ne@2ne-buntu:/etc/samba$ 

```restarted samba again (I thought it might matter)

Turrned on the XPVM (stupid windows activation pop up). Log on as a mandi. Still nothing. Why does samba hate mandi?

---

### Post by abuelitnt on 2008-04-12
> **ant2ne said:**
> Can you get ant2ne's?
it is blank

---

### Post by ant2ne on 2008-04-12
actually; no.  ant2ne can't do nothing, This is worse than before. I think that, until samba can do a checknames (underline) like windows can, samba is going to be second-rate.  advice?

---

### Post by ant2ne on 2008-04-12
On a whim, I changed my smb.conf to open up restrictions...```
[global]
workgroup = CYGNEHOME
server string = RAID1 File Server
preferred master = yes
local master = yes
;domain master = yes
os level = 33
encrypt passwords = yes

[Open]
path = /media/md3/shares/open
read only = no

[ant2ne]
path = /media/md3/shares/ant2ne
read only = no

[mandi]
path = /media/md3/shares/mandi
browseable = yes
read only = no

[Media]
path = /media/md3/shares/media
browseable = yes
read only = no

```

And that changed nothing. Nobody could access anything. I started thinking that this looks like a file permissions thing. The permissions on the shares were...
```
ant2ne@2ne-buntu:/media/md3/shares$ pwd
/media/md3/shares
ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 32
drwxrwxrwx  4 ant2ne sambausers 4096 2008-03-30 18:06 ant2ne
drwxrwxrwx  2 ant2ne sambausers 4096 2008-03-24 19:56 boys
drwxrwxrwx 10 mkc    sambausers 4096 2008-03-24 19:50 mandi
drwxrwxrwx  7 ant2ne sambausers 4096 2008-04-06 14:57 media
drwxrwxrwx 10 ant2ne sambausers 4096 2008-03-24 19:46 MSwin.stuff
drwxrwxrwx  4 ant2ne sambausers 4096 2008-04-06 19:27 open
drwxrwxrwx  2 ant2ne sambausers 4096 2008-03-24 19:56 temp
drwxrwxrwx 17 ant2ne sambausers 4096 2008-03-29 09:53 WinMy

```

Another whim took me...
```
ant2ne@2ne-buntu:/media/md3/shares$ cd ..
ant2ne@2ne-buntu:/media/md3$ ls -l
total 24
drwxr-xr-x  4 ant2ne root  4096 2008-04-06 16:45 data
drwx------  2 root   root 16384 2008-03-15 15:52 lost+found
drwxrwx--- 10 ant2ne root  4096 2008-03-29 17:19 shares
ant2ne@2ne-buntu:/media/md3$ sudo chmod -R 777 ./shares
```
(The directory "shares" holds the above samba shares.)

All of the sudden everyone can get in. The door was thrown open. WHY does samba require laxed permissions on the parent folder? What permissions should I put on the parent folder to let everyone in, But cause no harm.?

I'm going to use the FS permissions to control the shares, and let samba pretty much be open. Here are my current FS permissions. What do you think? Right now, only ant2ne mandi media and open are shares. I do eventually plan to implement the other folder shares also.

```
total 24
drwxr-xr-x  4 ant2ne root  4096 2008-04-06 16:45 data
drwx------  2 root   root 16384 2008-03-15 15:52 lost+found
drwxrwxr-x 10 ant2ne root  4096 2008-03-29 17:19 shares
ant2ne@2ne-buntu:/media/md3$ cd shares
ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 32
drwxr-x---  4 ant2ne sambausers 4096 2008-03-30 18:06 ant2ne
drwxrwxr-x  2 ant2ne sambausers 4096 2008-03-24 19:56 boys
drwxr-x--- 10 mandi  sambausers 4096 2008-04-12 21:08 mandi
drwxrwxr-x  7 ant2ne sambausers 4096 2008-04-12 21:08 media
drwxrwxr-x 10 ant2ne sambausers 4096 2008-03-24 19:46 MSwin.stuff
drwxrwxrwx  4 ant2ne sambausers 4096 2008-04-06 19:27 open
drwxrwxr-x  2 ant2ne sambausers 4096 2008-03-24 19:56 temp
drwxrwxr-x 17 ant2ne sambausers 4096 2008-03-29 09:53 WinMy
ant2ne@2ne-buntu:/media/md3/shares$ 
```

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

