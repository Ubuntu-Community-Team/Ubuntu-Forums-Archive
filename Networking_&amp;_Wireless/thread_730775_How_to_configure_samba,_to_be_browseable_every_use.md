---
title: "How to configure samba, to be browseable every user on LAN??"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by rado3105 on 2008-03-21
I have local network: 192.168.76.0/24, almost every user on LAN is windows user, I want  files on my linux notebook(ubuntu) to be shared amongst all user on LAN. If they put in windows explorer(or in total commander my ip address: 192.168.76.99, they will get on my shared folders without any autorization. 
Could you help, I tried it many ways but it didn´t help. 

My smb.conf is:
```

[global]
netbios name = R-C-LAPTOP
server string = CAD architects, Stockholm. East 32nd st, 34th floor
workgroup = RCLAN-RUDINA
security = share
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
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
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

[public]
comment = disk-D
path = /media/sda5
public = yes
writable = no



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
```

---

### Post by dmizer on 2008-03-21
make a backup of your current smb.conf file:
```
sudo cp /etc/samba/smb.conf /etc/smb/smb.conf-old
```
then if worst comes to worst and nothing works, you can return to your old configuration by doing this:
```
sudo cp /etc/samba/smb.conf-old /etc/smb/smb.conf
sudo /etc/init.d/samba restart
```

double check to make sure you have the samba server package installed on your system:
```
sudo aptitude install samba samba-common
```

add your ubuntu user to the samba group with the following command:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
"[COLOR="Red"]ubuntu_username[/COLOR]" should be replaced with the actual username on your ubuntu computer.

now, edit your /etc/samba/smb.conf file with your favorite editor (as root: sudo), delete everything in it, and replace it with this:
```
[global]
    ; General server settings
    netbios name = R-C-LAPTOP
    server string = CAD architects Stockholm East 32nd st 34th floor
    workgroup = RCLAN-RUDINA
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[public]
    comment = disk-D
    path = /media/sda5
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]ubuntu_username[/COLOR]
    force group = [COLOR="Red"]ubuntu_username[/COLOR]
```
"[COLOR="Red"]ubuntu_username[/COLOR]" should be replaced with the actual username on your ubuntu computer.

restart the samba server:
```
sudo /etc/init.d/samba restart
```

then your colleagues will be able to see your public share accross the lan by going to: smb://R-C-LAPTOP/public ... or by browsing to it under the "my network places".  if you need help sharing printers and some of the other things you have listed in your old smb.conf, we can work on that after you've established a working file share (start simple, work up).

---

### Post by EmoDx on 2008-03-21
Please explain to me how to edit this as root. When I browse to that file and right click on it, there isn't a way to open as root/sudo. How do I make this file accessible for editing? Thank you,

-Emo

---

### Post by Eiríkr on 2008-03-21
You'll need to use the terminal to get at it.  Open a terminal, and type:
```
sudo gedit /etc/samba/smb.conf
```
... and it will open for editing in the gedit application.  Similarly, all of DMizer's commands should be run in a terminal.  Type them in exactly as s/he's entered them.  

Incidentally, where did you get your current smb.conf file?  There's an enormous amount of very obscure options in there that very likely do not apply to your current situation.  These two in particular are guilty of preventing access:
```
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24 
```

As you state in your post, your network interface is **192.168.76.99**, and you want folks on the subnet **192.168.76.0/24** to have access.  These two options here directly contradict this, by only allowing access from the 192.168.0.0/24 subnet (i.e. machines with IP addresses in the 192.168.0.XXX range), and only listening for incoming connections on any interfaces on your machine that belong to that same subnet (which apparently do not exist).  

Anyway, I'd follow DMizer's instructions to see if you can get a basic setup running, and then you can add additional shares to it as needed.

Good luck,

Eiríkr

---

### Post by dmizer on 2008-03-21
for ubuntu:
```
gksudo gedit /etc/samba/smb.conf
```

for kubuntu:
```
kdesu kate /etc/samba/smb.conf
```

for xubuntu:
```
gksudo mousepad /etc/samba/smb.conf
```

---

### Post by rado3105 on 2008-03-22
I had to change sharing parameters to be that share browseable for anybody like this:

> [Disk-D]
    comment = Disk-D
    path = /media/sda5
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = r-c
    force group = r-c
    writable = no

---

### Post by dmizer on 2008-03-22
okay, you can't have both:
readonly = no
writeable = no

these two options mean the opposite thing.

if you want everyone to be able to read, but not write, it should look like this:
```
[Disk-D]
comment = Disk-D
path = /media/sda5
browseable = yes
[COLOR="Red"]read only = yes[/COLOR]
guest ok = yes
create mask = 0644
directory mask = 0755
force user = r-c
force group = r-c
```

if you want everyone to be able to read and write, it should look like this:
```
[Disk-D]
comment = Disk-D
path = /media/sda5
browseable = yes
[COLOR="Red"]read only = no[/COLOR]
guest ok = yes
create mask = 0644
directory mask = 0755
force user = r-c
force group = r-c
```

---

### Post by Eiríkr on 2008-03-22
@rado3105 -- 

I would strongly recommend that you have a look over [the online man page for the smb.conf file]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  It lists *every* option, tells you whether it can be used globally or just in share definitions, and explains what it does.  

Cheers,

Eiríkr

---

### Post by hanif on 2008-03-24
Dear All 

i am getting this error when i run this command on my Ubuntu 6.06 box

hanif@hanif-desktop:~$ sudo aptitude install samba samba-common
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up samba (3.0.22-1ubuntu3.6) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.6) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba

