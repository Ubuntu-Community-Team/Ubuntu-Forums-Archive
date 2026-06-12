---
title: "Can't Browse WIndows Network from Ubuntu 16.04"
date: 2020-07-03
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2020-07-03
I have 4 Ubuntu servers at one site. 3 of the computers can browse the Windows network and see all of the Windows computers and the Linux servers running Samba. They are running 18.04 LTS. I have one16.04 LTS  32 bit computer with pretty much the same hardware and software. That computer cannot browse the Windows network nor connect to smb/cifs shares. The other computers can see it and can connect to it's shares as can all of the Windows computers.

smbtree runs, prompts for a password but returns no results.

```
# smbtree
Enter root's password
```

nmblookup runs but returns no results.

```
# nmblookup -W ADMINISTRATION -A 192.168.1.2
Looking up status of 192.168.1.2
No reply from 192.168.1.2
```

smbclient runs but times out with an error.

```
# smbclient -W ADMINISTRATION -U administrator //shylock2/accounting
Enter administrator's password: 
Connection to shylock2 failed (Error NT_STATUS_IO_TIMEOUT)

```

These commands work on all of the other computers.

I have iptables running on this computer to do address translation for my block of public ip addresses. I also have port 137 blocked for udp and tcp on the public ip addresses, but I don't think that should effect the private addresses.

```
-A INPUT -s aa.bb.cc.dd/29 -p udp -m udp --dport 137 -j DROP
-A INPUT -s aa.bb.cc.dd/29 -p tcp -m tcp --dport 137 -j DROP
-A OUTPUT -s aa.bb.cc.dd/29 -p tcp -m tcp --dport 137 -j DROP
-A OUTPUT -s aa.bb.cc.dd/29 -p udp -m udp --dport 137 -j DROP
```

I haven't found anything in the logs to indicate a problem.

---

### Post by TheFu on 2020-07-05
Win10 changed the way network announcements work.  
Want to access a Windows Share from Linux? In short, seems that Win10 disables NetBIOS and using a manual CIFS is necessary.

Morbius1's instructions: [https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468)

---

### Post by rsteinmetz70112 on 2020-07-05
Thanks for the suggestion but Win 10 isn't involved and the suggestions in the linked thread didn't work.

I am trying to connect to an older Windows Server that runs a legacy application.

My 18.04 computers can connect just fine but this one 16.04  machine can't connect.

---

### Post by rsteinmetz70112 on 2020-07-07
OK I'm still trying to figure this one out samba appears to be in stalled and working. I can access shares from other computers including Windows and Ubuntu. 
Smbclient is still timing out
```
# smbclient -L '\\shylock2\accounting' -W administration -U administrator
Enter administrator's password:
Connection to shylock2 failed (Error NT_STATUS_IO_TIMEOUT)
```
But I am getting a sort of a prompt, but not the smb prompt.
Net Rpc does give me a share list so something is working
```
# net rpc share list -U rob
Enter rob's password:
print$
Finance
NTFS_Backup
IPC$
Hewlett-Packard-HP-LaserJet-M402dn
postscript-color-printer-(rev3)
HP-Officejet-Pro-8500-A909a
Hewlett-Packard-DesignJet-500+HPGL2-(C7770B)CMD:PCL
Savin-C9120

```
Smbstatus returns something, but not all of teh shares
```
# smbstatus --shares

Service      pid     machine       Connected at
-------------------------------------------------------
IPC$         18956   192.168.1.28  Tue Jul  7 14:35:52 2020
IPC$         18745   192.168.1.29  Tue Jul  7 14:30:46 2020

```

I'm sure it is a configuration issues I just haven't been able to figure out what is.

---

### Post by TheFu on 2020-07-07
Three things are normally requested, sometimes four, for problems like this.
[LIST]
[*]Show the config file; the /etc/samba/smb.conf is used slightly for client-side connections.
[*]Check the server log files for problems (event viewer on Windows)
[*]Run the client-side connection in verbose mode
[/LIST]
And sometimes, disabling the firewall for testing purposes is requested.
Try using IP addresses only for all connections too, not hostnames/LMhosts.

