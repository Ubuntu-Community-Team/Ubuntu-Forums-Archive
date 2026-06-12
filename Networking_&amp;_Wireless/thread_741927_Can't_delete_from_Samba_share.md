---
title: "Can't delete from Samba share"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Bluecube on 2008-04-01
I've got a shared HDD setup on a Thecus 2100 NAS system with folders shared out using Samba. I can create files on the shares without any issues but I'm unable to delete anything. When I try I get an error. On clicking further information it says that there's an "Invalid Argument". Does anyone have any idea why this is happening?

I'm using the latest Hardy Heron beta but had this issue previously with Gutsy.

I'm totally stumped here. Can anyone help out?

---

### Post by Eiríkr on 2008-04-01
This sounds like it might be a filesystems permission problem.  To help figure out what's going on, if you can log into your NAS via ssh or some such, post the contents of your smb.conf file ([font=courier]/etc/samba/smb.conf[/font]), and the results of the following (from within the NAS login):
```
ls -ld /problem/share/path
ls -l /problem/share/path
```

Cheers,

Eiríkr

---

### Post by Bluecube on 2008-04-01
Here we go...

[global]
server string = %h
deadtime = 15
hide unreadable=yes
load printers = no
log file = /opt/samba/var/log/samba.%m
log level = 0
max log size = 50
encrypt passwords = yes
case sensitive = auto
passdb backend = tdbsam
socket options = TCP_NODELAY
use sendfile = yes
local master = yes
domain master = no
preferred master =no
dns proxy = no
dos charset=utf8
unix charset=utf8
display charset=utf8
allow trusted domains = No
idmap uid = 20000-40000
idmap gid = 20000-40000
winbind separator = +
winbind nested groups = yes
winbind enum users = yes
winbind enum groups = yes
create mask = 0644
winbind use default domain = yes
map acl inherit = yes
nt acl support = yes
#map system = yes
bind interfaces only = yes
interfaces = eth*,wlan*,lo
guest account = nobody
map to guest = Bad User
guest only = yes
workgroup = FIRE
security = user
auth methods = guest sam_ignoredomain
password server = .
realm = 
idmap backend = idmap_rid:Fire=20000-40000
wins server = 

[Craig]
comment = Craigs Stuff
browseable = yes
guest only = no
path = /raid/Craig
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = yes
#recursive = yes

Output from ls -ld
drwxrwx---    2 admin    admingro     4096 Mar 31 17:17 /raid/Craig/

No output from ls -l command.

---

### Post by Eiríkr on 2008-04-01
I'll have to go over the conf file later, but if [font=courier]ls -l /raid/Craig[/font] produces zero output, it means that this directory is empty.  

Cheers,

Eiríkr

---

### Post by Bluecube on 2008-04-01
Yes the directory is empty. I can't access it to put anything into it!

---

### Post by Eiríkr on 2008-04-01
Oh, your first post said you could put things in, but couldn't delete them...?

Anyway, you've got [guest only = yes](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY) in your [global] options, but it is only used at the share definition level -- delete this line.  

Looking at your shared directory owner, group, and permissions, I'm led to ask what username you're trying to access this share with?

Cheers,

Eiríkr

---

### Post by Bluecube on 2008-04-02
My apologies. I've been having two separate issues with the NAS and I got them mixed up. The one I'm describing here is as described in my first post. The shares are accessible by anyone so no username is required to access them. 

My second issue (possibly related, possibly not) is that I can't access shares that are only accesible by certain users in this case user Craig.

---

### Post by Eiríkr on 2008-04-02
Your first issue seems to regard a share definition that you haven't posted, since the smb.conf file shown above only defines the [Craig] share.  Is this smb.conf file above your *whole* smb.conf file?  If so, there's no share anywhere that's accessible to anyone... :confused:

That aside, let's have a closer look at the smb.conf file options from your earlier post.  I've only commented on the noteworthy ones.  Click the links in the option names to browse to the relevant man page sections.

----------
**[global]**

**[deadtime]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DEADTIME") = 15**

Generally not needed; sets up auto-disconnection after so many minutes of inactivity.

**[hide unreadable]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HIDEUNREADABLE")=yes**

Share definition option.  Does *not* belong in the [global] section.  Delete this line.

**[load printers]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOADPRINTERS") = no**

Only relevant if you're sharing a printer via Samba.  Delete this line if you're not doing this.

**[case sensitive]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CASESENSITIVE") = auto**

Share definition option.  Does *not* belong in the [global] section.  Delete this line.

**[use sendfile]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USESENDFILE") = yes**

Share definition option.  Does *not* belong in the [global] section.  Delete this line.

**[dos charset]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DOSCHARSET")=utf8**

