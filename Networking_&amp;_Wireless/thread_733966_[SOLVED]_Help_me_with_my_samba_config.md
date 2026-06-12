---
title: "[SOLVED] Help me with my samba config"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Cellwind929 on 2008-03-24
I'm working on setting up samba to share my raid 5 storage array. I have it mounted as /mnt/storage. I used GSAMBAD to configure samba, and everything seems alright. GSAMBAD says nmbd and winbindd are inactive tough, and my shares aren't showing up in windows. What do I need to do get everything setup right?

If this is in the wrong subforum, I apologize, I just saw some other samba threads here and thought this was the place for them.

Heres my config file:
```
[global]
netbios name = cellserver
server string = 
workgroup = MSHOME
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = yes
wins server = 
wins proxy = no
dns proxy = no
preserve case = no
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = no
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =


[Storage]
path = /mnt/storage
comment = Storage
valid users = cellwind929, patron
write list = cellwind929
admin users = cellwind929
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

```

Thanks guys!

---

### Post by Eiríkr on 2008-03-24
I've seen really scattershot results with gsambad, with a number of cases of horrific conf file mangling.  I would *strongly* recommend you spend the time to learn about the smb.conf file format and options by referencing [the online man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), and try to wean yourself off of such GUI Samba config tools, as they are inevitably a step or two behind any changes in Samba itself.  Also, while nmbd should be up and running, winbind is completely unnecessary for basic network setups -- I certainly don't have it on my machine (not even installed), and my shares show up just fine over on my XP box.  

That said, let's look over your conf file...