I don't have the smbclient command on my systems, but do have one which connects to a Win7 system using autofs and a CIFS mount.
Here's the autofs mount:
```
K       -fstype=cifs,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/K
```

This is from a 16.04 server system (as a CIFS client) to a Win7 desktop (CIFS server). There are 2 other mounts to that system as well. There are all sorts of *client max protocol* and *client min protocol* settings, but the manpage says those are negotiated with the server, so shouldn't be needed on any client.

Did I miss where the exact CIFS server being used was mentioned? **older Windows Server** doesn't convey the supported CIFS/smb to be used.

---

### Post by rsteinmetz70112 on 2020-07-08
> **TheFu said:**
> Three things are normally requested, sometimes four, for problems like this.

[*]Show the config file; the /etc/samba/smb.conf is used slightly for client-side connections.
```
# Global parameters
[global]
        workgroup = ORLEANS
        server string = Egroupware Server (Samba,Ubuntu)
        security = USER
        obey pam restrictions = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        log file = /var/log/samba/log.%m
        logging = syslog@0 file@4
        max log size = 1000
        name resolve order = wins lmhosts hosts bcast
        time server = Yes
        logon path = \\REMUS\profiles\%U
        logon drive = U:
        logon home = \\REMUS\%U
        domain logons = Yes
        os level = 64
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        ldap ssl = no
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        admin users = root administrator
        create mask = 0664
        directory mask = 0775
        directory mode = 0775


[netlogon]
        comment = Network Logon Service
        path = /var/lib/samba/netlogon
        browseable = No


[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[Finance]
        comment = Financial Data
        path = /files/finance
        read only = No
        guest ok = Yes


[NTFS_Backup]
        path = /ntfs-backup
        force user = arris
        force group = users
        group = users
        read only = No
        force create mode = 0664
        inherit permissions = Yes
```

> 
[*]Check the server log files for problems (event viewer on Windows)


**No error messages in any of the samba logs or syslog.**


> [*]Run the client-side connection in verbose mode

**I haven't tried that one.**

> 
And sometimes, disabling the firewall for testing purposes is requested.

**Tried disabling ufw - no luck in my previous post I listed part of my iptables configuration which should not apply to these connection since it only should apply to my public ip addresses.**

> Try using IP addresses only for all connections too, not hostnames/LMhosts.

**Tried with host names and IP address got the same behavior.**

> I don't have the smbclient command on my systems, but do have one which connects to a Win7 system using autofs and a CIFS mount.
Here's the autofs mount:
```
K       -fstype=cifs,sec=ntlmv2,iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/K
```

**Tried using a cifs mount on the command line and it fails. I never tried using all of the options you listed above. It does work as expected on 3 other 18.04 machines. **

> This is from a 16.04 server system (as a CIFS client) to a Win7 desktop (CIFS server). There are 2 other mounts to that system as well. There are all sorts of *client max protocol* and *client min protocol* settings, but the manpage says those are negotiated with the server, so shouldn't be needed on any client.
Did I miss where the exact CIFS server being used was mentioned? **older Windows Server** doesn't convey the supported CIFS/smb to be used.

The Windows server is a Windows 2003 SBS. I can connect to it using the 18.04 computers. I also have Windows 7 and 10 workstations but I don't need to connect to them. However in the Ubuntu desktop Windows Network does not show any of them even though the 18.04 computers can browse them. I believe this is all the same problem. I'm just having trouble determine what its is.

---

### Post by rsteinmetz70112 on 2020-07-16
OK I'm back trying to figure this out 

The clinet is Ubuntu 16.04 LTS running

```
$ smbclient -V
Version 4.3.11-Ubuntu
```

The servver is Ubuntu 18.04 running smbd
 
```
# smbd -V
Version 4.7.6-Ubuntu
```

