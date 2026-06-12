---
title: "Samba only works after it's restarted"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by c-m on 2015-03-24
I have my 14.10 machine as a samba server, but oddly samba only works after I run "sudo service smbd restart"

I do remember seeing a thread on this but I can't find it now. 

The problem seems to be that the samba server loads up before the network card is initialised.

Is there a way to fix this once and for all?

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> I have my 14.10 machine as a samba server, but oddly samba only works after I run "sudo service smbd restart"

I do remember seeing a thread on this but I can't find it now. 

The problem seems to be that the samba server loads up before the network card is initialised.

Is there a way to fix this once and for all?How do you know that the Samba daemons are not running?

When you have the Samba server in the non-running condition (initial boot ???), what do you get from this command```
pgrep -l mbd
```

What is the exact response when you use *sudo service smbd restart * initially?  The response is different when starting the smbd daemon form when re-starting the daemon.

---

### Post by c-m on 2015-03-24
When I run 'sudo service smbd restart' I get:

```
smbd stop/waiting
smbd start/running, process 31866

```

After the restart:

```
pgrep -l mbd
1159 nmbd
31866 smbd
31871 smbd

```

Before the restart:

```

pgrep -l mbd
1206 smbd
1209 smbd
1240 nmbd


```

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> When I run 'sudo service smbd restart' I get:

```
smbd stop/waiting
smbd start/running, process 31866

```

After the restart:

```
pgrep -l mbd
1159 nmbd
31866 smbd
31871 smbd

```

Before the restart:

```

pgrep -l mbd
1206 smbd
1209 smbd
1240 nmbd


```

It appears that the Samba server is running when the machine is initially started.  Note that in all of the above tests both smbd and nmbd are running.
When restarting the service smbd just re-announcing itself to the network.  

Is **browsing the network ** initially your problem?

---

### Post by c-m on 2015-03-24
Yes. Unless I run 'sudo service smbd restart' after turning the computer on, my other devices cannot connect to the server.

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> Yes. Unless I run 'sudo service smbd restart' after turning the computer on, my other devices cannot connect to the server.
Did you use the configuration tips I gave you on your earlier Samba server (*name resolve order = bcast*).  I would also use this: *netbios name = "some name"* (where "some name" is a name that is 15 characters or less.  What do you get from this command```
hostname
```

This type of problem is due to the host naming process (NETBIOS) is not configured correctly.  What do you get from this command```
cat /etc/hosts
```

---

### Post by c-m on 2015-03-24
Hmm

```
hostname
Home

```

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Home

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

In samba.conf netbios is Samba24

```

[global]
	netbios name = Samba24
```

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> Hmm

```
hostname
Home

```

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Home

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

In samba.conf netbios is Samba24

```

[global]
	netbios name = Samba24
```
I assume you mean the file smb.conf NOT samba.conf.  ;-)

Right under *netbios name = Samba24* you can add the line```
name resolve order = bcast
```...then you can reboot the system.  

See if you can browse for Samba24

---

### Post by c-m on 2015-03-24
unfortunately there is no change after added that. On a fresh reboot i can't access the server by IP or name.

I don't see how this doesn't affect everyone running 14.04 and 14.10 as I haven't done anything special to the default samba conf.

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> unfortunately there is no change after added that. On a fresh reboot i can't access the server by IP or name.
It's hard to diagnose "no change after I added that".  What errors do you get?  

If you can't connect by IP address from a remote client then you have **IP networking** problems that you need to cure before Samba will work.

Can you connect to Samba from the Samba server itself?  Samba can be both a Server and a Client at the same time.

Post the output of this command from the Samba server terminal ```
smbtree -d3
```

---

### Post by c-m on 2015-03-24
There's no error as such, just that their was a problem connecting to the server smb://192.168.1.69 

I can ping the sever no problem, but unless I run "sudo service smbd restart" then neither the client nor the server itself can access any samba shares.