**Great googaly moogaly**, this is ugly!  :shock:  Here's your [font=courier][global][/font] section, annotated.  Note that the "See the man page section" text includes hyperlinks, which I've marked in blue as otherwise they don't seem to show in [font=courier][ code ][/font] sections.  
```
[global]
   netbios name = cellserver
   server string =      # Empty, so either set something or delete the line
   workgroup = MSHOME
   security = user      # The default value, so may be omitted
   hosts allow = 127. 192.168.0.
   interfaces = 127.0.0.1/8 192.168.0.0/24 
   remote announce = 192.168.0.255
        # Unnecessary option.  See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#REMOTEANNOUNCE).
   remote browse sync = 192.168.0.255
        # Unnecessary option.  See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#REMOTEBROWSESYNC).
   printcap name = /etc/printcap
        # Doesn't belong in [global] -- is only relevant in
        # printer share definition sections.  See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME).
   load printers = yes  # The default value, so may be omitted
   cups options = raw
        # Doesn't belong in [global] -- is only relevant in
        # printer share definition sections.  See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CUPSOPTIONS).
   printing = cups
        # Doesn't belong in [global] -- is only relevant in
        # printer share definition sections.  See [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING).
   guest account = smbguest
   log file = /var/log/samba/samba.log
   max log size = 1000
   null passwords = no  # The default value, so may be omitted
   username level = 8
        # Generally irrelevant unless you have DOS clients.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMELEVEL).
   password level = 8
        # Generally irrelevant unless you have DOS or Win95-98 clients.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PASSWORDLEVEL).
   encrypt passwords = yes
   unix password sync = yes
        # Generally not a good idea.  See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#UNIXPASSWORDSYNC).
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   local master = no
   domain master = no
   preferred master = no
        # Unless you have some fancy setup with more than one Samba server, 
        # you probably want your Samba server to set all three of these to "yes".
   domain logons = no
        # Generally irrelevant unless you have Win95-98 clients and are doing 
        # fancy Windows domain stuff.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DOMAINLOGONS).
   os level = 33
        # Okay, but then again the default value should work just fine,
        # so you can leave this line out entirely.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#OSLEVEL).
   logon drive = m:
        # Very obscure and likely completely unnecessary option.
        # Only useful for NT Workstation clients.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONDRIVE).
   logon home = \\%L\homes\%u
        # Very obscure and likely completely unnecessary option.
        # Only useful for NT Workstation or Win95-98 clients with fancy domain stuff.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONHOME).
   logon path = \\%L\profiles\%u
        # Very obscure and likely completely unnecessary option.
        # Only useful for NT Workstation clients using roaming profiles.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONPATH).
   logon script = %G.bat
        # Very obscure and likely completely unnecessary option.
        # Note, "This option is only useful if Samba is set up as a logon server."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONSCRIPT).
   time server = no # The default value, so may be omitted
   name resolve order = wins lmhosts bcast
   wins support = yes
   wins server =    # Empty, so delete the line
   wins proxy = no  # The default value, so may be omitted
   dns proxy = no
   preserve case = no
   client use spnego = no
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavier-duty Kerberos authentication.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CLIENTUSESPNEGO).
   client signing = no
        # You're better off using the default value of "auto", so just delete this line.
   client schannel = no
        # You're better off using the default value of "auto", so just delete this line.
   server signing = no
        # You're better off using the default value of "auto", so just delete this line.
   server schannel = no
        # You're better off using the default value of "auto", so just delete this line.
   nt pipe support = yes
        # Note, "This is a developer debugging option and can be left alone."
        # The default value, so may be omitted
   nt status support = yes
        # Note, "This is a developer debugging option and can be left alone."
        # The default value, so may be omitted
   allow trusted domains = no
        # The default value, so may be omitted
   obey pam restrictions = yes
   enable spoolss = yes
        # Bogus option, doesn't exist.  Delete this line.
   client plaintext auth = no
        # The default value, so may be omitted
   disable netbios = no
        # The default value, so may be omitted
   follow symlinks = no
   update encrypted = yes
        # Unneeded, and only works when "encrypt passwords" is set to "no" (a bad idea).
   pam password change = no
        # The default value, so may be omitted
   passwd chat timeout = 120
   hostname lookups = no
        # The default value, so may be omitted
   username map = /etc/samba/smbusers
   smb passwd file = /etc/samba/smbpasswd
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
   add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ADDUSERSCRIPT).
   add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ADDUSERTOGROUPSCRIPT).
   add group script = /usr/sbin/groupadd '%g'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ADDGROUPSCRIPT).
   delete user script = /usr/sbin/userdel '%u'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DELETEUSERSCRIPT).
   delete user from group script = /usr/sbin/userdel '%u' '%g'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DELETEUSERFROMGROUPSCRIPT).
   delete group script = /usr/sbin/groupdel '%g'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're using heavy-duty large-scale user account 
        # database admin on Win NT systems and need to sync Samba with those.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DELETEGROUPSCRIPT).
   add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
        # Very obscure and likely completely unnecessary option.
        # Only useful if you're doing heavy-duty Samba domain stuff.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ADDMACHINESCRIPT).
   machine password timeout = 120
        # Very obscure and likely completely unnecessary option.
        # Only useful if the Samba server is part of an NT domain.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#MACHINEPASSWORDTIMEOUT).
   idmap uid = 16777216-33554431
        # Very obscure and likely completely unnecessary option.
        # Only useful if the Samba server is mapping NT and Unix users.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#IDMAPUID).
   idmap gid = 16777216-33554431
        # Very obscure and likely completely unnecessary option.
        # Only useful if the Samba server is mapping NT and Unix groups.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#IDMAPGID).
   template shell = /dev/null
        # Very obscure and likely completely unnecessary option.
        # Only useful if Winbind daemon is handling NT user information.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#TEMPLATESHELL).
   winbind use default domain = no
        # The default value, so may be omitted
   winbind separator = @
        # Very obscure and likely completely unnecessary option.
        # Only useful for Winbind daemon.
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINBINDSEPARATOR).
   winbind cache time = 360
        # Only useful for Winbind daemon.
        # May as well leave as the default, so may be omitted.
   winbind trusted domains only = yes
        # Only useful for Winbind daemon.
        # Deprecated parameter anyway, so may be omitted.
   winbind nested groups = no
        # Only useful for Winbind daemon.
   winbind nss info = no
        # Only useful for Winbind daemon.
        # Bogus value anyway, so may be omitted.
   winbind refresh tickets = no
        # Only useful for Winbind daemon.
        # The default value, so may be omitted
   winbind offline logon = no
        # Only useful for Winbind daemon.
        # The default value, so may be omitted
```

