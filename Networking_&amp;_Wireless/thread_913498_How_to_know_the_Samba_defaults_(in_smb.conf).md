---
title: "How to know the Samba defaults? (in smb.conf)"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by gregphil on 2008-09-07
I read that in the most recent release of ubuntu & Samba the default authorization protocol has changed to ntlmv2.  But when I look in the doc's that came with the distribution (man smb.conf) I see these listed as the defaults:

client use spnego = yes
client lanman auth = yes
client ntlmv2 auth = no
client plaintext auth = no
lanman auth = no
ntlm auth = yes
security = USER

The default example /etc/smb.conf does not seem to change any of these, so how can I know what the actual 'default' Samba authorization level being used is?  Is there someway to list the current "effective" samba settings?  (there are about 340 possible settings).  I know I can force a specific setting to be something, but if the default looks OK I would like to leave that line out of the smb.conf file.  Otherwise I would need to include a line for each possible settings, and there are *many* of them. (see below)

Here is my attempt to organize the possible Samba 3.028a-1 settings (Global and Service sections) as well as list the default setting:

#=====================================
# GLOBAL SECTION parameter defaults
#=====================================
abort shutdown script = ""
add group script =
add machine script =
add port command =
add printer command =
add share command =
add user script =
afs username map =
algorithmic rid base = 1000
allow trusted domains = yes
announce as = NT Server
announce version = 4.9
auth methods =
bind interfaces only = no
browse list = yes
change share command =
check password script = Disabled
client lanman auth = yes
client ntlmv2 auth = no
client plaintext auth = no
client schannel = auto
client signing = auto
client use spnego = yes
#config file = No Default
cups server = ""
deadtime = 0
debug hires timestamp = no
debug pid = no
debug prefix timestamp = no
debug timestamp = yes
debug uid = no
#default service = No Default
defer sharing violations = True
delete group script =
deleteprinter command =
delete share command =
delete user from group script =
delete user script =
disable spoolss = no
display charset = UTF8
dns proxy = yes
domain logons = no
domain master = auto
#dos charset = No Default
enable asu support = no
enable privileges = yes
encrypt passwords = yes
enhanced browsing = yes
enumports command =
eventlog list =
get quota command =
guest account = nobody
homedir map =
host msdfs = yes
hostname lookups = no
#idmap alloc backend = No Default
#idmap alloc config = No Default
idmap backend = tdb
idmap cache time = 900
#idmap config No Default
#idmap domains No Default
idmap gid =
idmap negative cache time = 120
idmap uid =
include =
interfaces =
keepalive = 300
kernel oplocks = yes
lanman auth = no
large readwrite = yes
#ldap admin dn No Default
ldap delete dn = no
ldap group suffix =
ldap idmap suffix =
ldap machine suffix =
ldap passwd sync = no
ldap replication sleep = 1000
ldapsam:editposix = no
ldapsam:trusted = no
ldap ssl = start_tls
ldap suffix =
ldap timeout = 15
ldap user suffix =
lm announce = auto
lm interval = 60
load printers = yes
local master = yes
lock directory = ${prefix}/var/locks
lock spin count = 0
lock spin time = 200
#log file No Default
#log level No Default
logon drive =
logon home = \\%N\%U
logon path = \\%N\%U\profile
logon script =
lpq cache time = 30
machine password timeout = 604800
mangle prefix = 1
mangling method = hash2
map to guest = Never
max disk size = 0
max log size = 5000
max mux = 50
max open files = 10000
max protocol = NT1
max smbd processes = 0
max stat cache size = 1024
max ttl = 259200
max wins ttl = 518400
max xmit = 16644
message command =
min protocol = CORE
min wins ttl = 21600
name cache timeout = 660
name resolve order = lmhosts host wins bcast
netbios aliases =
#netbios name = # machine DNS name
netbios scope =
nis homedir = no
ntlm auth = yes
nt pipe support = yes
nt status support = yes
null passwords = no
obey pam restrictions = no
open files database hash size = 10007
oplock break wait time = 0
os2 driver map =
os level = 20
pam password change = no
panic action =
paranoid server security = yes
passdb backend = smbpasswd
passdb expand explicit = no
passwd  chat  =  *new*password* %n\n*new*password* %n\n *changed*
passwd chat debug = no
passwd chat timeout = 2
passwd program =
password level = 0
password server =
pid directory = ${prefix}/var/locks
preferred master = auto
preload =
preload modules =
printcap cache time = 750
printcap name = /etc/printcap
private dir = ${prefix}/private
read bmpx = no
read raw = yes
realm =
remote announce =
remote browse sync =
rename user script = no
reset on zero vc = no
restrict anonymous = 0
root directory = /
security = USER
server schannel = auto
server signing = Disabled
server string = Samba %v
set primary group script =
set quota command =
show  add  printer wizard = yes
shutdown script =
smb passwd file = ${prefix}/private/smbpasswd
smb ports = 445 139
socket address =
socket options = TCP_NODELAY
stat cache = yes
svcctl list =
syslog = 1
syslog only = no
template homedir = /home/%D/%U
#template shell No Default
time offset = 0
time server = no
unix charset = UTF8
unix extensions = yes
unix password sync = no
update encrypted = no
use kerberos keytab = False
use mmap = yes
username level = 0
username map =
username map script =
usershare allow guests = no
usershare max shares = 0
usershare owner only = True
usershare path = /var/lib/samba/usershares
usershare prefix allow list = NULL
usershare prefix deny list = NULL
usershare template share = NULL
use spnego = yes
utmp = no
#utmp directory = # Determined automatically
winbind cache time = 300
winbind enum groups = no
winbind enum users = no
winbind expand groups = 1
winbind nested groups = yes
winbind normalize names = no
winbind nss info = template
winbind offline logon = false
winbind refresh tickets = false
winbind rpc only = no
winbind separator = \
winbind trusted domains only = no
winbind use default domain = no
#wins hook No Default
wins proxy = no
wins server =
wins support = no
workgroup = WORKGROUP
write raw = yes
wtmp directory =