I don't think DOS supports UTF-8 character encoding...?  Probably irrelevant anyway, as I doubt you have any DOS clients.  Probably best to delete this line.

**[unix charset]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#UNIXCHARSET")=utf8**

Already the default value, and therefore redundant.  Delete to simplify your smb.conf file.  

**[display charset]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DISPLAYCHARSET")=utf8**

Probably best to delete this line and let the server use it's default.  From the man page section:
> Specifies the charset that samba will use to print messages to stdout and stderr. The default value is "LOCALE", which means automatically set, depending on the current locale. The value should generally be the same as the value of the parameter unix charset.

**[allow trusted domains]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ALLOWTRUSTEDDOMAINS") = No**

From the man page:
> This option only takes effect when the security option is set to [font=courier]server[/font], [font=courier]domain[/font] or [font=courier]ads[/font]. 

You have [font=courier]security = user[/font], rendering this option Irrelevant.  Remove this line.

[B][idmap uid]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#IDMAPUID") = 20000-40000
[idmap gid]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#IDMAPGID") = 20000-40000[/B]

Only relevant if you have NT clients and are doing complicated domain controller things.  Delete these lines if you're not doing this.

**[winbind separator]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDSEPARATOR") = +**

Very likely irrelevant, and possibly troublesome.  Delete this line.  From the man page:
> This parameter allows an admin to define the character used when listing a username of the form of DOMAIN \user. This parameter is only applicable when using the pam_winbind.so  and nss_winbind.so modules for UNIX services.

Please note that setting this parameter to + causes problems with group membership at least on glibc systems, as the character + is used as a special character for NIS in /etc/group.

[B][winbind nested groups]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDNESTEDGROUPS") = yes
[winbind enum users]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDENUMUSERS") = yes
[winbind enum groups]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDENUMGROUPS") = yes
[winbind use default domain]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDUSEDEFAULTDOMAIN") = yes[/B]

None of these options are relevant unless you're doing complex domain controller stuff.  Delete these lines if you're not.

create mask = 0644

[B][map acl inherit]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPACLINHERIT") = yes
[nt acl support]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NTACLSUPPORT") = yes
#[map system]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPSYSTEM") = yes[/B]

These are all share definition options.  They do *not* belong in the [global] section.  The last one is also only relevant if you have DOS clients.  Delete these lines.  

guest account = nobody
map to guest = Bad User

**[guest only]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY") = yes**

Share definition option.  Does *not* belong in the [global] section.  Delete this line.

**[auth methods]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#AUTHMETHODS") = guest sam_ignoredomain**

Unneeded except for testing by developers.  Delete this line.  From the man page:
> This option allows the administrator to chose what authentication methods smbd will use when authenticating a user. This option defaults to sensible values based on security. This should be considered a developer option and used only in rare circumstances. In the majority (if not all) of production servers, the default setting should be adequate.


**[password server]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PASSWORDSERVER") = .**

Only useful for fancy domain controller setups using Active Directory.  Moreover, the option value should be a hostname or network path, not just a dot.  Delete this line.

**[realm]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#REALM") =**

Only useful for fancy domain controller setups using a kerberos server.  Delete this line.

**[idmap backend]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#IDMAPBACKEND") = idmap_rid:Fire=20000-40000**

