---
title: "lost ability to browse windows network"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by mmoalem on 2008-04-04
hi there all - suddenly couple of days ago i lost the ability to browse my home network on my ubuntu machine. all other machines run windows and talk flawlessly between them and my ubuntu machine did the same until it stoped - i cant think of an obvious reason (installation of new software, network hardware).
not sure where to start in working this out so any tips will be greatly appreciated ...

---

### Post by Eiríkr on 2008-04-04
Is your Ubuntu machine also set up as a Samba server (i.e. you have shares on your Ubuntu machine that you access from Windows machines)?  If so, we might need to take a look at your /etc/samba/smb.conf file.  If no, then are the Windows machines running Autoupdate?  Are they XP, or some other flavour?  What version of Ubuntu are you running?  What version of the smbclient package do you have installed (check in Synaptic)?

Cheers,

Eiríkr

---

### Post by mmoalem on 2008-04-04
hi and thanks for the reply
my ubuntu is gutsy
smbclient 3.0.26a-lubuntu2.3
i think samba server is running (i have a shared folder on this machine which used to be accessible from other windows machines)
smb.conf:
> [global]
netbios name = ubuntu
server string = 
workgroup = mshome
security = user
hosts allow = 127. 192.168.1.
interfaces = 127.0.0.1/8 192.168.1.0/240 
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
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
wins support = no
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
winbind use default domain = yes
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

all machines run XP pro

my router does dhcp and ips are at the 192.168.1.xx range

---

### Post by Eiríkr on 2008-04-04
Looking over your conf file, I noted a number of issues.  You didn't use GSAMBAD to configure your server, did you?  I've found that tool to be *incredibly* terrible at producing functional and valid conf files.  You're much better off learning the options and diving right into the conf file itself with a text editor.  Moreover, if you had specific shared folders set up in the past, it looks like GSAMBAD has deleted them.  :(

I'm guessing you're not running your Samba server as a domain controller for a Windows domain, with profiles being stored centrally on the Samba server and downloaded to client Windows machines on every login.  If this assumption is correct, remove the whole share definition sections for [netlogon] and [profiles], as these are wholly unnecessary and just introduce new ways of bugging up your configuration.  

Likewise, if you're not serving a printer via Samba that is physically connected to your Ubuntu machine, remove the [printers] share.  

I find GSAMBAD's insistence on setting up shares solely for PDF conversions and another just for a PDF printer to be quite bizarre, especially given that many other apps include PDF conversion tools built-in (such as OpenOffice.org).  Unless you really find them useful, I would further strongly recommend that you remove the whole [pdf-documents] and [pdf-printer] shares.  

Now, for the remaining options in your [global] and [homes] sections.  ;)

----------
**[global]**

