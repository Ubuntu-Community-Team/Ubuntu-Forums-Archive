---
title: "OS X to Samba and Other Questions"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by jtdgrz on 2008-04-10
This is a unique problem as far as I can tell, I've done some Googling and searching these forums and can't seem to find anyone with quite the same problem.

I've been toying around with Samba tonight because my family wants to move our ~3 XP servers to Linux, and we want to preserve all our shares.

I've been looking through multiple samba configurations and such, and trying to make one that matches our current setup.  Here is what I have so far (with most of the junk omitted):

```

[global]d
    ; General server settings
    netbios name = io
    server string =
    workgroup = dgrz
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes


[johnie004$]
    path = /home/samba/johnie004
    read only=no
    writable=yes
    browsable=no
    valid users="jtdgrz"

[mikey003$]
    path=/home/samba/mikey003
    read only=no
    writable=yes
    browsable=no
    valid users="mike"

[userarea$]
    path=/home/samba
    read only=no
    writable=yes
    browsable=no
    valid users="administrator"

```

This is a conf I copied from here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now my problem is, in our current setup our folders are not browsable; connecting to our server does not give a list of the shares.   I duplicated this in the above configuration, and it works fine when connecting from windows to these shares.

However, when the browsable flag is set to no, I can not connect to the share from OS X.  When browsable is enabled, the shares are easily accessible.

(using, for example):
```
smb://server/userarea$
```

Is there something that I messed up?  My configuration file is probably a mess, I've been toying around with it a lot just trying to duplicate our current functionality.

Another thing that I've seen answered many times, but none easily, is connecting to multiple shares from a windows computer. 

When you try to connect to more than one share with a different user name, you get the following error:
```

---------------------------
Windows
---------------------------
The network folder specified is currently mapped using a different user name and password.

To connect using a different user name and password, first disconnect any existing mappings to this network share.
---------------------------
OK   
---------------------------

```

and then..
```

---------------------------
Windows
---------------------------
The mapped network drive could not be created because the following error has occurred:



Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again..


---------------------------
OK   
---------------------------

```

If at all possible, I'm looking for any type of fix for the first problem, and an easy fix to the second.  I don't want to spend hours setting up a user map, is there any other way?

---

### Post by jtdgrz on 2008-04-10
I've answered my own question, a little.

Then $ flag at the end of a share seems to make it not browsable, so adding the browsable flag was redundant.  Dropping the browsable =no flag leaves the shares not browsable, and I am able to connect to them from OS X now.

However, still in windows and OS X I cannot connect to multiple shares.

In OS X, I am greeted with:

```

A volume failed to mount.

The volume "userarea$" could not be mounted.

```

This is with one share already connected.  I can connect to any share easily, one at a time, but not two at a time.

Windows still has the same error as above.

---

### Post by Eiríkr on 2008-04-10
Looking over your conf file, I noted the following:

There's a stray "d" on the [global] line that should be removed.

**[server string](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SERVERSTRING) =**
Since this is blank, may as well leave it out for simplicity's sake (simple is good! :)), and allow the server to use the default value of "Samba %v", where %v is the package version.

**[announce version](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ANNOUNCEVERSION) = 5.0**
This setting is very likely completely unnecessary.  Beyond that, this value of "5.0" appears to be bogus.  From the man page:
> This specifies the major and minor version numbers that nmbd will use when announcing itself as a server. The default is 4.9. **Do not change this parameter unless you have a specific need to set a Samba server to be a downlevel server.**

Default: *[font=courier]announce version = 4.9[/font]*

**[null passwords](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NULLPASSWORDS) = true**
This strikes me as a bad idea, security-wise.  This option is only relevant if you have Samba accounts for which no password has been defined, and has nothing to do with guest access.  I would *strongly* recommend removing this option unless there is a real compelling reason to configure and then use Samba accounts with no passwords.  

**[username map](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP) = /etc/samba/smbusers**
This is only needed if you're actually mapping remote client usernames to local server usernames.  Have a look at [post=4496702]this post[/post], particularly the "In the [global] section" portion, for a description of how username mapping works.  

[b][printing](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING) = CUPS
[printcap name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME) = CUPS[/b]
Have a look at the relevant man page sections by clicking through the links in the option names.  Both of these are *only* relevant within printer share definitions, and do *not* belong in the [global] section.  Delete these lines.  


[b][syslog](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOG) = 1
[syslog only](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOGONLY) = yes[/b]
The first one is already the default value, and may thus be removed for simplicity.  The second one shunts all Samba server messages into the /var/log/syslog file, rather than using the separate /var/log/samba/log.smbd and /var/log/samba/log.nmbd files.  If that's what you want, great.