Please help me share my linux and xp

---

### Post by Eiríkr on 2008-03-24
@Hanif --

Please post your concern as a separate, new thread.  Your post has nothing to do with Samba share configurations, and so posting here is hijacking the thread (not a good thing).  Also, people who might know about Samba installation problems might not look at a Samba networking configuration thread, and therefore never see your concern.

Again, please start a new thread for your post.  

Thank you,

Eiríkr

---

### Post by hanif on 2008-03-24
ok

---

### Post by slackmaster on 2008-03-28
Hello dmizer,

Thanks for your tutorial on configuring samba shares. So far, it seems the most promising I've seen yet.
But it isn't working for me.  

Let me outline what I do know about my current samba server configuration.

1.Samba server is installed
2.I added the Ubuntu user which I use to log in.  I'll call it 'myname'.   So I added 'myname' to the usergroup 'myname'.   
3.Here is what my current smb.conf file looks like with comments and questions.  Take a look at the file and refer back to questions here.
4.Do I set the netbios name in the smb.conf file?  Or is it already set and I have to make smb.conf match it? 
5.The workgroup listed is exactly the same as the windows workgroup of my one windows machine.  
6.I'm not sure what to set the serverstring as.  
7.I followed your security recommendation.  I checked network tools to set the right name for my interface.  I use a WRT54G Rev 6 wireless router for my wireless windows machine, the wireless ubuntu laptop, and this Dell desktop.  
8.I used 'myname' for the user and group but in the real file there are no qoutations and it contains my real name of course.

On my windows machine, I attempted to locate my shared folder on the network but it never appears, even with my sunbelt firewall off.

I tried logging into my ubuntu machine using the IP address and share path location on this machine but it cannot find the network drive.  
I tried both the broadcast IP address and the regular IP address of listed in ifconfig.
I'm not sure what I'm missing here.  Maybe it is something obvious.  If you notice anything, please let me know.

Thanks so much for your help.
```

[global]

    ; General server settings

    netbios name = DELL

    server string = SMTECH

    workgroup = SMTECH

    announce version = 5.0

    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    interfaces = lo, eth0

    bind interfaces only = true



    passdb backend = tdbsam

    security = share

    null passwords = true

    username map = /etc/samba/smbusers

    name resolve order = hosts wins bcast



    wins support = no



    printing = CUPS

    printcap name = CUPS



    syslog = 1

    syslog only = yes



[public]

    comment = disk-D

    path = /home/samba/

    

    read only = no

    guest ok = yes

    create mask = 0644

    directory mask = 0755

    force user = 'myname'

    force group = 'myname'

available = no

browsable = yes

public = no

writable = no



[home]

path = /home

available = yes

browsable = yes

public = yes

writable = no



[samba]

path = /home/samba

available = yes

browsable = yes

public = yes

writable = no
```

---

### Post by Eiríkr on 2008-03-28
> **slackmaster said:**
> But it isn't working for me.  

Any specifics?  In Explorer, click My Network Places -> Entire Network -> Microsoft Windows Network -> WORKGROUP -> SERVER -> SHARE.  How far down can you get?


> **slackmaster said:**
> 3.Here is what my current smb.conf file looks like with comments and questions.  Take a look at the file and refer back to questions here.

Comments below, after I answer your questions here.


> **slackmaster said:**
> 4.Do I set the netbios name in the smb.conf file?  Or is it already set and I have to make smb.conf match it? 

The smb.conf file is where you set the netbios name of your Samba server.  If nothing is set, it should default to your hostname.  Refer to [the man page section here]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NETBIOSNAME").


> **slackmaster said:**
> 5.The workgroup listed is exactly the same as the windows workgroup of my one windows machine.  

This is fine, so long as the two match.


> **slackmaster said:**
> 6.I'm not sure what to set the serverstring as.  

Totally optional.  From [the man page section]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SERVERSTRING"):

> This controls what string will show up in the printer comment box in print manager and next to the IPC connection in net view. It can be any string that you wish to show to your users.

It also sets what will appear in browse lists next to the machine name.


> **slackmaster said:**
> I tried logging into my ubuntu machine using the IP address and share path location on this machine but it cannot find the network drive.  

What do you mean by "network drive"?  Did you map one to your Ubuntu share under Windows in the past?


> **slackmaster said:**
> I tried both the broadcast IP address and the regular IP address of listed in ifconfig.