```
 smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d39590] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a190] mpx_fde[(nil)] fd[9] - disabling
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d395d0] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a1d0] mpx_fde[(nil)] fd[9] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d39570] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a170] mpx_fde[(nil)] fd[9] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a1c0] mpx_fde[(nil)] fd[9] - disabling
Connecting to 192.168.1.254 at port 445
HOME
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d4c920] mpx_fde[(nil)] fd[11] - disabling
Connecting to 192.168.1.254 at port 445
	\\BTHUB3         		BT Home Hub 3.0A File Server
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
name_resolve_bcast: Attempting broadcast lookup for name BTHUB3<0x20>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d4e6c0] mpx_fde[(nil)] fd[14] - disabling
Connecting to 192.168.1.254 at port 445
		\\BTHUB3\IPC$           	IPC Service (BT Home Hub 3.0A File Server)


```

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> There's no error as such, just that their was a problem connecting to the server smb://192.168.1.69 

I can ping the sever no problem, but unless I run "sudo service smbd restart" then neither the client nor the server itself can access any samba shares.

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0

```

I need ALL of the output.

---

### Post by c-m on 2015-03-24
yes sorry I I was a bit too keen and didn't notice it asked for my password. I edited the post above with all the output.

---

### Post by bab1 on 2015-03-24
> **c-m said:**
> There's no error as such, just that their was a problem connecting to the server smb://192.168.1.69 

I can ping the sever no problem, but unless I run "sudo service smbd restart" then neither the client nor the server itself can access any samba shares.

```
 smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
interpret_interface: Adding interface 127.0.0.1/8
added interface 127.0.0.1/8 ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter carl's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d39590] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a190] mpx_fde[(nil)] fd[9] - disabling
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d395d0] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a1d0] mpx_fde[(nil)] fd[9] - disabling
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d39570] mpx_fde[(nil)] fd[7] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a170] mpx_fde[(nil)] fd[9] - disabling
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d3a1c0] mpx_fde[(nil)] fd[9] - disabling
Connecting to 192.168.1.254 at port 445
HOME
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name HOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name HOME<0x1d>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d4c920] mpx_fde[(nil)] fd[11] - disabling
Connecting to 192.168.1.254 at port 445
	\\BTHUB3         		BT Home Hub 3.0A File Server
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BTHUB3<0x20>
name_resolve_bcast: Attempting broadcast lookup for name BTHUB3<0x20>
Got a positive name query response from 192.168.1.254 ( 192.168.1.254 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f6043d4e6c0] mpx_fde[(nil)] fd[14] - disabling
Connecting to 192.168.1.254 at port 445
		\\BTHUB3\IPC$           	IPC Service (BT Home Hub 3.0A File Server)


```
I wonder if we are talking about the same host.  Is it Home of Samba24?  Which ever it is, I thought we were going to add this to the smb.conf file```
netbios name = Samba24
name resolve order = bcast
```

If these were added the output above would not have this```
resolve_lmhosts: Attempting lmhosts lookup
```.

In the past I have recommended that you not alter the smb.conf file other than the two lines I have listed.  You only need those lines modified and the shares added at the bottom of the smb.conf file.  It appears the the smb.conf file has been other lines modified.  These liines should not appear anywhere in the any smb.conf file```
Processing section "[global]"
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
```

So, starting at the beginning; **list the hosts on this network** by name, IP address and Samba function (e.g home - 192.168.1.69 - samba server, samba24 - ????.????.????.???? - samba client, bthub3 - 192.168.1.254  - samba server, et al).  I'm guessing, you correct and add what is needed.

Which host did you run *smbtree* on?  On that host post the output of this command```
cat /etc/samba/smb.conf
```

It will be more productive if I know the entire topology of the network (hosts and their function).  Include the Windows hosts also.  That way we can mutually ID and work on the same host to resolve your problems.

---

### Post by c-m on 2015-03-24
Thanks for the perserverance. 

Every output I have listed so far is from my Ubuntu machine which is my samba server. 

It's hostname is Home (this name was set during the Ubuntu install process), and it is at 192.168.1.69

Here is the smb.conf

```

