---
title: "Gigolo connects to same machine"
date: 2014-06-10
forum: Networking &amp; Wireless
---

### Post by winecurmudgeon2 on 2014-06-10
This is the damndnest thing. I'm running Gigolo 0.4.2 on Xubuntu 14.04 on desktop and laptop, and it works except for one thing. When I run it on my laptop, it connects to the laptop and when I run it on my desktop, it connects to the desktop. My LAN is working -- Dropbox and the printer are fine. I have all the necessary packages, openssh and gvfs, installed. I have used the correct IP addresses (and even reversed them) and used each computer's name, and they still connect to themselves.

Any thoughts?

---

### Post by bab1 on 2014-06-11
> **winecurmudgeon2 said:**
> This is the damndnest thing. I'm running Gigolo 0.4.2 on Xubuntu 14.04 on desktop and laptop, and it works except for one thing. 

When I run it on my laptop, it connects to the laptop and when I run it on my desktop, it connects to the desktop. 
> 
Gigolo should list all the available workgroups and the shares.  Initially the display might be of the local hosts shares, but if you click on the refresh icon it should show all


...  I have all the necessary packages, openssh and gvfs, installed. 

Openssh is not relevant to the issue.  The gvfs libs are installed with Gigolo if believe.
> 
I have used the correct IP addresses (and even reversed them) and used each computer's name, and they still connect to themselves.
Any thoughts?
What do you mean "reversed them"?  I think this is just a Gigolo display issue.  Try clicking on the refresh icon.  Are you sure both Samba servers up when you are using Gigolo?

---

### Post by winecurmudgeon2 on 2014-06-11
We're getting closer. I wasn't getting anything when I clicked the  refresh icon on Gigolo, but now it shows something -- see screen shot. Apparently,  I needed to install another samba package, which I did. The Asus is my laptop. But Gigolo doesn't show the desktop, which is connected to the router by ethernet (assuming it is supposed to show it).

And I'm still connecting to the same machine when I use Gigolo. Even though I can see the laptop from the desktop, when I right click on the laptop in the network box, the laptop is greyed out and I can't use connect.

Reverse means I tried all IP addresses on both machines.

---

### Post by bab1 on 2014-06-11
> **winecurmudgeon2 said:**
> We're getting closer. I wasn't getting anything when I clicked the  refresh icon on Gigolo, but now it shows something -- see screen shot. 

Apparently,  I needed to install another samba package, which I did. 

What package is that?  Generalizations don't really help in diagnosing problems.
> 
The Asus is my laptop. But Gigolo doesn't show the desktop, which is connected to the router by ethernet (assuming it is supposed to show it).

And I'm still connecting to the same machine when I use Gigolo. Even though I can see the laptop from the desktop, when I right click on the laptop in the network box, the laptop is greyed out and I can't use connect.

Reverse means I tried all IP addresses on both machines.
Your problem seems to be with Samba itself broadcasting the names of the Samba servers.  This is not a Gigolo problem per se.

The quickest way to diagnose this is to use the CLI tools provided by Samba.  I assume that both the desktop and the laptop are Ubuntu hosts.  From the laptop terminal (ctrl+t) post the output of this command```
smbtree
```

---

### Post by winecurmudgeon2 on 2014-06-11
I installed a package called samba, actually.

This is the result of smbtree:
jeff@Asus-UX31A:~$ smbtree
Enter jeff's password: 
WORKGROUP
    \\ASUS-UX31A             Asus-UX31A server (Samba, Ubuntu)
        \\ASUS-UX31A\print$             Printer Drivers
        \\ASUS-UX31A\IPC$               IPC Service (Asus-UX31A server (Samba, Ubuntu))

So it doesn't show the desktop.

---

### Post by bab1 on 2014-06-11
> **winecurmudgeon2 said:**
> I installed a package called samba, actually.

This is the result of smbtree:
jeff@Asus-UX31A:~$ smbtree
Enter jeff's password: 
WORKGROUP
    \\ASUS-UX31A             Asus-UX31A server (Samba, Ubuntu)
        \\ASUS-UX31A\print$             Printer Drivers
        \\ASUS-UX31A\IPC$               IPC Service (Asus-UX31A server (Samba, Ubuntu))

So it doesn't show the desktop.

Now we add some debug.  This will be rather large so scroll back to get the first part.  Post the output of this command```
smbtree -d3
```

Please post this between [code] blocks by clicking on the [SIZE=4]# [/SIZE]icon at the top of the reply editor.

---

### Post by winecurmudgeon2 on 2014-06-11
There you go.

```
 
 
jeff@Asus-UX31A:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=192.168.15.234 bcast=192.168.15.255 netmask=255.255.255.0
Enter jeff's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.15.234 ( 192.168.15.234 )
Connecting to 192.168.15.234 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.15.234 ( 192.168.15.234 )
Connecting to 192.168.15.234 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

 \\EMPIRE-HQ      		empire-hq server (Samba, Ubuntu)

 resolve_lmhosts: Attempting lmhosts lookup for name EMPIRE-HQ<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name EMPIRE-HQ<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name EMPIRE-HQ<0x20>
Connecting to 192.168.15.146 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
 \\EMPIRE-HQ\Canon-MX920-series	Canon MX920 series
\\EMPIRE-HQ\print$         	Printer Drivers
\\EMPIRE-HQ\IPC$           	IPC Service (empire-hq server (Samba, Ubuntu))

  \\ASUS-UX31A     		Asus-UX31A server (Samba, Ubuntu)

 resolve_lmhosts: Attempting lmhosts lookup for name ASUS-UX31A<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ASUS-UX31A<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ASUS-UX31A<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
 \\ASUS-UX31A\print$         	Printer Drivers
\\ASUS-UX31A\IPC$           	IPC Service (Asus-UX31A server (Samba, Ubuntu))

 
```

---

### Post by bab1 on 2014-06-11
> **winecurmudgeon2 said:**
> ```
resolve_hosts: Attempting host lookup for name ASUS-UX31A<0x20>
jeff@Asus-UX31A:~$ smbtree -d3...
[COLOR="#FF0000"]**Connecting to 127.0.1.1 at port 445**[/COLOR]
```
[CODE] 

The above in red won't work across the network.  127.0.1.1 is an address for the virtual interface (loopback).  It is only available to the local machine.  

Most likely the /etc/hosts file needs some help on both machines.  This is why you can't see the "non-local" machine no matter which machine you are on.

There are 2 ways to cure this.  First we need to whether you are getting your IP address via DHCP from a pool of addresses or via a fixed IP address.  If it is a fixed IP address then we can modify the /etc/hosts file on each machine.  If it is an IP address from the DHCP pool of addresses then we can set the NETBIOS name and bypass the /etc/hosts file altogether.  In fact using the NETBIOS name method can be used in any Samba server configuration.

The hosts method means you need to have a fixed address to begin with and hosts (DNS resolution) is setup correctly in the LAN.  Then Samba would have just worked!  If you have a random IP address assigned then host (DNS resolution) won't work at all anyway, so we configure the NETBIOS name manually to achieve networking connectivity for Samba (Windows Sharing) only.

Let me know how your IP addressing is configured and I will help you set up the name services resolution.

---

### Post by winecurmudgeon2 on 2014-06-12
Thanks so much for all your help, BAB1. As noted, what's really confusing is that the LAN works for everything else.

However, you'll have to talk me through how to send you the DHCP information. Where do I find it?

---