Here's that same section, after yanking out all the terrible cruft and unneeded garbage that gsambad threw in there.  Notice how much smaller it suddenly is.

```
[global]
# NetBIOS and name resolution options
   netbios name = cellserver
   workgroup = MSHOME
   wins support = yes
   dns proxy = no
   name resolve order = wins lmhosts bcast
# Network access options
   hosts allow = 127. 192.168.0.
   interfaces = 127.0.0.1/8 192.168.0.0/24 
# Logging options
   log file = /var/log/samba/samba.log
   max log size = 1000
# Master browser options
   local master = yes       # <-- Changed from "no"
   domain master = yes      # <-- Changed from "no"
   preferred master = yes   # <-- Changed from "no"
# Username and password security options
   guest account = smbguest
   username map = /etc/samba/smbusers
   encrypt passwords = yes
   obey pam restrictions = yes
   smb passwd file = /etc/samba/smbpasswd
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
   passwd chat timeout = 120
# Miscellaneous options
   preserve case = no
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   follow symlinks = no

```

----------

Now to look at your share definitions.  

**Egads**, this is just as ugly...  #-o

```
# The [homes] section here doesn't look right.
# Have a look at the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HOMESECT).
[homes]
   comment = Home Directories
   path = /home
   read only = no
   available = yes      # The default value, so may be omitted
   browseable = yes     # The default value, so may be omitted
   writable = yes       # "writable" is the opposite of "read only",
                        # so you only need one or the other
   guest ok = no        # The default value, so may be omitted
   public = no          # The default value, so may be omitted - "public" is same as "guest ok",
                        # so you only need one or the other
   printable = no       # The default value, so may be omitted
   share modes = no     
        # Note: "You should *NEVER* turn this parameter off as many Windows applications will break if you do so."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SHAREMODES).
   locking = no
        # Note: "Be careful about disabling locking either globally or in a specific service, 
        #       as lack of locking may result in data corruption. You should never need to set this parameter."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING).

# Somehow I really doubt you're running a network logon service,
# and thus you probably don't need this section at all.  
[netlogon]
   comment = Network Logon Service
   path = /home/netlogon
   read only = no
        # If it's "read only = no", then that means "writable = yes".
        # These two settings are contradicting each other here.
   available = yes      # The default value, so may be omitted
   browseable = yes     # The default value, so may be omitted
   writable = no
        # If it's "read only = no", then that means "writable = yes".
        # These two settings are contradicting each other here.
   guest ok = no        # The default value, so may be omitted
   public = no          # The default value, so may be omitted - "public" is same as "guest ok",
                        # so you only need one or the other
   printable = no       # The default value, so may be omitted
   share modes = no     
        # Note: "You should *NEVER* turn this parameter off as many Windows applications will break if you do so."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SHAREMODES).
   locking = no
        # Note: "Be careful about disabling locking either globally or in a specific service, 
        #       as lack of locking may result in data corruption. You should never need to set this parameter."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING).

# This section is *also* very likely 
# completely unnecessary for your setup.
[profiles]
   comment = User Profiles
   path = /var/samba/profiles
   read only = no
        # If it's "read only = no", then that means "writable = yes".
        # These two settings are contradicting each other here.
   available = yes      # The default value, so may be omitted
   browseable = yes     # The default value, so may be omitted
   writable = yes
        # If it's "read only = no", then that means "writable = yes".
        # These two settings are contradicting each other here.
   guest ok = no        # The default value, so may be omitted
   public = no          # The default value, so may be omitted - "public" is same as "guest ok",
                        # so you only need one or the other
   printable = no       # The default value, so may be omitted
   locking = no
        # Note: "Be careful about disabling locking either globally or in a specific service, 
        #       as lack of locking may result in data corruption. You should never need to set this parameter."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING).
   create mode = 0600
   directory mask = 0700

# Printer shares are only useful if you're actually
# sharing your printer via your Samba server machine.
# Remove this section if you're not doing that.
[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = yes     # The default value, so may be omitted
   writable = no        # The default value, so may be omitted
   guest ok = no        # The default value, so may be omitted
   public = no          # The default value, so may be omitted - "public" is same as "guest ok",
                        # so you only need one or the other
   printable = yes
   share modes = no     
        # Note: "You should *NEVER* turn this parameter off as many Windows applications will break if you do so."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SHAREMODES).
   locking = no
        # Note: "Be careful about disabling locking either globally or in a specific service, 
        #       as lack of locking may result in data corruption. You should never need to set this parameter."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING).
        
# Does the indicated path even exist on your machine?
# I've seen this section show up in a number of gsambad 
# examples, but I find it weird that folks would have
# a dedicated share solely for PDF documents... :confused:
# Remove this section if the indicated directory doesn't exist.
[pdf-documents]
   path = /home/pdf-documents
   comment = Converted PDF Documents
   available = yes      # The default value, so may be omitted
   browseable = yes     # The default value, so may be omitted
   writeable = yes
   guest ok = yes

# This also strikes me as all kinds of odd.  How often
# do you expect to be printing to PDF files?  
# Delete this section unless you really think you'll
# need it.  
[pdf-printer]
   path = /tmp
   comment = PDF Printer Service
   printable = yes
   guest ok = yes
   use client driver = yes
   printing = bsd
   print command = /usr/bin/gsambadpdf %s %u
   lpq command =
   lprm command =
   
# *Finally*, your actual share!  :)
[Storage]
   path = /mnt/storage
   comment = Storage
   valid users = cellwind929, patron
   write list = cellwind929
   admin users = cellwind929
        # This is a potentially risky option to use.
        # From the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ADMINUSERS):
        # "This is a list of users who will be granted administrative privileges on the 
        #  share. This means that they will do all file operations as the super-user (root)."
        #  You should use this option very carefully, as any user in this list will be able 
        #  to do anything they like on the share, irrespective of file permissions.
   read only = no
   available = yes      # The default value, so may be omitted
   browseable = yes     # The default value, so may be omitted
   writable = yes       # "writable" is the opposite of "read only",
                        # so you only need one or the other
   guest ok = no        # The default value, so may be omitted
   public = no          # The default value, so may be omitted - "public" is same as "guest ok",
                        # so you only need one or the other
   printable = no       # The default value, so may be omitted
   share modes = no     
        # Note: "You should *NEVER* turn this parameter off as many Windows applications will break if you do so."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SHAREMODES).
   locking = no
        # Note: "Be careful about disabling locking either globally or in a specific service, 
        #       as lack of locking may result in data corruption. You should never need to set this parameter."
        # See the [[color=blue]man page section[/color]](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING).
```

