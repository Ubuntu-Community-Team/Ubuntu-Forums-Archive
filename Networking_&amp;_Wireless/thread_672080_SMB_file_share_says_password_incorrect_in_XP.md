---
title: "SMB file share says password incorrect in XP"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-01-19
Good day everyone!

I've got a problem here: I have to set up a samba file server that would have say two file shares that I could access without a password and one has to be password protected. My smb.conf file is: ```
[global]

   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
   interfaces = eth0
   bind interfaces only = true
   log file = /var/log/samba/log.%m
   max log size = 1000
;   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = user
   invalid users = root
   case sensitive = no
;   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
;   pam password change = no
   load printers = no
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin
;   include = /home/samba/etc/smb.conf.%m
   socket options = TCP_NODELAY

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[Music]
path = /home/user/Music
available = yes
browsable = yes
public = yes
writable = yes

[Public]
path = /home/user/Public
available = yes
browsable = yes
public = yes
writable = yes

[Restricted]
path = /home/user/restricted
available = yes
valid users = restricted_user
browsable = yes
public = yes
writable = yes
```Everything works fine when I connect to the Restricted share from another Ubuntu box (a login/password window appears, I type it, press Enter and I see the folder contents) but the XP box rejects my login/password combination though everything's fine with it.

sudo smbpasswd -a restricted_user is done, chmod permissions for the restricted folder are okay. Error messages do not appear in the /var/log/samba/log.xpbox_name

Something's wrong with the XP password authentication? Help me please! Thank you!

---

### Post by curVV on 2008-03-27
same problem... will post if i figure it out somehow but i been struggling with this since 2 days ago.

---

### Post by curVV on 2008-03-27
ok, so it works now but not entirely sure why ;/ anyway what  i did was replaced the smb.conf with a simple one :

```
[global]
        workgroup = FSN
        server string = %h server (CYBERCIDE SHARE)
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        log file = /var/log/samba/log.%m
        max log size = 1000
        panic action = /usr/share/samba/panic-action %d
        comment = CYBERCIDE FILES

[filez]
        path = /smbshares
        valid users = cybercide, gordon, curvv
        write list = cybercide
        read only = No
        guest ok = Yes
```

The /smbshares directory has permissions set so only the owner(cybercide) can delete files and others can't write
(1775)

the valid users in the smb.conf file above are all users on the server sharing the files.

converted each of them to samba users using webmin and set their samba passwords(different to their actual passwords)

now only people logging in with cybercide user and password can write or upload files and people using the gordon account can only read.

works from windoze XP...

probably needs some more tweaking but at the moment it's working fine and i'm not gonna try fix what aint broke :)

---

### Post by Eiríkr on 2008-03-27
@PryGuy --

Here's your smb.conf file again, annotated and with commented-out lines removed.

```
[global]
## Name resolution options ##
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   wins support = no
   dns proxy = no
## Network security options ##
   interfaces = eth0
   bind interfaces only = true
## Logging options ##
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
## User security options ##
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = user
   invalid users = root
   case sensitive = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
## Miscellaneous options ##
   load printers = no
   socket options = TCP_NODELAY

; Since you commented out all the printing options above in [global], 
; you probably aren't sharing a printer, so why not delete this section?
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# ========== Share definitions ========== #
[Music]
   path = /home/user/Music
   available = yes  # Default value, so delete to simplify
   browsable = yes  # Default value, so delete to simplify
   public = yes
   writable = yes

[Public]
   path = /home/user/Public
   available = yes  # Default value, so delete to simplify
   browsable = yes  # Default value, so delete to simplify
   public = yes
   writable = yes

[Restricted]
   path = /home/user/restricted
   available = yes  # Default value, so delete to simplify
   browsable = yes  # Default value, so delete to simplify
   valid users = restricted_user
   public = yes     # <-- Here's your trouble.
   writable = yes

