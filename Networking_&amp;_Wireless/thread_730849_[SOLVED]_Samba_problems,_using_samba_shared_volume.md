---
title: "[SOLVED] Samba problems, using samba shared volumes from Windows"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by huahe on 2008-03-21
1. I can’t save from Photoshop CS3. I am getting this error: “Can not save file because a disk error have occurred”.

2. I even have problems creating folders from Windows Explorer. I get an error: “Can not rename folder”. But when I hit F5, I can see the folder with the right name.

3.  MAME32 is terribly slooooooow reading roms from the samba share.

This is my SMB.CONF :
```

[ global ]
interfaces = egiga0
unix charset = UTF8
workgroup = QUENDI
netbios name = CERBERUS
server string = Disco duro red RAID
hosts allow = 
hosts deny = 
security = SHARE
encrypt passwords = yes
max log size = 0
socket options = TCP_NODELAY SO_RCVBUF=65536 SO_SNDBUF=65536
max xmit = 65535
create mask = 0777
directory mask  = 0777
force create mode = 0777
force directory mode = 0777
```

---

### Post by Eiríkr on 2008-03-21
What versions of Ubuntu and Samba do you have installed?  My descriptions here apply to Gutsy 7.10 with Samba v3.026.  

If this is your whole smb.conf file, I am absolutely *flabbergasted* that you can do anything at all on your shares, precisely because **no shares are defined**.  

That said, let's look at what you have here in your [font=courier][global][/font] section, option by option.  I've linked each option name through to the relevant section of [the online man page](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html).

[font=courier]**[interfaces](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INTERFACES) = egiga0**[/font] -- 

> This option allows you to override the default network interfaces list that Samba will use for browsing, name registration and other NBT traffic. By default Samba will query the kernel for the list of all active interfaces and use any interfaces except 127.0.0.1 that are broadcast capable.

So this option is really **only** relevant if you have multiple network interfaces.  If you've only got loopback plus one other, there's no need to specify this.