[b][read only](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#READONLY)=no
[writable](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITABLE)=yes[/b]
These two options are antonyms of each other; you only need one or the other.  It's probably okay to have both, provided they don't contradict each other, but it increases the complexity of your conf file and needlessly increases the possibility of an error.  


I'm curious as to why you have only one valid user specified for each share, since you apparently also want to be able to access multiple shares.  This makes me think there might be a better way of setting up your shares and permissions, but I don't fully understand what it is you're trying to do.  Could you explain a little bit about why you've done this?  

Cheers,

Eiríkr

---

### Post by jtdgrz on 2008-04-10
Thank you for telling me what to remove to clear things up.  Like I said, I copied that configuration from the other tutorial and didn't really know what I was doing.

The  setup we currently have is as follows, for one of the servers:
folders:
```

-uberarea
-userarea
  -john
  -mike
  -tony
  -kathy
  -names

```

The userarea folder holds all the subsequent folders, and can be accessed by connecting to our server using smb://jupiter/userarea$.

When you connect to the main directory, with the administrator account, he can see and edit any of the other users folders.  administrator may also edit uberarea, and is the only account that may.

All of the subsequent folders are only accessible by their respective username, mostly.  i.e. only john can access the john (smb://jupiter/john$) share, and only mike can access the mike share... except administrator may access both of these from userarea, and it seems on the windows computer it is currently configured on, administrator may access any folder under userarea with the administrator login.

What I need is the same setup, duplicated in ubuntu.  A main folder, which holds all the user folders.  The main folder is accessible by 'administrator' and the user folders are only accessible by that user.

With the current conf, that works, except I can not connect to two shares at the same time, with different user names.

edit:

Here is my new conf, following your advice and also removing items deemed useless by testparm /etc/samba/smb.conf

```

[global]
    workgroup = dgrz
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    name resolve order = hosts wins bcast
    syslog only = yes

[johnie004$]
    path = /home/samba/johnie004
    read only=no
    valid users="jtdgrz"

[mikey003$]
    path=/home/samba/mikey003
    read only=no
    valid users="mike"

[userarea$]
    path=/home/samba
    read only=no
    valid users="administrator"

```

---

### Post by Eiríkr on 2008-04-10
So as I understand it, the only user that needs to access multiple shares at once is "administrator", yes?  And if so, can "administrator" access the [userarea$] share and then just directly access the subdirectories from there?

Cheers,

Eiríkr

---

### Post by jtdgrz on 2008-04-10
Yes, administrator may access any share.  And can currently do so by going through the directory after mapping the share.

However, if I try to connect multiple shares at the same time, i.e. connect to john and mike at the same time, the errors in the first post occur.  I assume that adding administrator to the other shares as a valid user would allow this to not happen with administrator, but accessing john as jtdgrz and mike as mike at the same time currently does not work.

---

### Post by Eiríkr on 2008-04-10
I'm curious as to why you'd even want to.  :confused:  :)  It sounds like I still don't have a handle on what you're shooting for -- if you lock the shares down to only one user, then presumably you only want that one user to access it.  In this case, why would you want / need to access multiple shares as those users, instead of as the administrator?  The administrator is ostensibly just that, for administration?

One option is to set up groups rather than individual users.  Thereby, if John and Mike need to access each other's files, you would create a group, add them to it, make that group the primary for both of their shares, change the permissions mode to ensure that group members have access, and then edit the smb.conf file to force that group for new files and directories (to ensure that group members can still access them; otherwise the group defaults to the owner's personal group).  Whew!  Like so:
```
sudo addgroup jandm
sudo usermod -aG jandm jtdgrz
sudo usermod -aG jandm mike
sudo chgrp -R jandm /home/samba/johnie004
sudo chgrp -R jandm /home/samba/mikey003
sudo chmod -R 770 /home/samba/johnie004
sudo chmod -R 770 /home/samba/mikey003
```
Add / edit these lines to the share definitions for [johnie004$] and [mikey003$]:
```
force group = jandm
valid users = @jandm
```
The **_@_** prefix denotes a group.  

With this setup, John and Mike can each access the other's shares while logging in as themselves, thereby avoiding that particular Windows error.  I use a similar group setup for my Samba media share, which I have mounted on Windows (as a network drive) alongside my private documents share.  

HTH,

Eiríkr

---

### Post by jtdgrz on 2008-04-10
While thinking through this in my head, I can understand how it can seem unreasonable to have two shares that are explicitly different be accessed by the same windows user at the same time.  As a matter of fact, I'm trying to figure out why exactly I encountered this problem in the first place and what led me to try to think of a solution.  I'm pretty sure Mike was trying to access administrator and the mike share at the same time, and that was probably the problem.

Thanks for allowing me to think this through clearly.

If I add administrator to all the other shares, will this allow the userarea share to be accessed at the same time as the johnie004 share?

---

### Post by Eiríkr on 2008-04-10
Provided you mean by user "administrator", then yes.  :)

---