I'm not sure how the protocol negotiation would or whether each version supports the same version. I can set the minimum and maximum version in the smb.conf file, one teh server, but I haven't. I can set the max protocol for smbclient , but not the minimum version as far as I can tell.

I upped the debug lever and this is what I got
```
$ smbclient -L romulus -U rob -d 5
INFO: Current debug levels:
  all: 5
  tdb: 5
  printdrivers: 5
  lanman: 5
  smb: 5
  rpc_parse: 5
  rpc_srv: 5
  rpc_cli: 5
  passdb: 5
  sam: 5
  auth: 5
  winbind: 5
  vfs: 5
  idmap: 5
  quota: 5
  acls: 5
  locking: 5
  msdfs: 5
  dmapi: 5
  registry: 5
  scavenger: 5
  dns: 5
  ldb: 5
  tevent: 5
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
INFO: Current debug levels:
  all: 5
  tdb: 5
  printdrivers: 5
  lanman: 5
  smb: 5
  rpc_parse: 5
  rpc_srv: 5
  rpc_cli: 5
  passdb: 5
  sam: 5
  auth: 5
  winbind: 5
  vfs: 5
  idmap: 5
  quota: 5
  acls: 5
  locking: 5
  msdfs: 5
  dmapi: 5
  registry: 5
  scavenger: 5
  dns: 5
  ldb: 5
  tevent: 5
Processing section "[global]"
doing parameter workgroup = ORLEANS
doing parameter netbios name = hamlet
doing parameter server string = Egroupware Server (Samba,Ubuntu)
doing parameter security = user
doing parameter obey pam restrictions = Yes
doing parameter passdb backend = tdbsam
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
doing parameter logging = syslog@0 file@4
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter name resolve order = wins lmhosts hosts bcast
doing parameter time server = Yes
doing parameter logon path = \\REMUS\profiles\%U
doing parameter logon home = \\REMUS\%U
doing parameter logon drive = U:
doing parameter domain logons = Yes
doing parameter os level = 64
doing parameter preferred master = Yes
doing parameter domain master = Yes
doing parameter dns proxy = No
doing parameter wins support = Yes
doing parameter ldap ssl = no
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter admin users = root, administrator
doing parameter create mask = 0664
doing parameter directory mask = 0775
pm_process() returned Yes
added interface enp1s0 ip=192.168.1.1 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="HAMLET"
Client started (version 4.3.11-Ubuntu).
Enter rob's password:
Opening cache file at /var/cache/samba/gencache.tdb
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/cache/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
sitename_fetch: No stored sitename for
no entry for romulus#20 found.
wins_srv_is_dead: 127.0.0.1 is alive
resolve_wins: using WINS server 127.0.0.1 and tag '*'
nmb packet from 127.0.0.1(35072) header: id=8985 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=ROMULUS<20> rr_type=32 rr_class=1 ttl=258694
    answers   0 char `.....   hex 6000C0A8011C
Got a positive name query response from 127.0.0.1 ( 192.168.1.28 )
namecache_store: storing 1 address for romulus#20: 192.168.1.28
Connecting to 192.168.1.28 at port 445
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 0
        SO_BROADCAST = 0
        TCP_NODELAY = 1
        TCP_KEEPCNT = 9
        TCP_KEEPIDLE = 7200
        TCP_KEEPINTVL = 75
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_REUSEPORT = 0
        SO_SNDBUF = 44800
        SO_RCVBUF = 341760
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
        TCP_QUICKACK = 1
        TCP_DEFER_ACCEPT = 0
 session request ok