[remote announce](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#REMOTEANNOUNCE)
[remote browse sync]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#REMOTEBROWSESYNC")
It's pretty unlikely that you need either of these options, as they are really only for complex network setups involving multiple Samba servers on different subnets.  This is highly improbable in any small home network.  :)  I'd suggest removing these lines, or at least commenting them out.  

[print cap name](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME)
[cups options](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CUPSOPTIONS)
[printing](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING)
These options are all *only* for use within printer share definitions, and should never appear in the [global] section.  Delete these lines.

[load printers](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOADPRINTERS)
This option is indeed a [global] option, but is moot if you're not sharing a printer.  Delete as appropriate.  

[null passwords](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NULLPASSWORDS) = no
Already the default value, and therefore redundant.  Delete this line to simplify your conf file.

[username level](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMELEVEL)
[password level](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PASSWORDLEVEL)
These options are only relevant if you have DOS machines attempting to access your Samba server.  Delete as appropriate.

[unix password sync](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#UNIXPASSWORDSYNC) = yes
This is seldom a good idea, unless you're running your Samba server as a Windows domain controller.  Delete as appropriate.  

[local master](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCALMASTER) = no
[domain master](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DOMAINMASTER) = no
[preferred master](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PREFERREDMASTER) = no
[wins support](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINSSUPPORT) = no
With a Samba server on a network with a bunch of Windows XP machines, you almost certainly want all of these set to "yes".  Otherwise, there is a chance that one of the XP machines might become the browsing master for the workgroup, and I've read that XP machines have a bug in their NetBIOS (i.e. Samba-style) name resolution functionality that makes it impossible to browse the network from a Samba client.  I suspect this is what's happened to you.  

[domain logons](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DOMAINLOGONS) = no
[time server](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#TIMESERVER) = no
Already the default value, and therefore redundant.  Delete these lines to simplify your conf file.

[logon drive](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONDRIVE)
[logon home](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONHOME)
[logon path](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONPATH)
[logon script](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOGONSCRIPT)
None of these lines are relevant unless you're using your Samba server as a Windows domain controller.  Delete as appropriate.

Good CRIKEY there's a crapload of junk here.  :evil:  *Except for* the following three lines, I'd recommend you delete all the rest of the [global] options below the "wins support" line.  
obey pam restrictions = yes
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
Keep these three lines intact, as they're related to Samba password security.


**[homes]**

Most of this looks okay, except for this line:
[locking](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING) = no
This turns file locking off, which means that two programs could wind up trying to write to one file at the same time.  This is generally a very bad idea, but for some unclear and apparently unwise reason, GSAMBAD insists on setting this to "no".  From the relevant man page section:
> Be careful about disabling locking either globally or in a specific service, as lack of locking may result in data corruption. You should never need to set this parameter.
----------

Make these changes, then restart your Samba server to make sure the daemon uses the new settings:
```
sudo /etc/init.d/samba restart
```

Let us know if you run into any other troubles.  

Cheers,

Eiríkr

---

### Post by mmoalem on 2008-04-06
hi there and thanks for the help - i was using gsambad as i'm quite clueless when it comes to editing conf files. I have followed your step by step guide but it did not work:(
my smb.conf now looks like this:
> [global]
netbios name = ubuntu

workgroup = mshome
security = user
hosts allow = 127. 192.168.1.
interfaces = 127.0.0.1/8 192.168.1.0/240 
#remote announce = 192.168.1.255
#remote browse sync = 192.168.1.255
#printcap name = /etc/printcap
#load printers = yes
#cups options = raw
#printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
#null passwords = no
#username level = 8
#password level = 8
encrypt passwords = yes
#unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = yes
domain master = yes
preferred master = yes
#domain logons = no
os level = 33
#logon drive = m:
#logon home = \\%L\homes\%u
#logon path = \\%L\profiles\%u
#logon script = %G.bat
#time server = no
name resolve order = wins lmhosts bcast
wins support = yes
#wins server = 
#wins proxy = no
#dns proxy = no
#preserve case = no
#client use spnego = no
#client signing = no
#client schannel = no
#server signing = no
#server schannel = no
#nt pipe support = yes
#nt status support = yes
#allow trusted domains = no
obey pam restrictions = yes
#enable spoolss = yes
#client plaintext auth = no
#disable netbios = no
#follow symlinks = no
#update encrypted = yes
#pam password change = no
#passwd chat timeout = 120
#hostname lookups = no
#username map = /etc/samba/smbusers
#smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
#add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/#null '%u'
#add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User #Account' -s /dev/null -g '%g' '%u'
#add group script = /usr/sbin/groupadd '%g'
#delete user script = /usr/sbin/userdel '%u'
#delete user from group script = /usr/sbin/userdel '%u' '%g'
#delete group script = /usr/sbin/groupdel '%g'
#add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba #Machine Account' -s /dev/null -M '%u'
#machine password timeout = 120
#idmap uid = 16777216-33554431
#idmap gid = 16777216-33554431
#template shell = /dev/null
#winbind use default domain = yes
#winbind separator = @
#winbind cache time = 360
#winbind trusted domains only = yes
#winbind nested groups = no
#winbind nss info = no
#winbind refresh tickets = no
#winbind offline logon = no

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
locking = yes

#[netlogon]
#comment = Network Logon Service
#path = /home/netlogon
#read only = no
#available = yes
#browseable = yes
#writable = no
#guest ok = no
#public = no
#printable = no
#share modes = no
#locking = no

#[profiles]
#comment = User Profiles
#path = /var/samba/profiles
#read only = no
#available = yes
#browseable = no
#writable = yes
#guest ok = no
#public = no
#printable = no
#locking = no
#create mode = 0600
#directory mask = 0700

#[printers]
#comment = All Printers
#path = /var/spool/samba
#browseable = yes
#writable = no
#guest ok = no
#public = no
#printable = yes
#share modes = no
#locking = no

#[pdf-documents]
#path = /home/pdf-documents
#comment = Converted PDF Documents
#available = yes
#browseable = yes
#writeable = yes
#guest ok = yes

#[pdf-printer]
#path = /tmp
#comment = PDF Printer Service
#printable = yes
#guest ok = yes
#use client driver = yes
#printing = bsd
#print command = /usr/bin/gsambadpdf %s %u
#lpq command =
#lprm command =

any more ideas?
cheers
michel

---

### Post by ivancruz on 2008-04-07
Try removing the trailing zero on interface parameter:

interfaces = 127.0.0.1/8 192.168.1.0/24

240 bits for mask bit length makes no sense.

---

### Post by Eiríkr on 2008-04-07
Thanks for catching that, ivancruz.  I'd missed it in my initial audit of the conf file options.

----------

@mmoalem --

After trimming out all the fluff from your conf file, adding the fix ivancruz spotted, adding some labels, you have this for your global options:
```
[global]
# Name resolution options
   netbios name = ubuntu
   workgroup = mshome
   name resolve order = wins lmhosts bcast
   wins support = yes
# Network security options
   hosts allow = 127. 192.168.1.
   interfaces = 127.0.0.1/8 192.168.1.0/240 # <-- change 240 here to 24
# Logging options
   log file = /var/log/samba/samba.log
   max log size = 1000
# User security options
   security = user
   guest account = smbguest
   encrypt passwords = yes
   obey pam restrictions = yes
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
# Master browser options
   local master = yes
   domain master = yes
   preferred master = yes
   os level = 33
# Misc options
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```

Now to go again over your [homes] share:

**[homes]**
   comment = Home Directories
   path = /home

   available = yes
   browseable = yes
# "available" and "browseable" are synonyms, you only need one or the other
# Plus, "yes" is the default value, so these options are redundant anyway and may 
# be deleted

   read only = no
   writable = yes
# "read only" and "writable" are antonyms, you only need one or the other

   guest ok = no
   public = no
# "guest ok" and "public" are synonyms, you only need one or the other
# Plus, "no" is the default value, so these options are redundant anyway and may 
# be deleted

   printable = no
# "no" is the default value, so this option is redundant anyway and may 
# be deleted

   share modes = no
# I'd missed this before.  From [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SHAREMODES"):
> You should *NEVER* turn this parameter off as many Windows applications will break if you do so.

   locking = yes
# This option should be deleted.  From [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LOCKING"):
> You should never need to set this parameter.

So after deleting redundant options and removing the troublesome ones, your [homes] section should look like this:
```
[homes]
   comment = Home Directories
   path = /home
   read only = no
```

GSAMBAD is a truly terrible piece of work, and I'm enormously dismayed that it's included in the Ubuntu repositories.  It might have been useful at some point in the past, but the conf files it currently outputs are worse than useless.  I would strongly recommend that you remove the GSAMBAD package from your system.  

Hope this helps,

Eiríkr

---