```

Scroll down to your [font=courier][Restricted][/font] share definition.  The problem is that you've got conflicting options here; you specify [font=courier]valid users[/font] on the one hand, but then on the other, you also open access up to anybody with [font=courier]public = yes[/font].  [font=courier]public = yes[/font] is the same thing as [font=courier]guest ok = yes[/font].  Guest access means that access uses the guest account, which you define in your [font=courier][global][/font] section as the "user" account.  I suspect that XP is getting confused by this inconsistency.  I'd recommend you try removing (or commenting out) this [font=courier]public = yes[/font] line for your [font=courier][Restricted][/font] share, and see if that works any better.  

----------

@curVV --

The filesystem permissions on your share don't look quite right:
> The /smbshares directory has permissions set so only the owner(cybercide) can delete files and others can't write
(1775)

Have a look at [the Wikipedia article section on filesystem permissions](http://en.wikipedia.org/wiki/File_system_permissions#Additional_Permissions), and also the ["Octal notation" subsection](http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation).  The last three digits here, "775", denote that the owner *and all group members* have all permissions, while other users can only read and execute (execute for directories means to open them).  If you want to exclude group members from write permissions, you have to change that second "7" to a "5".  

If you scroll down to [the "Octal notation and additional permissions" section](http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation_and_additional_permissions), you'll see that the leading "1" refers to the [font=courier]setuid[/font] bit.  On files or executables, this means the file will open or run with the owner's permissions, which can be risky.  On directories, however, this bit means that any files created in the directory will inherit the directory's owner.  This can be very useful for sharing purposes (more commonly for sharing among group members using the [font=courier]setgid[/font] bit, which would be a leading "2" in octal), but make sure it's what you intend.

I described how to configure filesystem permissions for Samba sharing for either a single-user or multi-user setup in [post=4496702]this post[/post], which might be a useful reference for folks reading this thread.  


> the valid users in the smb.conf file above are all users on the server sharing the files.

Listing the individual usernames works fine.  You can also specify groups here, by prepending an **_@_** onto the group name, such as [font=courier]valid users = @smbusers[/font] for example.  


> converted each of them to samba users using webmin and set their samba passwords (different to their actual passwords)

Sounds good.  On the command line, you'd run:
```
sudo smbpasswd -a USERNAME
```
... for each USERNAME you want to use with Samba.

> now only people logging in with cybercide user and password can write or upload files and people using the gordon account can only read.

For one, it looks like user "curvv" would also be able to read.  

For another, the [font=courier]write list[/font] option is not exclusive, but rather inclusive.  By this, I mean that it does not define *only* those users who can write to the share, but *also* those users who can write to the share, *in addition to* whatever is defined by the [font=courier]read only[/font] or [font=courier]writable[/font] options (which are antonyms; you only need one or the other, but if you have both for some reason, they can't both have the same value).  

Looking at [the man page section on the [font=courier]write list[/font] option](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITELIST):
> This is a list of users that are given read-write access to a service. If the connecting user is in this list then they will be given write access, no matter what the read only option is set to. 

So this [font=courier]write list[/font] option is *only* exclusive if the [font=courier]read only[/font] option is set to "yes".  I just tested this on my own setup, and if [font=courier]read only[/font] is "no" or [font=courier]writable[/font] is "yes", then any user who can access the share **and who also has write permissions on the filesystem** will be able to write.  

Ultimately, it's best to control read-write access at the filesystem permissions level ;) -- which it looks like you're doing.  :)


One thing for thread readers to note is that Windows is very aggressive about caching share authentication info.  So once you log into a Samba share with one username and password, that's what Windows will use for successive connections.  If the Samba username or password ever change, Windows will keep trying with the old ones, and just fail out instead of asking the user for the new ones.  This same caching makes it pretty hard to change which Samba login you want to use.  KennedyM wrote a HOWTO for getting rid of Windows authentication caches in [post=4491515]this post[/post], in case anyone needs it.  

Cheers,

Eiríkr

---

### Post by curVV on 2008-03-28
Thanks for that, Eiríkr! Makes everything much less clouded. Reading up on those links you posted...

---

### Post by Eiríkr on 2008-03-28
Glad my ramblings seem to be useful.  ;)  Post again if I've left anything unclear.  

Cheers,

Eiríkr

---