[font=courier]**[unix charset](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#UNIXCHARSET) = UTF8**[/font] -- 

> Specifies the charset the unix machine Samba runs on uses. Samba needs to know this in order to be able to convert text to the charsets other SMB clients use.

This is also the charset Samba will use when specifying arguments to scripts that it invokes.

Default: *unix charset = UTF8*

Since your option here is already the default value, there's no need to specify it -- so best to leave it out and simplify your conf file.  


[font=courier][b][workgroup](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WORKGROUP) = QUENDI
[netbios name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NETBIOSNAME) = CERBERUS
[server string](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SERVERSTRING) = Disco duro red RAID[/b][/font] -- 

These options are pretty straightforward, and look fine.  


[font=courier][b][hosts allow](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HOSTSALLOW) = 
[hosts deny](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HOSTSDENY) = [/b][/font] -- 

Both of these options are **only** relevant in share definitions, and do not belong in the [font=courier][global][/font] section.  Furthermore, since both of these are not set to anything (the default), there's no need to include them at all anyway.  Delete these lines.  


[font=courier][b][security](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY) = SHARE
[encrypt passwords](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ENCRYPTPASSWORDS) = yes[/b][/font] -- 

Security is a big complicated issue, and I would still recommend you read the man page section even though your setting for this option looks okay.  Meanwhile, the default for [font=courier]encrypt passwords[/font] is already "yes", so again you can delete this line.  


[font=courier]**[max log size](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAXLOGSIZE) = 0**[/font] -- 

>  This option (an integer in kilobytes) specifies the max size the log file should grow to. Samba periodically checks the size and if it is exceeded it will rename the file, adding a .old extension.

A size of 0 means no limit. 

Looks fine.


[font=courier]**[socket options](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SOCKETOPTIONS) = TCP_NODELAY SO_RCVBUF=65536 SO_SNDBUF=65536**[/font] --

> You may find that on some systems Samba will say "Unknown socket option" when you supply an option. This means you either incorrectly typed it or you need to add an include file to includes.h for your OS. If the latter is the case please send the patch to  [email]samba-technical@samba.org[/email].

You can find these "unknown socket option" messages in [font=courier]/var/log/samba/log.smbd[/font].  Look for "unknown parameter".  I've just removed all unknowns on my end, and things work fine for me.  


[font=courier]**[max xmit](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAXXMIT) = 65535**[/font] -- 

> This option controls the maximum packet size that will be negotiated by Samba. The default is 16644, which matches the behavior of Windows 2000. A value below 2048 is likely to cause problems. **You should never need to change this parameter from its default value.**

It sounds like you need to remove this line to allow the default to kick back in again.


[font=courier][b][create mask](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK) = 0777
[directory mask](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK)  = 0777
[force create mode](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE) = 0777
[force directory mode](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEDIRECTORYMODE) = 0777[/b][/font] -- 

All of these are **only** relevant in share definitions, and do not belong in the [font=courier][global][/font] section.  Moreover, it sounds like the [font=courier]force create mode[/font] and [font=courier]force directory mode[/font] settings are redundant:

> This operation is done after the mode mask in the parameter create mask [or directory mask] is applied.

----------

I'm very curious how you wound up with such a mangled smb.conf file.  Was this the result of a GUI config tool, by chance?  If so, which one?  I've read numerous threads where the ultimate culprit in screwing up the conf file was a GUI config tool, such as gsambad or SWAT.  

Anyway, you need to fix the options in your [font=courier][global][/font] section, then [read this part of the man page about conf file sections](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#id2481212), and then add the needed lines to your conf file to define a file share.  

Good luck,

Eiríkr

---

### Post by huahe on 2008-03-24
Thanks a lot for your response!

Yes, you were right, I did not paste the complete  smb.conf file. I paste the complete file at the end of this post. By the way, I changed some values after I read your message.

Anyway, I must confess. The Samba server is not an Ubuntu machine. It is a NAS, a network disk with Linux on it, with Samba 2.2 It's a D-link 323, very popular. 

I still have the same problems with this disk. I installed a VirtualBox with Ubuntu and Samba3, and all went like a charm :( So, it seems that the problem is my disk or Samba 2.2

What do you think ?

Here you are the complete file:

```
[ global ]
interfaces = egiga0
unix charset = UTF8
workgroup = WORKGROUP
netbios name = NASDrive
server string = My NAS drive
hosts allow = 
hosts deny = 
security = SHARE
encrypt passwords = yes
max log size = 0
socket options = TCP_NODELAY SO_RCVBUF=16644 SO_SNDBUF=16644
#max xmit = 65535
create mask = 0777
directory mask  = 0777

[ All ]
comment = 
path = /mnt/HD_a2
valid users = 
read only = no
guest ok = yes
oplocks = yes
map archive = yes

```

---

### Post by Eiríkr on 2008-03-25
Hey there huahe --

I'm curious if access to your NAS is working any better?  

Let's look over your current smb.conf file.  Any options I don't comment on should be fine as-is.  

----------
**[ global ]**
This share definition name is problematic -- there should be *no* spaces between the name and the brackets.  So this share heading should look like this: [font=courier][global][/font]

**unix charset = UTF8**
Default value, you can delete this line to simplify the file.

[B]hosts allow =
hosts deny =[/B]
Empty, so delete to simplify.

**encrypt passwords = yes**
Default value, you can delete this line to simplify the file.

**[ All ]**
This share definition name is problematic -- there should be *no* spaces between the name and the brackets.  So this share heading should look like this: [font=courier][All][/font]

**comment = **
Empty, so delete to simplify.

**valid users =**
Empty, so delete to simplify.

**read only = no**
Same as "writable = yes".

**oplocks = yes**
Default value, you can delete this line to simplify the file.

**map archive = yes**
Default value, you can delete this line to simplify the file.

----------

So after slimming down your conf file and fixing a couple of things, it should look like this:
```
[global]
   interfaces = egiga0
   workgroup = WORKGROUP
   netbios name = NASDrive
   server string = My NAS drive
   security = SHARE
   max log size = 0
   socket options = TCP_NODELAY SO_RCVBUF=16644 SO_SNDBUF=16644
   #max xmit = 65535
   create mask = 0777
   directory mask  = 0777
   
[All]
   path = /mnt/HD_a2
   read only = no
   guest ok = yes
```

Try this one out and let me know if it works.

Cheers,

Eiríkr

---

### Post by huahe on 2008-03-25
Hello! 
Thanks thanks thanks!!!
I did all you told me, but everything is going the same.
I can't save from Photoshop to the NAS, and creating New folders gives me the weird error (Can not change folder name, can not find the specified file). This happens in two PCs connected to the network.

:(

---

### Post by Eiríkr on 2008-03-25
Sorry this is taking me so long to figure out; I have no direct experience with "share" level Samba security, preferring the default (and more secure) "user" level.  

Looking more closely at [the man page section regarding share-level security]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITYEQUALSSHARE") (for when [font=courier]security = share[/font]), I noted the following:
> When clients connect to a share level security server they need not log onto the server with a valid username and password before attempting to connect to a shared resource (although modern clients such as Windows 95/98 and Windows NT will send a logon request with a username but no password when talking to a [font=courier]security = share[/font] server). Instead, the clients send authentication information (passwords) on a per-share basis, at the time they attempt to connect to that share.

Note that smbd *ALWAYS* uses a valid UNIX user to act on behalf of the client, even in [font=courier]security = share[/font] level security.

I also note that your [font=courier][All][/font] share is defined as [font=courier]guest = ok[/font], about which [the man page says]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK"):

> If this parameter is yes for a service, then no password is required to connect to the service. Privileges will be those of the guest account.

Looking then at [the man page section for the [font=courier]guest account[/font] parameter]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT"), we find:
>     This is a username which will be used for access to services which are specified as guest ok (see below). Whatever privileges this user has will be available to any client connecting to the guest service. This user must exist in the password file, but does not require a valid login. The user account "ftp" is often a good choice for this parameter.

    On some systems the default guest account "nobody" may not be able to print. Use another account in this case. You should test this by trying to log in as your guest user (perhaps by using the [FONT="Courier New"]su -[/FONT] command) and trying to print using the system print command such as [FONT="Courier New"]lpr(1)[/FONT] or [FONT="Courier New"]lp(1)[/FONT].

    This parameter does not accept % macros, because many parts of the system require this value to be constant for correct operation.

    Default: *[FONT="Courier New"]guest account = nobody[/FONT] # default can be changed at compile-time*

    Example: *[FONT="Courier New"]guest account = ftp[/FONT]*

So, if you see no authentication prompt asking for username and password to log into your share, it must be giving you guest access, in which case you have the same permissions as the guest account user, which in this case is user "nobody".  This user is generally very restricted, and I somehow doubt that this user has the needed permissions on the [font=courier]/mnt/HD_a2[/font] directory used for your [font=courier][All][/font] share.  You can check the permissions on this directory by logging into your NAS directly and typing:
```
ls -ld /mnt/HD_a2
```

Let me know if this makes sense, and we'll go from there.

Cheers,

Eiríkr

---

### Post by huahe on 2008-03-26
Fixed! You gave me the clue ! I changed SHARE, and added an admin user. All problems gone.
Thanksss!!!!

---

### Post by Eiríkr on 2008-03-26
Excellent, huahe!  :D  Could you post your working smb.conf file for others to learn from?  

And if that does it for this thread, please also mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

### Post by huahe on 2008-03-26
This is my new smb.conf. MAME is still slow, but I think it's a MAME issue.

```
[global]
interfaces = egiga0
unix charset = UTF8
workgroup = WORKGROUP
netbios name = NASHD
server string = My NAS
security = USER
max log size = 512
socket options = TCP_NODELAY SO_RCVBUF=16644 SO_SNDBUF=16644
create mask = 0777
directory mask  = 0777

[All]
comment = All my stuff
path = /mnt/HD_a2
read only = no
writeable = yes
admin users = huahe
guest ok = no
```

---