[global]
	netbios name = Samba24
	name resolve order = bcast
	server string = Samba file and print server
	workgroup = Workgroup
	security = user
	hosts allow = 127. 192.168.1.
	interfaces = 127.0.0.1/8 192.168.1.0/24
	bind interfaces only = yes
	remote announce = 192.168.1.255
	remote browse sync = 192.168.1.255
	printcap name = cups
;	load printers = yes
	cups options = raw
;	printing = cups
	guest account = smbguest
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 6
	password level = 6
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
;	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = wins lmhosts bcast
;	wins support = no
;	wins proxy = no
	dns proxy = no
;	preserve case = yes
;	short preserve case = yes
	client use spnego = no
	client signing = no
	client schannel = no
	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
;	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no
	update encrypted = yes
;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
	username map = /etc/samba/smbusers
;	passdb backend = tdbsam
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
;	winbind refresh tickets = no
;	winbind offline logon = no




[TV & Video]
	path = /media/carl/TV & Video
	comment = No comment
	valid users = carl
	username = carl
	writeable = yes
;	available = yes
;	browseable = yes
;	printable = no
	locking = no
	strict locking = no

[Misc]
	path = /media/carl/Misc
	writeable = yes
;	browseable = yes
	valid users = carl

[RAW]
	comment = Pictures
	path = /media/carl/RAW
	writeable = yes
;	browseable = yes
	valid users = carl
```

There is one client called Mine on IP 192.168.1.64 running OSX Yosemite

I use a BT home Hub 3.0 Router - This has it's own samba server built in and is at 192.168.1.254

---

### Post by bab1 on 2015-03-25
> **c-m said:**
> Thanks for the perserverance. 

Every output I have listed so far is from my Ubuntu machine which is my samba server. 

It's hostname is Home (this name was set during the Ubuntu install process), and it is at 192.168.1.69

Here is the smb.conf

```

[global]
	netbios name = Samba24
	name resolve order = bcast
	server string = Samba file and print server
	workgroup = Workgroup
	security = user
	hosts allow = 127. 192.168.1.
	interfaces = 127.0.0.1/8 192.168.1.0/24
	bind interfaces only = yes
	remote announce = 192.168.1.255
	remote browse sync = 192.168.1.255
	printcap name = cups
;	load printers = yes
	cups options = raw
;	printing = cups
	guest account = smbguest
	log file = /var/log/samba/samba.log
	max log size = 1000
;	null passwords = no
	username level = 6
	password level = 6
;	encrypt passwords = yes
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
;	preferred master = no
;	domain logons = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
;	time server = no
	name resolve order = wins lmhosts bcast
;	wins support = no
;	wins proxy = no
	dns proxy = no
;	preserve case = yes
;	short preserve case = yes
	client use spnego = no
	client signing = no
	client schannel = no
	server signing = no
	server schannel = no
;	nt pipe support = yes
;	nt status support = yes
	allow trusted domains = no
	obey pam restrictions = yes
	enable spoolss = yes
;	client plaintext auth = no
;	disable netbios = no
	follow symlinks = no
	update encrypted = yes
;	pam password change = no
	passwd chat timeout = 120
;	hostname lookups = no
	username map = /etc/samba/smbusers
;	passdb backend = tdbsam
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
;	winbind refresh tickets = no
;	winbind offline logon = no




[TV & Video]
	path = /media/carl/TV & Video
	comment = No comment
	valid users = carl
	username = carl
	writeable = yes
;	available = yes
;	browseable = yes
;	printable = no
	locking = no
	strict locking = no

[Misc]
	path = /media/carl/Misc
	writeable = yes
;	browseable = yes
	valid users = carl

[RAW]
	comment = Pictures
	path = /media/carl/RAW
	writeable = yes
;	browseable = yes
	valid users = carl