The broadcast address is just that, for broadcasting, and would never work for any kind of browsing unless your network config is *really* screwy.  As in, it would take a lot of work to make it that screwy.  ;)

----------

And now for the smb.conf options.  I only comment on options that seem noteworthy.

**[global]**

**[announce version]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#ANNOUNCEVERSION") = 5.0**

This is an optional parameter, and probably shouldn't be messed with anyway.  Refer to the man page section linked to in the parameter name for details.  You'll want to delete this line from your conf file.


**[security]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITY") = [share]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITYEQUALSSHARE")**

I've generally found "share" security to be problematic myself, but as with anything, YMMV.  


**[null passwords]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#NULLPASSWORDS") = true**

This is only relevant if you have Samba access accounts that are explicitly defined without passwords.  This is generally not a good idea.


**[username map]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP") = /etc/samba/smbusers**

Useful if you actually need username mapping.  Refer to the linked man page section for details.  


**[wins support]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WINSSUPPORT") = no**

I've found that setting this to "yes" tends to provide better browsability.  Note that you can only have *one* machine defined as a wins server on your network.  Win XP does not default to being a wins server, so you're safe unless you've explicitly altered this setup in your Win XP networking options.


[B][printing]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTING") = CUPS
[printcap name]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PRINTCAPNAME") = CUPS[/B]

These are both share-level *only*, and should not appear in your [global] section.  They're also only relevant anyway if you're sharing a printer, which you're not.  

Let me guess, you've used gsambad in the past, no?  This tool is **amazingly terrible** at configuring Samba, and I've seen flabbergastingly ugly conf files produced by gsambad.  Please ***never*** use this tool again.  (At least, don't until the devs get off their backsides and fix it.)


**[syslog]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOG") = 1**

Already the default value, so may be deleted to make your conf file simpler.


**[syslog only]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SYSLOGONLY") = yes**

Generally not needed, and probably not a good idea as it just makes your syslog that much bigger and harder to find things in.  Better to delete this line and thereby use the default value of "no" to have logging just go to the specific Samba log files in the /var/log/samba directory.



**[public]**

**[path]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PATH") = /home/samba/**

Looks fine.  Make sure whatever username you're using has the needed filesystem permissions on this directory.


[B][guest ok]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTOK") = yes
[public]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PUBLIC") = no[/B]

These two are synonyms, but you have them set to contradictory values.  Also note that even guest access uses a regular Ubuntu username underneath.  Unless you specify a username in the [global] [guest account]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT") option, it defaults to user "nobody", which is *very* limited and is almost guaranteed to have no permissions on any of your shares.  Forgetting to specify a guest account is probably the single most common Samba share access permission problem.


[B][create mask]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CREATEMASK") = 0644
[directory mask]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#DIRECTORYMASK") = 0755[/B]

In general, it is much more secure and less error-prone to manage filesystem permissions at the filesystem level, through judicious use of group membership, file / directory ownership, and the [font=courier]chmod[/font] and [font=courier]chown[/font] / [font=courier]chgrp[/font] commands.  Have a look at [post=4496702]this post[/post] for a description of how to configure filesystem permissions for both single-user and multi-user setups.  


[b][force user](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEUSER) = 'myname'
[force group](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEGROUP) = 'myname'[/b]

It's much better and less error-prone to use the guest account [global] option for guest access instead of forcing users and groups.  


**[available](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#AVAILABLE) = no**

This essentially turns the share off, so no one can access it or even see it.  The default is "yes", so you can delete this line to restore the default value.  


**[browsable](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BROWSEABLE) = yes**

Already the default value, so delete this line to simplify your conf file.


**[writable](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WRITEABLE) = no**

Already the default value, so delete this line to simplify your conf file.  Same as "read only = yes".



**[home]**

[b]available = yes
browsable = yes
writable = no[/b]

Again, these are already the defaults, and may therefore be deleted.  


**public = yes**

Access will default to the guest account, which, since you haven't defined one, defaults to user "nobody".  "nobody" has read permissions on the /home directory itself (since all accounts are allowed access), but will have no access at all to any sub-directories.



**[samba]**

[b]available = yes
browsable = yes
writable = no[/b]

Again, these are already the defaults, and may therefore be deleted.  


**public = yes**

Access will default to the guest account, which, since you haven't defined one, defaults to user "nobody".  "nobody" has read permissions on the /home directory itself (since all accounts are allowed access), but will have no access at all to any sub-directories, **including** the /home/samba path used for this share.

----------

Guest access is really only needed if you don't know ahead of time who will be accessing your shares.  It is the source of more errors and problems and posts on this Forum about Samba than I can count.  User-based security with no guest access does indeed require a Samba username and password, but *only for the first time a share is accessed* -- all three of Linux, Mac, and Windows include mechanisms to store the share login info so you never need to enter it again.  (Windows has a bug related to overly aggressive login info caching that prevents login info from being changed, causing problems if you need to access a share using a different login.  Details on fixing that are [thread=720889]here[/thread].)  

HTH,

Eiríkr

---

