---
title: "Networking help"
date: 2020-06-07
forum: Networking &amp; Wireless
---

### Post by crocker-3 on 2020-06-07
I am unable to share a folders to other windows users in Mac. It worked afternoon so install then rebooted and folders do not appear. I've tried to set up SAMBA. As this is going to be my Plex server. I have a 3 TB hard drive that I need to empty with TV shows on it. When I tried to copy the files off my three terabyte hard drive the computer freezes. I also have an array card there's several years old. Any help would be appreciated. I am a Windows and Mac user. I can list hardware specs if needed. I'm using kbuntu os.

---

### Post by TheFu on 2020-06-07
> I am unable to share a folders to other windows users in Mac. 
Seems like this is a Windows and Mac-OSX question.

Which computer freezes?  Windows, OSX?

You mention kbuntu, but not what you did to share under kubuntu.  If you setup samba, perhaps posting the changes that you made to the smb.conf file would be helpful?  Also, it is much easier to get things working with a "server" has a static IP address, so does the samba server machine have a static IP?

If the steps taken can be clearly provided, always saying which computer each step happened on, then someone might be able to help.

---

### Post by crocker-3 on 2020-06-07
The kbuntu freezes when copying from the USB drive to the the raid hard drive. can't connect from a Mac at the moment tells me I don't have permission. Did not make any changes to the samba file when I get a chance I'll post the exact file.

---

### Post by TheFu on 2020-06-08
raid?
USB?

> If the steps taken can be clearly provided, always saying which computer each step happened on, then someone might be able to help. 

---

### Post by crocker-3 on 2020-06-09
I'm not sure if it's the USB freezing or the raid.

Hare is my samb conf file.
Let me know what I need to fix in it?

[global]
netbios name = plex
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
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
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
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
passdb backend = tdbsam
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
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[tv]
path = /media/bob/1D82D92961F02F48/TV
comment = No comment
valid users = %U
invalid users = %U
write list = %U
admin users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = no
locking = no
strict locking = no

---

### Post by Morbius1 on 2020-06-10
Holy Frijoles!!

Once upon a time when Samba 2 was state of the art and there were 3" books on its care and feeding an application called gadmin-samba was created to manage a samba server. Your smb.conf is a clear indication you are using it. Alas, very little of it ( and the 3" book ) has relevance to the modern version of samba that you are running. As proof you can run a diagnostic command:
```
testparm -s
```
Notice that the first 20 or so lines of the output tells you that most of the parameters you are using are either deprecated or just plain no longer exists.

You might consider resetting your smb.conf to the factory settings and starting over:

(1) Make a backup of your current smb.conf
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

(2) Copy a copy of the factory default smb.conf to the working location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```

(3) Make surgical edits to smb.conf:

** In the [global] section reset your host name - put in under the workgroup = WORKGROUP line:
```
netbios name = plex
```
[COLOR=#ff0000]*Note: If your host name is already "plex" you don't need the line above. Samba automatically sets the netbios name to the host name for you.*[/COLOR]

** As for the share I don't understand what you ( or gadmin-samba ) were going for here:
> [tv]
path = /media/bob/1D82D92961F02F48/TV
comment = No comment
[COLOR=#0000cd]valid users = %U
invalid users = %U[/COLOR]
write list = %U
admin users = %U
read only = no
available = yes
browseable = yes
writable = yes
[COLOR=#0000cd]guest ok = yes[/COLOR]
public = yes
printable = no
locking = no
strict locking = no 
Doesn't make much sense to me but you need to state how you want the clients to this system to be able to access this server. If you want access without providing user names and passwords something like this would be more efficient:
```
[tv]
path = /media/bob/1D82D92961F02F48/TV
read only = no
guest ok = yes
locking = no
strict locking = no 
force user = bob
```

After all that is done restart samba:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

[COLOR=#0000cd]**Big Note**: The only thing I don't know - because I am not a Plex user - is who plex runs as. I've read that plex runs as the user plex in which case it will never be able to access /media/bob/1D82D92961F02F48/TV because of the inherent security setting of /media/bob.[/COLOR][COLOR=#ff0000]
[/COLOR]
It would be better if you just logged into the server as plex then the share path would be /media/plex/1D82D92961F02F48/TV and [highlight]force user = plex[/highlight]. 

Or use something like this to make Plex run as "bob" and keep the path where it is: [https://forums.plex.tv/t/proper-way-to-run-plex-as-another-user-with-systemd-ubuntu-server-16-04-lts/158853](https://forums.plex.tv/t/proper-way-to-run-plex-as-another-user-with-systemd-ubuntu-server-16-04-lts/158853)

In any event I'm not qualified to talk about plex. Better left to someone who is.

---

### Post by crocker-3 on 2020-06-10
At this point all I need is for windows and Mac to be able to access the shared folder as guest. No use her name and password required is what I'm looking for. If you could make me a new SMBA config file that would be great. Using the same path that I already have. Then we could look at why it freezes when connecting 4 TB Western digital USB hard drive. When I copy files off the hard drive the computer completely freezes or runs slow I see both behaviors. That's the reason why I want to try copying the files over the network. It could be due to the age of the arrayed card. Like I stated before I have no prior experience with Linux other than screwing around with it.
Your help would be greatly appreciated in this matter.

---

### Post by Morbius1 on 2020-06-10
> If you could make me a new SMBA config file that would be great. Using the same path that I already have.
That is exactly what I did in my post.

---

### Post by crocker-3 on 2020-06-10
I'm not understanding what you did.
I added The Force = bob.
now my Mac and Windows can't even access the drive in macOS x it sees it as a ? And Windows don't even see the Plex drive. When I use the UI to browse the network.
If that's not how I'm supposed to be looking for the drive please let me know. You usually in Windows I open network see my drive and connect to it same thing in Mac OS x.

---

### Post by crocker-3 on 2020-06-11
Is there a graphical interface that I can use to set up network share?

---

