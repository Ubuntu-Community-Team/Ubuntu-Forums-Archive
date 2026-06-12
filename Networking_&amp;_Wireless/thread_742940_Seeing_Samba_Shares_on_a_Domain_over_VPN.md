---
title: "Seeing Samba Shares on a Domain over VPN?"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by bthoward on 2008-04-02
Ok I'll admit it I'm using Hardy Heron but I don't think my problems are related to Hardy at all in this instance so I'm posting it here....

Currently I'm on a 192.168.1.x network (my own at home)
I'm connected to this via WiFi and I have a VPN connection using vpnc and a nm-applet connection nugget to get connected to the VPN.

Here is a dump of my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr OBFUSCATE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr OBFUSCATE  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe75:5bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1019166 errors:754 dropped:754 overruns:0 frame:0
          TX packets:968123 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:58084293 (55.3 MB)  TX bytes:804852826 (767.5 MB)
          Interrupt:18 Base address:0xa000 Memory:dfbff000-dfbfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.1.9.51  P-t-P:10.1.9.51  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:151237 (147.6 KB)  TX bytes:54399 (53.1 KB)
```

I am running shorewall on this machine but have a policy that trusts all connections going both directions between me and the vpn interface.  

When putting "smb://<server name>" into Nautilus I get nothing returned.  If I type "smb://myth" (the mythbuntu box on my home network all of the shares setup for my wife to have access show up just fine).  Here is a return of smbclient run with no user information:

```
brett@lappy:~$ smbclient -L <server name> | head -n 20
Password: 
Domain=[<mydomain>] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine <server name>.  Error was NT_STATUS_ACCESS_DENIED
Domain=[<mydomain>] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful

```

Now if I add user information:
```
brett@lappy:~$ smbclient -L eugsrv300 -U<domain username> -W<mydomain> | head -n 20
Password: 
Domain=[<mydomain>] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]
Domain=[<mydomain>] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]

	Sharename       Type      Comment
	---------       ----      -------
	Presentations   Disk      
	C$              Disk      Default share
	ABS             Disk      
	Metadata        Disk      
	F$              Disk      Default share
	IPC$            IPC       Remote IPC
	APPSHARES       Disk      Application Shares
	Transfer        Disk      
	MeetingCompliance Disk      
	ADMIN$          Disk      Remote Admin
	GRPFILES        Disk      GRPFILES (AD)
	E$              Disk      Default share

```

What do I need to do in order to be able to browse these shares in a gui fashion.  Granted I can now use mount -t smbfs to get at these files but its not very handy when there are many servers with many shares that I have random different access needs to and I'm not always connected to VPN so permanently mounting them isn't a very good option.  I'd really like to be able to just browse to them like I would be able to if I were in Windoze... 

Oh and I did try putting "smb://<domain user>:<domain pass>@<server name>" and the same w/o the pass and the : to no avail.  Figured it was worth a try... :)  Any help is greatly appreciated!  

Thanks gentlemen.

---

### Post by andguent on 2008-04-09
I just found your post, hopefully you already figured out the answer.

What I would suggest testing is smb://<server IP address> and see how that goes. You may have to give the VPN IP address of the server.

If that works, I might recommend putting into your /etc/hosts file, a unique network name for your server you would only use when connecting over the VPN.

EX:
When at home, browsing works fine because names reolve correctly:
homeserver resolves to 192.168.1.10 (or whatever)

When on the VPN, name resolving might not always work the way you want. Manually adding something like this to your hosts file may help:
10.1.9.50 homeserver-vpn

From then on, the name homeserver works from home, and the name homeserver-vpn works over the vpn.

Another thought to be aware of: when specifiying your username when connecting to a domain, try putting your username as domain\username, EX:
WidgetsRUs\bthoward

Just an idea, hopefully you got it straitened out by now.

---

### Post by bthoward on 2008-04-09
The problem isn't that I'm not finding the server.  The problem is that its using my userinfo from the box and not my VPN user info and I'm not able to see shares cause I'm not privliged when using the gui tools (nautilus).  What I need is either a way to use the GUI tools to enter what user/pass combo I wanna use or I need it to automatically use my VPN credentials to view shares on the other side of the VPN.

Being that my box can ping and resolv the server name just fine smb://<server name> presents identical results as smb://<server ip>

---

### Post by andguent on 2008-04-10
Have you already tried Places -> Connect to server -> Windows Share? 

Do note that most of that menu is optional, but it should let you set your username on a per server basis and give you a shortcut in places to use from then on.

---

### Post by bthoward on 2008-04-10
I'd missed that... that seems to work kinda flakey (but one would expect that in Hardy) but I did finally get that to mount the share and allow me in there... 

Thanks!

---

### Post by Wharf Rat on 2008-06-01
I am working on the same thing.

My work server listens for a VPN.

So, I can use Places -->Connect to Server - [WWW.MYOFFICE.COM](WWW.MYOFFICE.COM)  and find it.

Using Windows Share Option
I use:
Server - [www.myoffice.com](www.myoffice.com)
User Name - my login id
Domain Name - the office Windows domain.
This will automatically show my personal network folder.

In order to access a different folder on our network such as "Public" or "Management"

Add that folder name in the "Folder" box.


Now, to figure out how to keep the settings so I don't have to re-enter the same stuff.  Perhaps even an icon so I can click and have the system mount the remote folder. ??

PS
It makes things real sluggish.
Also, I get two mount points on my desktop for each remote folder mounted.  ???

---

### Post by andguent on 2008-06-01
pyneighborhood is available in synaptic, and lets you browse a server and double click shares to mount them. Make sure you look around in the preferences box, as there is a "connect as user:" field that is important in a secured environment. pyneighborhood appears to be the upgrade/rewrite to LinNeighborhood.

A second option is available for those comfortable on the command line and in /etc/fstab. Try adding a line like this to the end:
```
//<server ip>/<server share> /home/<local username>/mountedshare cifs noauto,user=<server username>,password=<server password>,uid=<local uid number>,users 0 0
```

Replace the <...>'s as needed:
* <server ip> = IP address of remote server that has the share (name probably works too, but IP can be more reliable).
* <server share> = Name of Samba/Windows file share on the server
* <local username> = Your username on your workstation
* <server username> = Your username on the server at work. Note, this can be domain\username too.
* <server password> = Your password at work (Note, this makes your work password available to anyone who can get root on this workstation, see cifs/fstab man page for options to hide it.)
* <local uid> = The user id number on your workstation. In a terminal as yourself, try running "echo $UID" to figure this out.

From there, it intentionally will NOT auto connect. My experimentation found that the best way to get it to auto connect was to run the command "mount -a" once logged in. You can do this via a custom launcher, or by adding an entry to System -> Preferences -> Sessions -> Startup Programs.

---

