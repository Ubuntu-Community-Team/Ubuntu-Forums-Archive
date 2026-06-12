---
title: "SmbClient needs guest password?"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by ewanchic on 2008-02-25
I am trying to connect to my samba server machine using either smbclient or mount -t smbfs. This is for guest access. If I connect to the Samba server from Windows, I can get in browse, copy, move, & delete files. No Problems. However, when connecting from a command line (Ubuntu) with no password I get either:

> 
smbclient //samba-server/

Password:
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME


or

> mount -t smbfs //samba-server/ /media/backups
or
> mount -t smbfs //samba-server/Backup.Zimbra /media/backups

Produces the same result:
> 
Password:
Anonymous login successful
21385: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed


---

### Post by swerdna on 2008-02-26
Depending on the age of your version of ?buntu, you might have to use cifs instead of smbfs

---

### Post by ewanchic on 2008-02-26
I am using Ubuntu 7.10 - server, for both the samba server and the connecting client.

> 
mount -t cifs //samba-server/Backup.Zimbra /media/backups

Password:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


Still works from a windows machine. Is there a particular password I should be using? Or a particular usrname?

This is my my samba script:
> 
[global]
  netbios name = samba-server
  server string = Samba %v on (%L)
  workgroup = Servers

  os level = 34
  local master = yes
  security = share

[RequestTracker.HTML]
  path = /usr/share/request-tracker3.6/html
  browseable = yes
  guest ok = yes
  writable = yes
  force user = root
  force group = root

[Backup.Zimbra]
  path = /media/sdc1/backups/zimbra
  browseable = yes
  guest ok = yes
  writable = yes
  force user = nobody
  force group = nogroup



BTW, force user can be "root" or "nobody", doesn't matter I still get the same results.

---

### Post by ewanchic on 2008-02-26
Here are some revelations. I was able to connect after using an IP address verses a hostname:

> 
mount -t smbfs //10.0.0.101/Backup.Zimbra /media/backups


This worked, regardless if I used smbfs or cifs. But again, I was a accessing the samba-server from a windows client using //samba-server/...whatever

To note, the ubuntu-client is running zimbra, and zimbra has it's own ldap server installed. Could this be messing it up? Would I need to identify samba-server with LDAP somehow?

---

### Post by Eiríkr on 2008-02-26
> ...the ubuntu-client is running zimbra, and zimbra has it's own ldap server installed. Could this be messing it up? Would I need to identify samba-server with LDAP somehow?
I doubt it, I think it's part of how Unixy clients talk to the SMB server -- I have to use the IP instead of the NetBIOS names when connecting from either Linux or Mac OSX clients, but when connecting from Windows clients, the NetBIOS names work just fine.  (Actually, I just set up local DNS recently, so using the DNS hostnames [which by default are identical to the NetBIOS names, unless otherwise specified] might work now).  From the [man page for smb.conf]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), in particular the [font=courier]name resolve order[/font] option details (emphasis mine):
> **name resolve order (G)**

This option is used by the programs in the Samba suite to determine what naming services to use and in what order to resolve host names to IP addresses. Its main purpose to is to control how netbios name resolution is performed. The option takes a space separated string of name resolution options.
The options are: "lmhosts", "host", "wins" and "bcast". They cause names to be resolved as follows:
[list][*][font=courier]lmhosts[/font]: Lookup an IP address in the Samba lmhosts file. If the line in lmhosts has no name type attached to the NetBIOS name (see the manpage for lmhosts for details) then any name type matches for lookup. 
[*][font=courier]host[/font]: Do a standard host name to IP address resolution, **using the system [font=courier]/etc/hosts[/font], NIS, or DNS lookups**. This method of name resolution is operating system depended for instance on IRIX or Solaris this may be controlled by the [font=courier]/etc/nsswitch.conf[/font] file. **Note that this method is used only if the NetBIOS name type being queried is the 0x20 (server) name type or 0x1c (domain controllers)**. The latter case is only useful for active directory domains and results in a DNS query for the SRV RR entry matching _ldap._tcp.domain. 
[*][font=courier]wins[/font]: Query a name with the IP address listed in the WINSSERVER parameter. **If no WINS server has been specified this method will be ignored.**
[*][font=courier]bcast[/font]: Do a broadcast on each of the known local interfaces listed in the interfaces parameter. This is the least reliable of the name resolution methods as it depends on the target host being on a locally connected subnet.[/list]
The example below will cause the local lmhosts file to be examined first, followed by a broadcast attempt, followed by a normal system hostname lookup.

When Samba is functioning in ADS security mode ([font=courier]security = ads[/font]) it is advised to use following settings for name resolve order:

[font=courier]name resolve order = wins bcast[/font]

DC lookups will still be done via DNS, but fallbacks to netbios names will not inundate your DNS servers with needless querys for DOMAIN<0x1c> lookups.

**Default: [font=courier]name resolve order = lmhosts host wins bcast[/font]**

Example: [font=courier]name resolve order = lmhosts bcast host[/font]

So the way I read this, you might need to have a properly configured lmhosts file, hosts file, DNS server, or WINS server or name lookup won't work properly.  Given the different behaviour I see between Unixy and Windows clients, I'd guess that Unixy clients are more apt to go for the hosts file or DNS entries.  Whatever the case, try entering all relevant hostnames and IPs into the /etc/hosts files for your clients and servers (or make sure your DNS server is properly configured), and see if that helps.  

Cheers,

Eiríkr

---