#=====================================
# SERVICE SECTIONS parameter defaults
#=====================================
acl check permissions = True
acl compatibility = Auto
acl group control = no
acl map full control = True
admin users =
afs share = no
aio read size = 0
aio write size = 0
allocation roundup size = 1048576
available = yes
blocking locks = yes
block size = 1024
browseable = yes
case sensitive = no
change notify = no
comment =
copy =
create mask = 0744
csc policy = manual
cups options = ""
default case = lower
default devmode = yes
delete readonly = no
delete veto files = no
#dfree cache time = No Default
#dfree command = No Default
directory mask = 0755
directory security mask = 0777
dmapi support = no
dont descend =
dos filemode = no
dos filetime resolution = no
dos filetimes = yes
ea support = no
fake directory create times = no
fake oplocks = no
follow symlinks = yes
force create mode = 000
force directory mode = 000
force directory security mode = 0
force group =
force printername = no
force security mode = 0
force unknown acl user = no
force user =
fstype = NTFS
guest ok = no
guest only = no
hide dot files = yes
hide files =
hide special files = no
hide unreadable = no
hide unwriteable files = no
hosts allow =
hosts deny =
inherit acls = no
inherit owner = no
inherit permissions = no
invalid users =
kernel change notify = yes
level2 oplocks = yes
#locking No Default
#lppause command = No Default
lpq command =
lpresume command =  /usr/bin/lpalt %p-%j -p2
#lprm command = determined by printing parameter
#magic output = <magic script name>.out
magic script =
mangled map =
mangled names = yes
mangling char = ~
map acl inherit = no
map archive = yes
#map hidden No Default
map read only = yes
map system = no
max connections = 0
max print jobs = 1000
max reported print jobs = 0
min print space = 0
#msdfs proxy No Default
msdfs root = no
nt acl support = yes
only user = no
oplock contention limit = 2
oplocks = yes
path =
posix locking = yes
postexec =
preexec =
preexec close = no
preserve case = yes
printable = no
#print command No Default
printer admin =
printer name = none
#printing No Default
printjob username = %U
profile acls = no
#queuepause command No Default
queueresume command =
read list =
read only = yes
root postexec =
root preexec =
root preexec close = no
security mask = 0777
set directory = no
share modes = yes
short preserve case = yes
store dos attributes = no
strict allocate = no
strict locking = Auto
strict sync = no
sync always = no
use client driver = no
username =
use sendfile = false
valid users =
veto files =
veto oplock files =
vfs objects =
#volume = # the name of the share
wide links = yes
#writeable No Default
write cache size = 0
write list =