```

There is one client called Mine on IP 192.168.1.64 running OSX Yosemite

I use a BT home Hub 3.0 Router - This has it's own samba server built in and is at 192.168.1.254
The smb.conf file looks very different from the default smb.conf file.  The errors and warnings show that.

As I have said previously you should use the original default smb.conf file.  The only modification should be adding the lines in the [global] section```
netbios name = Samba24
name resolve order = bcast
```...in your example you have added the lines, but you have also canceled them later on in the smb.conf file.  When you use a known good smb.conf file (e.g. the default file).  We don't have to wonder what is not correct.

The only **addition **needed after this is the share definitions.

Once this is done the Samba server will be referred to as Samba24 rather than Home and the name lookups will be via *bcast* only.

I'm guessing that you have used the smb.conf file from an earlier Samba install.  Samba from Ubuntu 14.04 on is very different.  It is Samba v4.  Earlier Ubuntu distros use Samba v3.  Do have a backup of the default smb.conf file for this install?

Once you have this server figured out you can progress to the host Mine (OSX) if it still has problems.

---

### Post by c-m on 2015-03-25
I hadn't played with the smb.conf perhaps it was the gadmin-samba app I tried a while back.

I've now reverted to a basic smb.conf

```

[global]
    ; General server settings
    netbios name = Home
    server string = Home Samba Server
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = no
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes



[TV & Video]
	path = /media/carl/TV & Video
	comment = No comment
	valid users = carl
	username = carl
	writeable = yes
;	available = yes
;	browseable = yes
;	printable = no
	locking = no
	strict locking = no

[Misc]
	path = /media/carl/Misc
	writeable = yes
;	browseable = yes
	valid users = carl

[RAW]
	comment = Pictures
	path = /media/carl/RAW
	writeable = yes
;	browseable = yes
	valid users = carl
```

I can see the server and it's shares but I can't access the shares unless I first login to the server. i.e I can't leave the server at the ubuntu login screen and access the shares from my mac.

Anyway, thanks for all the help

---

### Post by bab1 on 2015-03-25
> **c-m said:**
> I hadn't played with the smb.conf perhaps it was the gadmin-samba app I tried a while back.

Perhaps????  I'd call that playing with the smb.conf file.   :-(
> 
...

Anyway, thanks for all the help
It's still not right, but if your happy....

---

### Post by c-m on 2015-03-25
Oh no. What's wrong with this one?

I got from the guide on the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I can get the original from /usr/share/samba/smb.conf and use that if it would be better

---

### Post by bab1 on 2015-03-25
> **c-m said:**
> Oh no. What's wrong with this one?

I got from the guide on the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I can get the original from /etc/samba/smb.conf and use that if it would be better
Read post ##16.  What do you think?

---

### Post by c-m on 2015-03-25
Right. This is the one from from /usr/share/samba/smb.conf so is the default one from my system.

Oddly there was no netbios name in it at all (I added it along with other line you mentioned), nor does it seem to use security = user


```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

	netbios name = Home
	name resolve order = bcast

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin



[TV & Video]
	path = /media/carl/TV & Video
	comment = No comment
	valid users = carl
	username = carl
	writeable = yes
;	available = yes
;	browseable = yes
;	printable = no
	locking = no
	strict locking = no

[Misc]
	path = /media/carl/Misc
	writeable = yes
;	browseable = yes
	valid users = carl

[RAW]
	comment = Pictures
	path = /media/carl/RAW
	writeable = yes
;	browseable = yes
	valid users = carl



```

---

### Post by bab1 on 2015-03-25
> **c-m said:**
> Right. This is the one from from /usr/share/samba/smb.conf so is the default one from my system.

Oddly there was no netbios name in it at all (I added it along with other line you mentioned), nor does it seem to use security = user



The netbios name is not defined by default, nor is the correct **name resolve order** set.  That's why I suggested that you set them.  All of the other settings will work perfectly with no alterations.  I'm not sure why you referenced the 2006 posting.  The only information that should be used regarding Samba v4 package (i.e. samba) is from 2014 and on. 


The **security = USER**  is defined by default and does not need to be explicitly set in the smb.conf file.  If you have not altered the file you can see the default setting with this command```
testparm -sv|grep security
```...it should return this```
testparm -sv|grep security
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
	**[COLOR="#FF0000"]security[/COLOR]** = USER

```

---

