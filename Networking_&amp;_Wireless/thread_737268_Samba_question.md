---
title: "Samba question"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by eludlow on 2008-03-27
Playing around with samba and windows file sharing, and I'm wondering if the following is possible...

Windows user connects to pc (\\pcname) and is presented with
[LIST=1]
[*]printer connected to linux machine
[*]each user on linux machine's home area, which needs that user's password (obviously!) to access
[*]an "anonymous" share where anyone can put files without the need for a password
[/LIST]

If this asking too much of Samba?

Many thanks,
Ed Ludlow

---

### Post by Eiríkr on 2008-03-27
Does this look at all like what you want?  If so, then yes.  :)

Cheers,

Eiríkr

---

### Post by eludlow on 2008-03-27
> **Eiríkr said:**
> Does this look at all like what you want?  If so, then yes.  :)

Cheers,

Eiríkr

Yes - exactly that :)

Please share the secret ;)

E

---

### Post by Eiríkr on 2008-03-27
I don't actually share any printers via Samba, so you'll want to look at [the man page section about that]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTERSSECT"), but for the rest, here's a sample of my smb.conf file.

```
[global]

## Name resolution options ##
   workgroup = HOMELAN
   server string = %h server
   wins support = yes

## Network security options ##
   interfaces = lo eth0
   bind interfaces only = true

## Logging options ##
   panic action = /usr/share/samba/panic-action %d
   syslog = 0
   debug level = 0
   log file = /var/log/samba/log.%m
   max log size = 1000

## User security options ##
;   security = user # Default value
   username map = /etc/samba/user.map
   invalid users = root
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

## Miscellaneous options ##
   socket options = TCP_NODELAY
   unix extensions = yes

## Master browser settings ##
   preferred master = yes
   domain master = yes
   local master = yes

#======================= Share Definitions =======================

[UserA's Documents]
        path = /data/usera_docs
        valid users = usera
        writable = yes

[UserB's Documents]
        path = /data/userb_docs
        valid users = userb
        writable = yes

[shared]
        path = /data/shared
        valid users = @users
        writable = yes
        comment = Shared directory with forced group.

[Music]
        path = /data/shared/Music
        valid users = @users
        writable = yes
```

Hope this helps,

Eiríkr

---

### Post by eludlow on 2008-03-27
That's marvellous, thank you.

One question...
Where you have "valid user=xxx" is xxx a samba user of a linux user?

E

---

### Post by Eiríkr on 2008-03-27
They must be one and the same.  As [the man page for [font=courier]smbpasswd[/font]]("http://linux.die.net/man/5/smbpasswd") describes:
> name

    This is the user name. It must be a name that already exists in the standard UNIX passwd file.

As a consequence, **all** Samba usernames are *also* Ubuntu usernames.  Note that you can map usernames, however, so the username you log in with from a remote host does not have to be one of these Samba / Ubuntu usernames.  The mapping file will define which local Samba / Ubuntu username the remote username equates to.  

Even if you're mapping usernames, you never use the mapped remote machine usernames in the conf file settings -- you must use the corresponding local Ubuntu usernames that the remote usernames are mapped to.  

Cheers,

Eiríkr

---

### Post by eludlow on 2008-03-27
Brilliant, thanks.  Will have a play in a bit and report back.

Appreciate your help, thanks.

Ed

---

### Post by Eiríkr on 2008-03-27
You're most welcome.  Have fun, and good luck.  :)

Eiríkr

---

### Post by eludlow on 2008-03-27
Getting there...:)

What's the significance of the "@users" in your config?

It's still prompting me for a login when I try and get into my "shared area" which requires the user "@users" - is there a way to let any one have read / write without needing to log in?

Ed

---

### Post by Eiríkr on 2008-03-27
The **_@_** prefix denotes a group name.  This is really only useful for multi-user setups when you want to define different groups with different permissions.  Have a look at [post=4496702]this post[/post] if you're at all interested in that side of things; scroll down to the "Multi-user" section.  I'd also recommend having a look at the smb.conf man page ([here online]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), or type [font=courier]man smb.conf[/font] in a terminal) to familiarize yourself with the various options.  

For no-authentication access, you'll want to set up guest access.  There are two parts to this -- one is defining the [font=courier]guest account[/font] option in your [font=courier][global][/font] options section, and the other is adding the [font=courier]guest ok = yes[/font] line to the share definition(s).  ([font=courier]public = yes[/font] is a synonym for this; you only need one or the other.)  If you forget to set the [font=courier]guest account[/font] option, guest logins will use the default guest account, which is user "nobody".  This user is generally very limited, and will very likely have no filesystem permissions to your shared directories (unless you've specifically added such permissions at some point).  Forgetting this setting is a common cause of Samba access problems.  

Note that opening up guest access can leave you vulnerable, and is really only best used when you don't know ahead of time who is going to access your shares.  Nautilus has an option to remember share authentication data so you only ever need to enter it once.  Windows has the same capability, but does it by default (and will just error out if the Samba login or password ever change on the server side; see [post=4491515]this post[/post] for instructions on how to fix this on the Windows side).  Mac also allows you to "remember" share authentication data.  

If you're worried about handing out your Ubuntu login and password to others just so they can access a Samba share, remember that Samba passwords do *not* need to match the Ubuntu passwords.  Also, with username mapping, it's easy enough to give others a remote login username that has nothing to do with the actual local Ubuntu username that the share will be accessed as.  

In general, it's best to have separate Ubuntu usernames for everyone accessing Samba (unless perhaps you're talking about a huge client base such as for a university or company), as then you can tell by looking at the logs who accessed what when.  If multiple remote users are mapped to a single local user, you'll only be able to tell that some member of that mapping group did something, but you won't be able to tell *which* member of the group.  

HTH,

Eiríkr

---