After again clearing out all the *extensive* gsambad rubbish, we arrive at the following *much* smaller set of options.  Note that I'm assuming you don't have to share your printer via Samba.

```
[Storage]
   path = /mnt/storage
   comment = Storage
   valid users = cellwind929, patron
   write list = cellwind929
   read only = no
```

----------

Whew!  As you can see, gsamabd is **enormously and egregiously messy**, and introduces tons of options you don't need, many that are possibly dangrerous, and even quite a few that are flat-out bogus.  **Bad gsambad!  No cookie!**  :evil:

Again, I would *strongly* recommend you take the time to familiarize yourself with the Samba conf file format and options by perusing [the man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  **Remember, kids, the man page is your friend.**  :D

Cheers,

Eirikr

PS -- After fixing your conf file, remember to also restart Samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by Cellwind929 on 2008-03-24
Wow, awesome reply. I'll ditch the gui and plugin the config file and give it a shot.

Thanks!

---

### Post by Cellwind929 on 2008-03-24
I've played around with the new shortened config file. The only problem I'm having is with the Networking section:
```
# Network access options
   hosts allow = 127. 192.168.0. 10.100.*.*
   interfaces = eth0
```
I go to add it to the windows network place, but windows explorer just barfs on itself and doesn't show anything.

I'm guessing I have something setup wrong.
At school, my servers ip is 10.100.7.55, and at home its 192.168.1.110.

Heres the ifconfig from the server:
```
Link encap:Ethernet  inet addr:10.100.7.55 Bcast: 10.100.255.255 Mask: 255.255.0.0
```

ipconfig from the xp desktop

IP:10.100.8.170
subnet:255.255.0.0
Default gateway: 10.100.0.1

---

### Post by Eiríkr on 2008-03-24
For starters, try commenting out the lines there in the Networking section (just add a number symbol **#** or semicolon **;** at the front of the line), save, then restart Samba:
```
sudo /etc/init.d/samba restart
```

If you can access from the XP machine after doing this, then that was definitely the issue.  If you're concerned about limiting possible unwanted access to your Samba server, you'll need to uncomment those two lines again.  When doing so, make sure that the [font=courier]interfaces[/font] value is correct (does it match what you see in [font=courier]ifconfig[/font]?).  Also, now that I look at it again, I think the proper wildcard for [font=courier]hosts allow[/font] is *not* the asterisk, but rather simply omission.  So allowing any host from the 10.100.0.0/16 subnet would look like [font=courier]10.100.[/font] rather than the value you've got at present.  

HTH,

Eiríkr

---

### Post by Cellwind929 on 2008-03-24
That solved it. I'll poke around with limiting hosts later. The only other questions I have are, when I connected to the folder, it already logged me in as user cellwind929. I got no popup dialogue, which was confusing. Maybe it's because I have a webmin session and/or ssh connection open to the computer already? Also, even as the user cellwind929, I can't write to /mnt/storage. Do I need to change the permissions of the folder somewhere?

---

### Post by Eiríkr on 2008-03-24
Windows is very stupidly aggressive about caching share authentication info, and second-guesses the user by assuming that once a share has been logged into, the user *always* wants to use the same login.  Moreover, if the valid username ever changes on the server side, Windows just stupidly fails out instead of asking the user for a new login.  Have a look at [post=4491515]KennedyM's informative HOWTO for trying to get Windows to behave[/post].  

As far as write permissions go, looking over your share definition again, I note that user cellwind929 is in the write list, but you also have the share set to "read only = no", which would seem to give write permission to anyone who can access the share.  In addition to the smb.conf file settings, however, you need to make sure that the usernames specified also have permissions to read / write / execute as desired on the filesystem itself.  You can check who can write to your [font=courier]/mnt/storage[/font] directory by typing:
[code]ls -ld /mnt/storage[/font]

If the output is unclear to you, post it here and I'll go over it for you.

Cheers,

Eiríkr

---

### Post by Cellwind929 on 2008-03-24
output for the ls -ld is as follows
```
drwxr-rx-x 2 root root 6 2008-03-24 09:03 /mnt/storage
```

I want only cellwind929 to have read/write/exectue, and then have a user account that is read only. Should read only = yes? and then give the account write privllages, or does the readonly flag supercede that?

---

### Post by Eiríkr on 2008-03-24
For your smb.conf file, yes, "read only = yes" is what you want.  Since this is the default value, you can simply remove the line to keep things simple.  This flag *only* applies to what folks connecting via Samba are allowed to do *by the Samba daemon*, so if Samba says "sure, user Bob can write," but the filesystem says "only root", Bob ain't going to be able to do much writing.  

So here, we see that root is the owner and primary group.  The first triplet of permissions is "rwx", stating that the owner (root) can **_r_**ead, **_w_**rite, and e**_x_**ecute.  The second triplet tells us that group members (in this case, members of the group "root", which is usually only the root user) can **_r_**ead and e**_x_**ecute.  The last triplet tells us what everyone else can do.  I assume that the first "x" here is a typo?  

So given your setup, I'd recommend you read over [post=4496702]this post[/post], particularly the "Multi-user" section, about setting up groups, group memberships, and filesystem permissions, and then make changes (using the [font=courier]chown[/font], [font=courier]chgrp[/font], and [font=courier]chmod[/font] commands as needed) to your [font=courier]/mnt/storage[/font] directory permissions.

Cheers,

Eiríkr

---

### Post by Cellwind929 on 2008-03-24
I followed the guide you linked. Everything works magically now. I can control the system however I want now. A big thanks again.

---

### Post by Eiríkr on 2008-03-24
Glad it worked!  :D  If that does it for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