Again, very fancy stuff for authenticating *lots* of users in a domain controller setup.  Very unlikely that this is needed.  If you don't know what this is, you're best off commenting out this line (add a **_#_** at the beginning), and if your NAS complains, the manufacturers are doing some *wacky* crap, and you'll probably need to uncomment the line.  If no complaint, good -- they're not as insane as I'm beginning to worry.  ;)

**[wins server]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINSSERVER") =**

Only useful for multi-subnet networks.  Empty anyway in your conf file, so delete.  


**[Craig]**

[B][browseable]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BROWSEABLE") = yes
[guest only]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY") = no[/b]

Already the default values, and therefore redundant.  Delete to simplify your smb.conf file.  

[B][map acl inherit]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPACLINHERIT") = yes
[inherit acls]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INHERITACLS") = yes[/B]

Very likely unneeded, but not harmful here, and might be relevant if your NAS manufacturer has made things much fancier than usually required.   

**[inherit permissions]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INHERITPERMISSIONS") = Yes**

Again, likely irrelevant, but not harmful here.  From the man page section (emphasis mine):
> The permissions on new files and directories are normally governed by create mask, directory mask, force create mode and force directory mode but the boolean inherit permissions parameter overrides this.

New directories inherit the mode of the parent directory, including bits such as setgid.

New files inherit their read/write bits from the parent directory. Their execute bits continue to be determined by map archive, map hidden and map system as usual.

Note that the setuid bit is never set via inheritance (the code explicitly prohibits this).

This can be particularly useful on **large systems with many users, perhaps several thousand**, to allow a single [homes] share to be used flexibly by each user.

Default: [font=courier]inherit permissions = no[/font]

**[map archive]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPARCHIVE") = yes**

Already the default value, and therefore redundant.  Delete to simplify your smb.conf file. 

**[map hidden]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPHIDDEN") = yes**

Again, likely irrelevant, unless your NAS manufacturer went overboard.  From the man page:
> This controls whether DOS style hidden files should be mapped to the UNIX world execute bit.

Note that this requires the create mask to be set such that the world execute bit is not masked out (i.e. it must include 001). See the parameter create mask for details.

*No default*

I'm not really sure what this means, and this is the first I've heard of a "world executable bit".  :confused:

**#recursive = yes**

This last does not appear to be a valid Samba option, and as such should probably be deleted altogether.
----------

Given the amount of extraneous stuff in here, I have to ask if you've used a GUI config tool at any point?  I've so far never seen a GUI config tool that produces a sane, fully functional, and fully valid smb.conf file -- they all include rubbish that doesn't belong, and / or just overly complicates things.  If you haven't used any such tool, the fault lies with your NAS manufacturer.  Pray tell, what are the make and model of your NAS?

And if there happens to be another share definition for access by anyone that you didn't include in your previous post, please post that as well.

Hope this helps get your Samba config sorted,

Eiríkr

---

### Post by Bluecube on 2008-04-02
Here's my entire conf file. I shortened it to try and limit any confusion. I've got a Thecus n2100 NAS and the only way to configure Samba is through a very limited web interface. Indeed I had to try and find a way to access the smb.conf file by SSH in order to get all the info you required.

I'm just off to fully read your very comprehensive reply and hopefully sort things out. Thanks very much!

[global]
server string = %h
deadtime = 15
hide unreadable=yes
load printers = no
log file = /opt/samba/var/log/samba.%m
log level = 0
max log size = 50
encrypt passwords = yes
case sensitive = auto
passdb backend = tdbsam
socket options = TCP_NODELAY
use sendfile = yes
local master = yes
domain master = no
preferred master =no
dns proxy = no
dos charset=utf8
unix charset=utf8
display charset=utf8
allow trusted domains = No
idmap uid = 20000-40000
idmap gid = 20000-40000
winbind separator = +
winbind nested groups = yes
winbind enum users = yes
winbind enum groups = yes
create mask = 0644
winbind use default domain = yes
map acl inherit = yes
nt acl support = yes
#map system = yes
bind interfaces only = yes
interfaces = eth*,wlan*,lo
guest account = nobody
map to guest = Bad User
#guest only = yes
workgroup = FIRE
security = user
auth methods = guest sam_ignoredomain
password server = .
realm = 
idmap backend = idmap_rid:Fire=20000-40000
wins server = 

[album]
comment = 
browseable = no
guest only = no
path = /raid/album
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0644
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = yes

#recursive = yes
[iTunes]
comment = 
browseable = no
guest only = yes
path = /raid/iTunes
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0644
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no

[usbcopy]
comment =
browseable = yes
guest only = yes
path = /raid/usbcopy
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0644
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no

[usbhdd]
comment =
browseable = yes
guest only = yes
path = /raid/usbhdd
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0644
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no

[Craig]
comment = Craigs Stuff
browseable = yes
guest only = no
path = /raid/Craig
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = yes
#recursive = yes

[General]
comment = General
browseable = yes
guest only = yes
path = /raid/General
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no
#recursive = yes

[Music]
comment = Music
browseable = yes
guest only = yes
path = /raid/Music
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no
#recursive = yes

[Video]
comment = Video
browseable = yes
guest only = yes
path = /raid/Video
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no
#recursive = yes

[Pictures]
comment = Pictures
browseable = yes
guest only = yes
path = /raid/Pictures
map acl inherit = yes
inherit acls = yes
read only = no
create mask = 0777
force create mode = 0000
inherit permissions = Yes
map archive = yes
map hidden = no
#recursive = yes

---

### Post by Eiríkr on 2008-04-02
If you can get in via ssh, then I'd suggest you (first back up your smb.conf file, just in case, then) edit it by hand.  :)  If things go boing you can always restore the backed up copy.  I usually just do something like this before mucking about:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.BAK
```

----------
I've already gone over the [global] and [Craig] options, so here I'll just look at the other share definitions.  

All the shares seem to include the following options related to ACLs (**_a_**ccess **_c_**ontrol **_l_**ists, a more finely-grained means of setting up permissions than the basic Unix owner / group / others permissions settable via [font=courier]chmod[/font].  More at Wikipedia [here]("http://en.wikipedia.org/wiki/Access_control_list"), and a short description of using these on Ubuntu [here]("http://tlug.dnho.net/?q=node/171")).  These can be useful for ensuring the expected shared permissions for multi-user setups, but the options are *only* relevant if your NAS actually has ACL support.  To test that, ssh into your NAS, type in "setfa" (minus the quotes) and hit tab -- if this autocompletes into "setfacl", then your NAS does have support installed.  Next, these are relevant if the directories you're sharing have what are called "default ACLs" included in their attributes.  These are indicated in the output of the [font=courier]ls -l[/font] command if there is a plus sign **_+_** after the usual permissions.  Since all of your shares are in the /raid directory, run this:
```
ls -l /raid
```
If the entries for your shared directories look like this:
```
ls -l /raid
total 20
...
drwxrwx---+ 2 admin admingro 4096 Mar 31 17:17 /raid/Craig
...
```

If there's no plus sign, your shared directories aren't using the extended ACL functionality, and all of these ACL-related options are moot and can (maybe even should?) be removed:

[B][map acl inherit]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPACLINHERIT") = yes
[inherit acls]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INHERITACLS") = yes[/B]

Another common option is [font=courier][inherit permissions]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INHERITPERMISSIONS")[/font], but as I understand it, this refers to your basic owner / group / other permissions.  Files or directories in such a share will inherit the share directory's permissions, instead of the normal Unixy way of having permissions set based on the umask of the user.  Inheriting from the folder is a *very* useful option for shared folders, otherwise new folders and directories will usually only be accessible by the user that created them -- a pain in the rear.  On the flip side, this option is largely moot for any single-user shares.  

The shares you want publicly accessible by guest accounts **must** have at least the [font=courier][guest ok]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK") = yes[/font] option set (synonym for [font=courier]public = yes[/font]).  I note that your ostensibly public shares are missing this, and instead only have [font=courier][guest only]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTONLY") = yes[/font].  But, from the man page section (emphasis mine):
> If this parameter is [font=courier]yes[/font] for a service, then only guest connections to the service are permitted. **This parameter will have no effect if [font=courier]guest ok[/font] is not set for the service.**

This would help explain why your guest access isn't working too well.  However, there are two more wrinkles to guest access.  One is that guest access occurs using the Ubuntu username specified in the [font=courier]guest account[/font] option in your [font=courier][global][/font] section, which in your file is [font=courier][guest account]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT") = nobody[/font] -- and given that this username is usually *extremely* limited in what it can do in terms of filesystem permissions, your guest users are highly unlikely to be able to do anything on your shares except maybe read them.  Note that filesystem permissions take priority over Samba permissions -- if the share definition says [font=courier]read only = no[/font] (same as [font=courier]writable = yes[/font]), but your filesystem permissions for that user don't include the **_w_**, you won't be able to write.  I'd suggest you change that "nobody" value to something else, maybe a new user account you set up just for Samba guest access:
```
sudo adduser --no-create-home sambaguest
```
Then make sure this username has the required access to your shared folders, perhaps by setting up a group, adding this user (and any others you're using for Samba), and then making sure this group is the primary for your shared directories:
```
sudo addgroup sambausers
sudo usermod -aG sambausers USERNAME # <-- repeat for all usernames you're using
sudo chgrp -R sambausers /raid
```
Then you'll have to go through and make sure the shared directories that you want group access to have r / w / x perms for the group, using the [font=courier]chmod[/font] command.  

The second wrinkle to Samba group access depends on your security mode, which here is "user".  In this case, you also need to set the [font=courier][map to guest]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPTOGUEST")[/font] option, as noted in the man page:
> Note that this parameter is needed to set up "Guest" share services when using security modes other than share and server. This is because in these modes the name of the resource being requested is not sent to the server until after the server has successfully authenticated the client so the server cannot make authentication decisions at the correct time (connection to the share) for "Guest" shares.
...which you've done.  And I think "Bad User" should be fine.  

I've already gone over the [font=courier][map archive]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPARCHIVE")[/font] and [font=courier][map hidden]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MAPHIDDEN")[/font] options.  

The [font=courier][force create mode]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE")[/font] option is set to "0000" in all cases, which is the default value and thus does nothing anyway.  

Your [font=courier][create mask]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK")[/font] option would seem to conflict with the [font=courier][inherit permissions]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INHERITPERMISSIONS")[/font] option.  I'm not sure which one wins out, but I strongly doubt that having both set is a good idea.
----------

That should just about do it.  Permissions are a big, fugly, complicated subject, and one that I'm still struggling with (experimenting with setting up full ACLs for proper shared group directories under NFS, which offers no "inherit" option).  You might want to read up some on the Wikipedia page [here](http://en.wikipedia.org/wiki/File_system_permissions).  

I hope this helps you get your NAS properly configured.

Cheers,

Eiríkr

---