---

### Post by dmizer on 2008-09-07
Your best source of information for default options is in the man file. Trust the man file before you trust the default config.

Otherwise you can find most anything you need here: [http://us1.samba.org/samba/docs/](http://us1.samba.org/samba/docs/) and here: [http://wiki.samba.org/index.php/Main_Page](http://wiki.samba.org/index.php/Main_Page)

Here's where you can find the Samba feature change history: [http://wiki.samba.org/index.php/Samba_Features_added/changed_(by_release](http://wiki.samba.org/index.php/Samba_Features_added/changed_(by_release))

---

### Post by gregphil on 2008-09-10
I looked at the pages you referenced and the "change list" but could not find anything about the authorization method currently being used (by default) or any past changes to this (say from Samba 2.x.yy to Samba 3.x.yy)

I care because I am trying to create an example of how ubuntu can do the simplest peer-to-peer file sharing with Windows boxes (probably what 80% of the new to ubuntu uses want to do).  However if the Windows shares are setup to authenticate the user (i.e. not to allow anonymous or "guest" logins) I can not get ubuntu to browse the Windows shares.  (and I am not alone).  I had seen some posts claiming the default Samba authentication method has been changed to ntlmv2 and I wanted to check if this was part of the problem.  While I don't have any legacy (Win95 etc) windows boxes lying around, apparently many others do, and they don't support ntlmv2.

In any event there appears to be a bug in the gnome gvfs library which the nautilus network file browser tries to use to authenticate.  That bug prevents nautilus from listing the available shares on a Windows box (if authentication is required to use the share on the windows box).  Nautilus CAN connect if you enter the full path to the share, but that is not "browsing".

[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/208302](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/208302)  (etc)

[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

If you have any more info on how to make peer-to-peer shared file browsing work, I would like to try it.  It must be true peer-to-peer (using DHCP) so setup can be simple, and so no one computer is required to be present and turned on for the other computers to share files. (Windows boxes can do this, so you know it is possible!).  I am told ubuntu 7.10 could do this no problem.

Thank You.

---

### Post by dmizer on 2008-09-10
Here's a post I made earlier with multiple references for potential fixes for Ubuntu being unable to browse Windows shares: [http://ubuntuforums.org/showpost.php?p=5646796&postcount=10](http://ubuntuforums.org/showpost.php?p=5646796&postcount=10)

It's been my experience that Windows network browsing problems are caused by a variety of things, so there's not going to be one silver bullet configuration to solve all problems, and browsing problems are not always gvfs related.

Things that are helpful:
1) a properly configured smb.conf file (where Ubuntu is NOT the domain master)
2) a properly configured Windows network with all machines under the same workgroup name
3) properly configured firewalls (Ubuntu and Windows)
4) properly configured winbind server in Ubuntu
5) correct order of hosts resolution in /etc/nsswitch (wins must be resolved before dns)

I do have a lot of experience with samba and cifs, and I support what you're trying to do so please feel free to keep this dialogue moving forward and I'll do what I can to provide answers.

---

### Post by gregphil on 2008-09-11
Thanks for your reply, but.....

I could make it work myself IF I enabled a server (such as WINS) on a machine.  The problem here is that only ONE machine can have WINS enabled (or be a domain master etc) so for the small network to work at all that particular machine would need to up and running.  I turn off my machines when I am not around so this is not an option. I also have enough machines (8 or so....) that it is not clear which few I might have on at a given time.

Under Windows this is no problem, basic peer-to-peer file sharing(authenticated for some sense of security) works just fine and no one machine has to be configured as the "master".

This can work under CentOS 5.2 and KDE, and I hear it used to work under ubuntu 7.10.  However in ubuntu 8.04.1 it does not seem to be possible to make it work anymore (at least using the GUI applications).  However the command line "smbclient" still works to browse and connect to peer-to-peer shares from a Windows box.

I believe this is a bug in the new gnome gvfs library:
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

I was hoping there was some reasonable work-around.

Thank You.

---