protocol negotiation failed: NT_STATUS_INVALID_NETWORK_RESPONSE
```

---

### Post by TheFu on 2020-07-16
```
protocol negotiation failed: NT_STATUS_INVALID_NETWORK_RESPONSE
```

Try adding this option on the smbclient command:     -m SMB3_10
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=883939](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=883939)

I don't know what the SMB version for 2003 is - may need to specify that - it is 17 yrs ago. Perhaps time to upgrade?

We are well beyond my skills - I've never used Windows Servers.

---

### Post by rsteinmetz70112 on 2020-07-17
I think I've found part or maybe all of the problem. 
I've decided to leave the Windows server till later, but I can connect using smbclient from other Linux computers so IF I can get this working it should work as well.

The Linux Server I'm trying to connect from is also running iptables to do NAT translation for our public ip addresses to allow external connection to certain services on our servers. That all works peachy. 

I discovered yesterday that when connecting via smbclient the "router" uses its public ip address which was rejected by my Linux server. I'm not sure what is actually happening, but when I added the public ips as "hosts allow" in smb.conf smbclient worked. Other stuff, like the gnome Windows Network is still broken. I figure if I can get the address translation working as it needs to it everything will work.

Now I just need to figure our how to set up iptables (or something else) to not do translation on the ports necessary for samba, but not block or drop traffic to and from them. BTW I am using iptables because that was what was available when I started this. I looked as the newer stuff but found I needed to reenter the iptables rules because there was no straightforward way to do address translation, probably on purpose.

These are the ports I apparently need :

```
netbios-ns	        137/tcp				# NETBIOS Name Service
netbios-ns	        137/udp
netbios-dgm	138/tcp				# NETBIOS Datagram Service
netbios-dgm	138/udp
netbios-ssn	139/tcp				# NETBIOS session service
netbios-ssn	139/udp

Port 389 (TCP) – for LDAP (Active Directory Mode)
Port 445 (TCP) – NetBIOS was moved to 445 after 2000 and beyond, (CIFS)
```

With IP tables I am forwarding all traffic to the public ipaddress. There are a pair of statements like the ones below for each available IP address.

```
-A PREROUTING -d X.X.X.X./32 -j DNAT --to-destination 192.168.1.1
-A POSTROUTING -s 192.168.1.1/32 -j SNAT --to-source X.X.X.X
```


In iptables I currently have these ports blocked:

```
-A INPUT -p tcp -m tcp --dport 1434 -j DROP
-A INPUT -p udp -m udp --dport 1434 -j DROP
-A INPUT -p udp -m udp --dport 389 -j DROP
-A INPUT -p tcp -m tcp --dport 389 -j DROP
-A INPUT -s X.X.X./29 -p udp -m udp --dport 137 -j DROP
-A INPUT -s X.X.X.X/29 -p tcp -m tcp --dport 137 -j DROP
-A OUTPUT -p udp -m udp --dport 389 -j DROP
-A OUTPUT -p tcp -m tcp --dport 389 -j DROP
-A OUTPUT -p tcp -m tcp --dport 1434 -j DROP
-A OUTPUT -p udp -m udp --dport 1434 -j DROP
-A OUTPUT -s X.X.X.X/29 -p tcp -m tcp --dport 137 -j DROP
-A OUTPUT -s X.X.X.X/29 -p udp -m udp --dport 137 -j DROP
```

As I understand it this would drop all traffic to and from 137 for the public ip address range, what I need it for that not to be routed to the public address at all and simply handled using the private IP address. 

I think I can do that by port forwarding only the ports actually needed by the server, except I'm not entirely sure what they all are, I know I need to not forward the above ports and I need to forward http, https ssh and some others. At some point I will need LDAP available locally but changing that to apply to only the public addresses would be simple, see the port 137 as an example.

---

### Post by TheFu on 2020-07-17
I'd limit all samba traffic to only the LAN interface.
No way would I open CIFS on a public internet IP NIC.  No FREAKIN' WAY!   That's just asking for hackers.

I use a router distribution, OPNSense, for my public router.  Some things are just too important for me to screw up.

---

### Post by rsteinmetz70112 on 2020-07-20
That is the intention. 

I was unaware that the CIFS on the local interfaces was being intercepted by iptables. I can block the ports with iptables but I need to leave them open locally. That's the issue now.

I'm just not sure how to get that accomplished.

---

### Post by TheFu on 2020-07-20
"locally" is ambiguous.  Please clarify and be as accurate as possible. Details matter.

OTOH, I block all CIFS traffic at the router, so even if I screw up, it isn't getting outside.  The CIFS ports are the most scanned by crackers in a recent article I saw a few days ago.  ssh on 22/tcp was the next most common, then FTP, HTTP/HTTPS and SMTP.  Then all the other 64K random ports.

---

### Post by rsteinmetz70112 on 2020-07-21
By locally I mean the local network on private addresses 192.168.1.xxx

The cifs ports are blocked at the firewall for the private ip addresses but I recently discovered that iptables address translation is sending some cifs/samba traffic to the public address. I can access the samba shares via the private address just fine but I can't mount a cifs share or use a lot of the command line tools with iptables active. I can work around some of it by allowing the servers to access the public addresses, they are normally restricted to the private address range.

The router I'm using is an ATT provided Fiber gateway ARRIS Model BGW210-700 with limited ability to handle the public addresses in fact after the fiber was installed I discovered those pieces of the gateway didn't work at all and I had to update the software in it to get anything to work. Something ATT couldn't tell me for weeks and eventually I found a user site with information about the update. That how I ended up with iptables doing the address translation.

---

### Post by TheFu on 2020-07-21
In the smb.conf
```
hosts allow = 127.0.0.1 172.22.22.0/24 172.21.22.27
hosts deny = 0.0.0.0/0
```

I expected to find **interfaces =** setting, but didn't see it in mine
```

       bind interfaces only (G)

           This global parameter allows the Samba admin to limit what
           interfaces on a machine will serve SMB requests. It affects file
           service smbd(8) and name service nmbd(8) in a slightly different
           ways.
...
       interfaces (G)

           This option allows you to override the default network interfaces
           list that Samba will use for browsing, name registration and other
           NetBIOS over TCP/IP (NBT) traffic. By default Samba will query the
           kernel for the list of all active interfaces and use any interfaces
           except 127.0.0.1 that are broadcast capable.
       Example: interfaces = eth0 192.168.2.10/24 192.168.3.10/255.255.255.0

```
manpages are pretty great.

Members of my LUG have mentioned AT&T connection stuff.  A few of them have created workarounds to get passed some limitations  that negatively impact performance and  connection stability.  I may be switching for the vastly higher throughput and lower price, but need to move some gateway stuff onto cloudy providers first.

---

### Post by rsteinmetz70112 on 2020-07-24
My understanding of```
 hosts allow = 192.168.1.0/24 
```is to allow only those addresses listed and not any others, so hosts deny is redundant and is generally used when you want to deny specific hosts but I could be wrong. I have seen examples using the deny all address.

Since my problem seems to revolve around the IP tables settings, I'm not sure how to circumvent them I think I'll try setting ```
 interfaces = enp1s0 192.168.1.0/24 
```and  limiting it to local addresses, I'm not sure how that will interact with iptables nat settings.

I tried the things above but it appears that iptables is still translating the address 

With regard to the ATT connections on my gateway you can set a "cascaded router" to handle the Public Addresses and have the gateway send all of that traffic to the router. I didn't have one but the cheap one I bought didn't really do what I needed and I didn't want to take time to figure out one that could accomplish what I needed.

---

### Post by TheFu on 2020-07-24
Dumb question, is 
```
sudo apt install cifs-utils
```
installed?

---

### Post by rsteinmetz70112 on 2020-07-27
Yep it is.

---

### Post by TheFu on 2020-07-27
> **rsteinmetz70112 said:**
> Yep it is.

I asked because a newly installed system here was having issues accessing a Windows share and it turned out I hadn't installed that package. Afterwards, all my mounts just worked.  Would have been nice if the errors in syslog mentioned the missing package instead of just saying permission denied. ;(

---

### Post by rsteinmetz70112 on 2020-07-27
```
# apt install cifs-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
cifs-utils is already the newest version (2:6.4-1ubuntu1.1).
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
```

---

