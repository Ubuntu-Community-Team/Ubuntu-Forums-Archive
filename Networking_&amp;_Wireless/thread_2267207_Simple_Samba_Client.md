---
title: "Simple Samba Client?"
date: 2015-02-28
forum: Networking &amp; Wireless
---

### Post by pbpersson on 2015-02-28
My apologies if this has been asked before.  I am certain that is has, but I cannot find it.

I just installed 14.04 and I want to be able to **easily** link to my Windows shares on the network.  Is there is easy to use GUI interface for this?

I tried SMB4K which I used to use years ago but it does not seem to be working.  Most applications I try just give me errors.

If I am on a Windows machine it "just works".  I can see the machines on the network and the shares in a graphical window and can use all the shares and map to them if desired.

Isn't there anything in Ubuntu that "just works" in the same fashion?

Yes, I have seen articles where I can drill down into directories and manually add shares into text files but isn't there a GUI solution for this?  I even configured the network server with a static IP address to meet Ubuntu halfway.  :-)

---

### Post by Bucky Ball on 2015-02-28
My guess is you install Samba and system-config-samba, perhaps restart, then, open Nautilus>Network folder>Windows Network. I'm not using Nautilus, but in pcmanfm it is Go>Network. If your Windows Samba shares are there, everything should be good. If not, you'll need to configure Samba.  I think there's a network bookmark in the left pane already in Nautilus.

The GUI for configuring should be in your menus somewhere if you need it. Hope that helps. ;)

---

### Post by bab1 on 2015-02-28
> **pbpersson said:**
> My apologies if this has been asked before.  I am certain that is has, but I cannot find it.

I just installed 14.04 and I want to be able to **easily** link to my Windows shares on the network.  Is there is easy to use GUI interface for this?

I tried SMB4K which I used to use years ago but it does not seem to be working.  Most applications I try just give me errors.

If I am on a Windows machine it "just works".  I can see the machines on the network and the shares in a graphical window and can use all the shares and map to them if desired.

Isn't there anything in Ubuntu that "just works" in the same fashion?

Yes, I have seen articles where I can drill down into directories and manually add shares into text files but isn't there a GUI solution for this?  I even configured the network server with a static IP address to meet Ubuntu halfway.  :-)
It is not at all clear what you are going to use Samba for.  If you are only using the Ubuntu host as a Samba client ( all the shares are elsewhere) then you ned to do nothing extra.  The Samba client software is installed by default on the current Ubuntu distro.

If on the other hand you are going to be serving shares for the rest of the network in a directory outside of your /home directory, you need to install the Samba package (which is the server portion).  Be aware that the current version of Samba has 3 daemons (*samba, smbd and nmbd*).  For a workgroup situation you need only configure *smbd* daemon via the smb.conf file.  The simplest thing is to add only the shares you need at the bottom of the file and restart the *smbd* daemon.  Editing the smb.conf file directly is the easiest method.  The whole thing takes less than 5 minutes after you prepare the directory that you want to share (chown, chmod, etc.).

If you want to share your own directories (those in your own /home/username) you can easily do that by right clicking on the directory >>  select properties >>  select the "Local Network Share" tab and follow the instructions.

---

### Post by pbpersson on 2015-03-01
All of my data is on a Windows machine on the network.

I am using an Ubuntu desktop machine, version 14.04.  I want to read and write my data on the Windows network.

This never reliably works for me.  I was hoping that version 14.04 would be better.  

When I go into Nautilus and click on "browse network" it says:
     Unhandled error message: Timeout was reached

When I click on "Connect to Server" and put in the address such as smb://192.168.0.100 it says:
     Unhandled error message: Failed to retrieve share list from server: Connection timed out

The message appears in half a second, there is no wait so it does not appear to even be trying

If I go into Konqueror and click on "Network Folders" it actually shows me all the shares on the Windows network.

Progress!! :-D

Then if I click on the share I want I get the timeout error.  :-(

It shows me a page of exact information.  It has the IP address of the Windows machine, the name of the share....

It says the timeout value is 20 seconds but I get the error page in a half second.  This seems very strange.

I have upgraded my main desktop to 14.04 so now I have two machines in two different rooms of the house where I can work on this issue. :-)

[B]Possible Causes:
There may have been a problem at some point along the network path between the server and this computer.
The server was too busy responding to other requests to respond.[/B]

No, it is not either one of these as the Windows machines can always connect :-)

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> All of my data is on a Windows machine on the network.

I am using an Ubuntu desktop machine, version 14.04.  I want to read and write my data on the Windows network.

In IT speak you are using The Ubuntu desktop machine as a Samba client.  You don't need anything more than the default install as the Samba client software is installed by default.
> 
This never reliably works for me.  I was hoping that version 14.04 would be better.

The client software is the same.  The problem is most likely in the NetBIOS networking services.
>   

When I go into Nautilus and click on "browse network" it says:
     Unhandled error message: Timeout was reached

When I click on "Connect to Server" and put in the address such as smb://192.168.0.100 it says:
     Unhandled error message: Failed to retrieve [the] share list from server: Connection timed out

The message appears in half a second, there is no wait so it does not appear to even be trying

More confirmation that the networking services need attention.
> 

If I go into Konqueror and click on "Network Folders" it actually shows me all the shares on the Windows network.

Progress!! :-D

Then if I click on the share I want I get the timeout error.  :-(

It shows me a page of exact information.  It has the IP address of the Windows machine, the name of the share....

It says the timeout value is 20 seconds but I get the error page in a half second.  This seems very strange.

I have upgraded my main desktop to 14.04 so now I have two machines in two different rooms of the house where I can work on this issue. :-)

[B]Possible Causes:
There may have been a problem at some point along the network path between the server and this computer.
The server was too busy responding to other requests to respond.[/B]

No, it is not either one of these as the Windows machines can always connect :-)
The Windows machines use a slightly different method "to retrieve share list from server".  The Samba client can be configured to work the same way.

Like it or we will need to use the terminal CLI to diagnose and fix the problem.  I'll provide the commands so you just have to provide the terminal response.  Post the output of this command ```
smbtree -d3
```

Place the text between [noparse]```
 
```[/noparse] blocks.  You can do this by clicking on the [SIZE=5]**# **[/SIZE]icon at the top of the advanced reply editor and pasting the info in between the blocks.

---

### Post by pbpersson on 2015-03-01
I figured there was some slight difference in how Ubuntu was doing this as opposed to Windows.  Here is the output you requested:

```

phil@Phil-Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter phil's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.23 at port 445
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
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b822b0] mpx_fde[(nil)] fd[9] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b81520] mpx_fde[(nil)] fd[10] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80ce0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80680] mpx_fde[(nil)] fd[12] - disabling
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b82590] mpx_fde[(nil)] fd[9] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b81800] mpx_fde[(nil)] fd[10] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80fc0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80670] mpx_fde[(nil)] fd[12] - disabling
TEAL-NETWORK
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.108 ( 192.168.0.108 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.108 at port 445
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.108 at port 445
phil@Phil-Ubuntu:~$ 

```

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> I figured there was some slight difference in how Ubuntu was doing this as opposed to Windows.  Here is the output you requested:

```

phil@Phil-Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter phil's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.23 at port 445
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
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b822b0] mpx_fde[(nil)] fd[9] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b81520] mpx_fde[(nil)] fd[10] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80ce0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80680] mpx_fde[(nil)] fd[12] - disabling
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b82590] mpx_fde[(nil)] fd[9] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b81800] mpx_fde[(nil)] fd[10] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80fc0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fbf86b80670] mpx_fde[(nil)] fd[12] - disabling
TEAL-NETWORK
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.108 ( 192.168.0.108 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.108 at port 445
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.108 at port 445
phil@Phil-Ubuntu:~$ 

```

This is normal```
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: [COLOR="#008000"]**Permission denied**[/COLOR]
```

But this is not```
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: [COLOR="#FF0000"]No such file or directory[/COLOR]
```

The file is owned by root so permission denied is logical, but the file should exist.  What portions of Samba have you modified; if anything?

What output to you get if you use smbtree like this```
sudo smbtree -d3
```
 What output do you get from this command```
ls -l /var/cache/samba/
```

Is the username phil used on the windows machines?  Are the shares open to everyone?

---

### Post by pbpersson on 2015-03-01
**What portions of Samba have you modified; if anything?**

It depends.  If the configuration files are on the /home mount point, the /home is very old - I have kept it for many years as I have done fresh installs of several Ubuntu versions.  The root mount point is brand new, I formatted it when I installed 14.04 and I have not touched anything.

[B]What output to you get if you use smbtree like this
sudo smbtree -d3[/B]

```
phil@Phil-Ubuntu:~$ sudo smbtree -d3
[sudo] password for phil: 
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
Connecting to 192.168.0.23 at port 445
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
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030566230] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa0305654a0] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030564c60] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030564600] mpx_fde[(nil)] fd[14] - disabling
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030563ee0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa0305662a0] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030566ca0] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fa030566500] mpx_fde[(nil)] fd[14] - disabling
TEAL-NETWORK
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.108 ( 192.168.0.108 )
Connecting to 192.168.0.108 at port 445
Connecting to 192.168.0.108 at port 445
phil@Phil-Ubuntu:~$ 

```

[B]What output do you get from this command
ls -l /var/cache/samba/[/B]

```
phil@Phil-Ubuntu:~$ ls -l /var/cache/samba/
total 416
-rw-r--r-- 1 root root 425984 Mar  1 13:12 gencache.tdb
phil@Phil-Ubuntu:~$ 

```

**Is the username phil used on the windows machines? Are the shares open to everyone?**

Yes, the phil account is on all Windows machines and the password is the same.  Do I need to enter the account and password into some Samba configuration file?  The shares are open to Everyone with full control.

---

### Post by bab1 on 2015-03-01
> Yes, the phil account is on all Windows machines and the password is the same. Do I need to enter the account and password into some Samba configuration file? The shares are open to Everyone with full control. 

I'm not a Windows guy at all.  The user (or group) Everyone may not the same as everyone (all users).  I would try and give the user *phil* full control.

The Ubuntu Samba client is finding all the machines but the user is not allowed access.

I'm wondering what Samba packages you do have installed.   Post the output of this```
sudo dpkg -l | grep samba
```

---

### Post by pbpersson on 2015-03-01
I have added the phil account to both shares with full control, no change with regards to the error message in Konqueror.

Every time I upgrade to a new version of Ubuntu I run a script to re-install all the packages that were in the old version.  I wonder if I have some samba package that should not be there?

```
phil@Phil-Ubuntu:~$ sudo dpkg -l | grep samba
[sudo] password for phil: 
ii  python-samba                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Python bindings for Samba
ii  samba-common                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       all          common files used by both the Samba server and client
ii  samba-common-bin                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba common files used by both the server and the client
ii  samba-libs:amd64                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba core libraries
phil@Phil-Ubuntu:~$ 

```

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> I have added the phil account to both shares with full control, no change with regards to the error message in Konqueror.

Every time I upgrade to a new version of Ubuntu I run a script to re-install all the packages that were in the old version.  I wonder if I have some samba package that should not be there?

```
phil@Phil-Ubuntu:~$ sudo dpkg -l | grep samba
[sudo] password for phil: 
ii  python-samba                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Python bindings for Samba
ii  samba-common                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       all          common files used by both the Samba server and client
ii  samba-common-bin                                      2:[COLOR="#FF0000"]4.1.6[/COLOR]+dfsg-1ubuntu2.14.04.7                       amd64        Samba common files used by both the server and the client
ii  samba-libs:amd64                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba core libraries
phil@Phil-Ubuntu:~$ 

```

All the packages that are there are good.  We are now using Samba v4 (see the red above.)   See if you have this package```
sudo dpkg -l |grep cifs
```

---

### Post by pbpersson on 2015-03-01
```
phil@Phil-Ubuntu:~$ sudo dpkg -l |grep cifs
[sudo] password for phil: 
ii  cifs-utils                                            2:6.0-1ubuntu2                                      amd64        Common Internet File System utilities
phil@Phil-Ubuntu:~$ 
```

---

### Post by bab1 on 2015-03-01
All these test are coming up okay.  I'm running out of theories here.  One more piece of information and then I'm going to have you install the Samba server package.

Post the output of this```
sudo pdbedit -L
```

---

### Post by pbpersson on 2015-03-01
```
phil@Phil-Ubuntu:~$ sudo pdbedit -L
[sudo] password for phil: 
sudo: pdbedit: command not found
phil@Phil-Ubuntu:~$ 
```

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> ```
phil@Phil-Ubuntu:~$ sudo pdbedit -L
[sudo] password for phil: 
sudo: pdbedit: command not found
phil@Phil-Ubuntu:~$ 
```

I'm stumped.  Everything points to the Ubuntu machine running only the Samba client software.  It appears everything is installed correctly.

I wonder if the Windows machines are configured properly for NetBIOS over TCP (NBT).  You can check the Windows host this way```

    1. Click Start, point to Settings, and then click Network and Dial-up Connection.
    2. Right-click Local Area Connection, and then click Properties.
    3. Click Internet Protocol (TCP/IP), and then click Properties.
    2. Click Advanced.
    5. Click the WINS tab, and then click Enable NetBIOS over TCP/IP.
```

If you have any firewalls on these Windows hosts you need to make sure that NBT is allowed to pass through.

[COLOR="#0000FF"]Edit:  This is the difference between Samba SMB and Windows SMB.  Windows no longer uses NetBIOS over TCP (NBT).  Samba still uses this functionallity.[/COLOR]

---

### Post by pbpersson on 2015-03-01
I went into the Windows machine and set it always use NetBIOS over TCP/IP.  There is no change.

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> I went into the Windows machine and set it always use NetBIOS over TCP/IP.  There is no change.

So it was set to NOT use NBT and you set it TO USE NBT?

If so, reboot the machine and wait 5 minutes or so and try again from the Ubuntu machine.

---

### Post by pbpersson on 2015-03-01
Is there a tutorial somewhere that shows how this is supposed to work?  Are there any configuration steps needed?  Does Ubuntu know to use the phil account and the password with the Windows machines?

---

### Post by pbpersson on 2015-03-01
> **bab1 said:**
> So it was set to NOT use NBT and you set it TO USE NBT?

If so, reboot the machine and wait 5 minutes or so and try again from the Ubuntu machine.

I cannot reboot the Windows machine.  It is doing a seven hour file transfer.

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> Is there a tutorial somewhere that shows how this is supposed to work?  

Not that I'm aware of.  Not even Microsoft can state a concise how to.  All the Samba documentation is located [here]("https://www.samba.org/samba/docs/").  I would say that the "By Example" series would be you best bet to learn how to configure Samba sharing.  It is rally for Samba v3, but for now it is applicable to Samba v4 standalone file sharing servers.
> 
Are there any configuration steps needed?  
No configuration steps are needed for a Samba client.  The Samba file sharing mechanism (smbd and nmbd) is configured via /etc/samba/smbd.  The latest Samba Active Directory Domain Controller (AD-DC) is configured via extensive scripting to configure the LDAP back end.  I mention this only so you are aware of the samba daemon.  THIS IS FOR THE AD-DC ONLY.  It is not needed for a simple stand alone file sharing server. > 
Does Ubuntu know to use the phil account and the password with the Windows machines?
It should know.  I used the fact that there was no pdbedit to confirm that the Samba server was NOT installed.

I guess you will have to wait until the Windows machine is through with what you have started before we can continue with what we are doing.  Do you have another Windows machine with shares that we can test with?

---

### Post by pbpersson on 2015-03-01
[ATTACH=CONFIG]260376[/ATTACH]
The top radio button was clicked which I think means it was using NetBIOS.  I changed it to always force NetBIOS.  I don't think this is the issue.

I looked in the Windows logs, found the error, and followed the steps in this article:  [https://social.technet.microsoft.com/Forums/windows/en-us/30919e4f-6810-48d6-8769-2cff61f07544/event-id-2017-the-server-was-unable-to-allocate-from-the-system-nonpaged-pool-because-the-server?forum=w7itpronetworking](https://social.technet.microsoft.com/Forums/windows/en-us/30919e4f-6810-48d6-8769-2cff61f07544/event-id-2017-the-server-was-unable-to-allocate-from-the-system-nonpaged-pool-because-the-server?forum=w7itpronetworking)

I still would like to know why when Ubuntu tries to access a Windows share it is so much different than a Windows machine accessing it.  Perhaps this is one of the mysteries of the universe I will never understand.  ;-)

As I said, I cannot reboot that machine until tomorrow morning.  I will let you know what happens.

Thank you for all your help! :-D

---

### Post by pbpersson on 2015-03-01
When I asked if there was a simple tutorial I was thinking something like this: [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

I don't know if that is up to date or will even work.  Oh....I guess that is for server, not client.

I have more Windows machines but I have other projects I need to work on tonight.  I am hoping the registry change will do the trick.

Thank you,


Phil

---

### Post by bab1 on 2015-03-01
> **pbpersson said:**
> [ATTACH=CONFIG]260376[/ATTACH]
The top radio button was clicked which I think means it was using NetBIOS.  I changed it to always force NetBIOS.  I don't think this is the issue.

The top button you have selected is NOT for NETBIOS.  It is for LMHOSTS; and even older protocol (LanMan).  The radio button that is labeled "enable" does just that.  It enables NETBIOS over TCP/IP.  This allows the NETBIOS name to be broadcast over the network you have configured with IP Addressing.
> 
I looked in the Windows logs, found the error, and followed the steps in this article:  [https://social.technet.microsoft.com/Forums/windows/en-us/30919e4f-6810-48d6-8769-2cff61f07544/event-id-2017-the-server-was-unable-to-allocate-from-the-system-nonpaged-pool-because-the-server?forum=w7itpronetworking](https://social.technet.microsoft.com/Forums/windows/en-us/30919e4f-6810-48d6-8769-2cff61f07544/event-id-2017-the-server-was-unable-to-allocate-from-the-system-nonpaged-pool-because-the-server?forum=w7itpronetworking)

Hmmm...
> 

I still would like to know why when Ubuntu tries to access a Windows share it is so much different than a Windows machine accessing it.  Perhaps this is one of the mysteries of the universe I will never understand.  ;-)

Microsoft is the keeper of the protocol.  The SMB and NETBIOS protocols were backwards engineered  It's hard to keep up with a moving target; even harder if it is stealth.  It has been only recently the protocol was was forced to be revealed by court order.

The current smbd daemon (process) is not as current as the latest Microsoft version.  As it relates to Samba v3 it will not be updated.  The Samba developers are working on an updated version for Samba v4.

At this point, it is what it is. You can make it work but it appears the problem is with your Microsoft configuration.
> 

As I said, I cannot reboot that machine until tomorrow morning.  I will let you know what happens.

Thank you for all your help! :-D
We shall see then what the next step is.

My Microsoft experience is limited.  The majority of my experience (20+ years) is UNIX/Linux based.  In the past I have configured Samba server file shares and I run Samba at home.  My Windows machines at home share files so they are considered servers, but they are not what Windows calls "Windows Server".  They are Windows 7 and Vista laptops.

I've seen registry hacks, but I don't know enough to comment on them.  This is after all an Ubuntu Linux forum.  ;-)

---

### Post by pbpersson on 2015-03-02
This is the setting that was used before we started:

[B]Use NetBIOS setting from the DHCP server.  If static IP address is used or the DHCP server does not provide NetBIOS setting, enable NetBIOS over TCP/IP
[/B]

Since this Windows 7 Professional workstation (not server) uses a static IP, I think that means I was using NetBIOS all along.  :confused:

After rebooting the Windows machine I can now access and read/write Windows shares on the main Ubuntu desktop from Dolphin but not Nautilus which is fine for my purposes. \\:D/

The second Ubuntu machine sees the Windows workgroup but says there are no machines or shares. :-(

I cannot work on this today, I will get back to it tonight and check the same things on this machine that we checked on the other. :-)

---

### Post by bab1 on 2015-03-02
> **pbpersson said:**
> This is the setting that was used before we started:

[B]Use NetBIOS setting from the DHCP server.  If static IP address is used or the DHCP server does not provide NetBIOS setting, enable NetBIOS over TCP/IP
[/B]

Since this Windows 7 Professional workstation (not server) uses a static IP, I think that means I was using NetBIOS all along.  :confused:
This does not take into account the methods that Samba users for host discovery and the master browser listing.  Samba ONLY uses NetBIOS over TCP/IP (NBT).
> 
After rebooting the Windows machine I can now access and read/write Windows shares on the main Ubuntu desktop from Dolphin but not Nautilus which is fine for my purposes. \\:D/
[QUOTE]As they say the proof is in the pudding.  If you have a Windows machine that is serving file shares that a Samba client accesses you need NB. 


The second Ubuntu machine sees the Windows workgroup but says there are no machines or shares. :-(
[/QUOTE]Sometimes it is just a matter of time (15 minutes or so) before the Master Browse List is propagated.> 

I cannot work on this today, I will get back to it tonight and check the same things on this machine that we checked on the other. :-)
A good idea.

---

### Post by pbpersson on 2015-03-02
Okay, I am now working on the second Ubuntu 14.04 machine.  This is a brand new fresh install.  I will attempt to provide the output of all the commands we used to troubleshoot the first machine.

smbtree -d3:
```
phil@PT-Phil:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.23 bcast=192.168.0.255 netmask=255.255.255.0
Enter phil's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
Connecting to 192.168.0.23 at port 445
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
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
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
		\\PT-PHIL\print$         	Printer Drivers
		\\PT-PHIL\IPC$           	IPC Service (PT-Phil server (Samba, Ubuntu))
TEAL-NETWORK
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f18980] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f19400] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f174f0] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f171d0] mpx_fde[(nil)] fd[18] - disabling
	\\PHIL-WINDOWS7  		
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WINDOWS7<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WINDOWS7<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PHIL-WINDOWS7<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f17250] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f18d90] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f19770] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f195d0] mpx_fde[(nil)] fd[18] - disabling
	\\PAM-WINDOWS    		
resolve_lmhosts: Attempting lmhosts lookup for name PAM-WINDOWS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PAM-WINDOWS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PAM-WINDOWS<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f15820] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f19070] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f19510] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f3501f172b0] mpx_fde[(nil)] fd[18] - disabling
phil@PT-Phil:~$ 

```

sudo smbtree -d3:
```
phil@PT-Phil:~$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.23 bcast=192.168.0.255 netmask=255.255.255.0
Enter root's password: 
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
Connecting to 192.168.0.23 at port 445
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
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PT-PHIL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
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
		\\PT-PHIL\print$         	Printer Drivers
		\\PT-PHIL\IPC$           	IPC Service (PT-Phil server (Samba, Ubuntu))
TEAL-NETWORK
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name TEAL-NETWORK<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\WINDOWS8-TEST  		
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name WINDOWS8-TEST<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e5e40] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e50b0] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e4830] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e41d0] mpx_fde[(nil)] fd[18] - disabling
	\\PHIL-WINDOWS7  		
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WINDOWS7<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PHIL-WINDOWS7<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PHIL-WINDOWS7<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e5860] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e4600] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e5f70] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e4540] mpx_fde[(nil)] fd[18] - disabling
	\\PAM-WINDOWS    		
resolve_lmhosts: Attempting lmhosts lookup for name PAM-WINDOWS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name PAM-WINDOWS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name PAM-WINDOWS<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e4600] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e5920] mpx_fde[(nil)] fd[16] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e5340] mpx_fde[(nil)] fd[17] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fe4c96e3810] mpx_fde[(nil)] fd[18] - disabling
phil@PT-Phil:~$ 

```

ls -l /var/cache/samba/:
```
phil@PT-Phil:~$ ls -l /var/cache/samba/
total 16
-rw-r--r-- 1 root root  237 Mar  2 18:33 browse.dat
-rw-r--r-- 1 root root  696 Feb 28 00:40 gencache.tdb
-rw------- 1 root root  696 Feb 28 01:31 netsamlogon_cache.tdb
drwxr-xr-x 2 root root 4096 Feb 28 00:40 printing
phil@PT-Phil:~$ 

```

sudo dpkg -l | grep samba:
```
phil@PT-Phil:~$ sudo dpkg -l | grep samba
ii  python-samba                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Python bindings for Samba
ii  samba                                                 2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                                          2:4.1.6+dfsg-1ubuntu2.14.04.7                       all          common files used by both the Samba server and client
ii  samba-common-bin                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba common files used by both the server and the client
ii  samba-dsdb-modules                                    2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba Directory Services Database
ii  samba-libs:amd64                                      2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba core libraries
ii  samba-vfs-modules                                     2:4.1.6+dfsg-1ubuntu2.14.04.7                       amd64        Samba Virtual FileSystem plugins
ii  system-config-samba                                   1.2.63-0ubuntu6                                     all          GUI for managing samba shares and users
phil@PT-Phil:~$ 

```

sudo dpkg -l |grep cifs:
```
phil@PT-Phil:~$ sudo dpkg -l |grep cifs
ii  cifs-utils                                            2:6.0-1ubuntu2                                      amd64        Common Internet File System utilities
phil@PT-Phil:~$ 
```

sudo pdbedit -L:
This does nothing but if I do it without the sudo I get:
```
phil@PT-Phil:~$ pdbedit -L
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/private/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/private/passdb.tdb!
User Search failed!
phil@PT-Phil:~$ 

```

Does this help?

---

### Post by bab1 on 2015-03-02
> Does this help? 
Not really.  I'm not sure what I should expect vs what I do see.  It would be helpful to know what the various hosts names are, what OS they are running and what shares have been created.  It appears that some of these machines are working now, but there is nothing for me to compare it to

Maybe something like this will simplify things.
```

Server Name::    OS::        Shares::     IP address::
 

```

---

### Post by pbpersson on 2015-03-02
There are no servers.

There is only one machine and one share I care about:

//PHIL-WINDOWS7/DataStorage and the IP address is 192.168.0.108

That is a Windows7 Professional Workstation.

I thought that perhaps by comparing the Ubuntu machine that is not working to the one that is now working you would discover that something was installed that should not have been or something was not installed that should have been.

---

### Post by bab1 on 2015-03-02
> **pbpersson said:**
> There are no servers.

There is only one machine and one share I care about:

//PHIL-WINDOWS7/DataStorage and the IP address is 192.168.0.108

That is a Windows7 Professional Workstation.

Without getting too deep into it; Anytime you have _a host sharing its files with others it is a server_.  Despite what the Microsoft label says.  This host is acting as a server.  It is important as it may be the cause of some of the problems.  In any event it is helpful to understand which machine is ***serving*** the files and which machine is acting as a client.
> 

I thought that perhaps by comparing the Ubuntu machine that is not working to the one that is now working you would discover that something was installed that should not have been or something was not installed that should have been.
I'm not convinced that the machine that you say is working is really running correctly.  So let's check ***both clients*** (Your Ubuntu hosts) first.

Explain how the IP addressing is configured.  Is it via DHCP, or Reservation or statically set?  For each host post the output of these commands (separate code blocks for each host please)```

cat /etc/hosts

hostname

cat /etc/samba/smb.conf
```

Please insure that NetBIOS over TCP is enabled on any Widows host that is sharing files.

---

### Post by pbpersson on 2015-03-02
For both these Ubuntu machines, the IP addressing is the default which I believe is DHCP.

I must do these two machines in different posts.

This is the first machine we worked on where I can now see shares in Konqueror and Dolphin.

cat /etc/hosts:
```
phil@Phil-Ubuntu:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Phil-Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
phil@Phil-Ubuntu:~$ 

```

hostname:  Phil-Ubuntu


cat /etc/samba/smb.conf:
```
phil@Phil-Ubuntu:~$ cat /etc/samba/smb.conf
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

phil@Phil-Ubuntu:~$ 

```

---

### Post by pbpersson on 2015-03-02
Here is the second machine, the one where I cannot see the shares on the network.

cat /etc/hosts:
```
phil@PT-Phil:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	PT-Phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
phil@PT-Phil:~$ 

```

hostname: PT-Phil


cat /etc/samba/smb.conf:
```
phil@PT-Phil:~$ cat /etc/samba/smb.conf
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

phil@PT-Phil:~$ 

```

---

### Post by bab1 on 2015-03-03
Both smb.conf files are identical.

I want you to add 2 lines to each smb.conf file.  These should clean up most of the errors and bring us closer to what will be correct for your installation.

Please at these lines to the [global] section of the /etc/samba/smb.conf file for the host Phil-Ubuntu```

name resolve order = host bcast
netbios name = PHIL-UBUNTU

```...you need to edit the file as the root user so you need to use this method:  

Make a back up copy```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

Edit the original```
sudo nano /etc/samba/smb.conf
```...The first section is the [global] section.  You can add the 2 lines anywhere in that section.

Now restart the smbd daemon```
sudo service restart
```

Now do the same thing with the host PT-Phil
```

name resolve order = host bcast
netbios name = PT-PHIL

```

Once both machines have been restarted wait 5 minutes and see if you can now browse the network.  Post the output of one of these machines for this command```
smbtree -d3
```

---

### Post by pbpersson on 2015-03-03
I made those changes on both machines.  I also changed the workgroup name to TEAL-NETWORK as that is the workgroup name for the Windows machines.  I restarted both machines and waited five minutes.  The machine that worked before in Dolphin and Konqueror still worked and the machine that did not work before still does not work.  The machine I am typing on now still does not work, PT-Phil.  I wonder if I rebooted them and tried again with this machine first if this one would work and the other one would not?  It's just a random thought.  Here is the output you requested, this is from PT-Phil:

```
phil@PT-Phil:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.23 bcast=192.168.0.255 netmask=255.255.255.0
Enter phil's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814a530] mpx_fde[(nil)] fd[9] - disabling
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814a5c0] mpx_fde[(nil)] fd[9] - disabling
TEAL-NETWORK
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814e7d0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814da40] mpx_fde[(nil)] fd[12] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814d200] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814cba0] mpx_fde[(nil)] fd[14] - disabling
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
resolve_hosts: Attempting host lookup for name PT-PHIL<0x20>
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
		\\PT-PHIL\print$         	Printer Drivers
		\\PT-PHIL\IPC$           	IPC Service (PT-Phil server (Samba, Ubuntu))
	\\PHIL-WINDOWS7  		
resolve_hosts: Attempting host lookup for name PHIL-WINDOWS7<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c8150410] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814fa30] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814cce0] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814f890] mpx_fde[(nil)] fd[16] - disabling
	\\PAM-WINDOWS    		
resolve_hosts: Attempting host lookup for name PAM-WINDOWS<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139
Connecting to 198.105.254.23 at port 445
Connecting to 198.105.254.23 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c8150370] mpx_fde[(nil)] fd[13] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c8150430] mpx_fde[(nil)] fd[14] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814cdf0] mpx_fde[(nil)] fd[15] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7fc6c814f9b0] mpx_fde[(nil)] fd[16] - disabling
phil@PT-Phil:~$ 

```

---

### Post by bab1 on 2015-03-03
The problem is due to the Ubuntu Samba clients looking to the internet to resolve what is an internal LAN NetBIOS name.  You can see that with this line```

resolve_hosts: Attempting host lookup for name WINDOWS8-TEST<0x20>
Connecting to 198.105.244.23 at port 445
Connecting to 198.105.244.23 at port 139

```  This will have to be suppressed.  It is easy to do.

You need to edit both machines /etc/samba/smb.conf file and remove the hosts parameter so the name resolve line looks like this```
name resolve order = bcast 
```

Then you need to either reboot the machines or restart smbd with this```
sudo service smbd restart 
```

Post another ```
smbtree -d3 
```

[COLOR="#0000FF"]Edit:  The IP address 198.105.244.23 is in a block of addresses owned by[/COLOR]```
NetRange:       198.105.240.0 - 198.105.255.255
CIDR:           198.105.240.0/20
NetName:        SEARCHGUIDE
NetHandle:      NET-198-105-240-0-1
OrgName:        Search Guide Inc
OrgId:          SG-63
Address:        1942 Broadway
Address:        Suite 319
City:           Boulder
StateProv:      CO
PostalCode:     80302

```
My guess is your ISP is directing your errant requests to this site.  The DNS request (hosts) should be dropped but most ISP's ignore the protocol and accept $$$ for redirecting this kind of traffic.  What DNS servers have you specified.  You can use OpenDNS or Google public DNS servers if you like.

---

### Post by pbpersson on 2015-03-03
That certainly works very differently!  If this is the answer, why isn't this parameter automatically included?  Sharing now works perfectly from PHIL-UBUNTU in Nautilus.  It is really nice to see.  I have not specified any DNS servers in Ubuntu, I assumed that would be handled by DHCP.  Here is what the Windows machine has for DNS servers:

192.168.0.1
205.171.2.25

Here is the output of that command:

```
phil@Phil-Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter phil's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
TEAL-NETWORK
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name TEAL-NETWORK<0x1d>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WINDOWS8-TEST  		
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name WINDOWS8-TEST<0x20>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\PT-PHIL        		PT-Phil server (Samba, Ubuntu)
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name PT-PHIL<0x20>
Got a positive name query response from 192.168.0.23 ( 192.168.0.23 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.23 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\PT-PHIL\print$         	Printer Drivers
		\\PT-PHIL\IPC$           	IPC Service (PT-Phil server (Samba, Ubuntu))
	\\PHIL-WINDOWS7  		
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name PHIL-WINDOWS7<0x20>
Got a positive name query response from 192.168.0.108 ( 192.168.0.108 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.108 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\PHIL-WINDOWS7\W$             	Default share
		\\PHIL-WINDOWS7\Users          	
		\\PHIL-WINDOWS7\U$             	Default share
		\\PHIL-WINDOWS7\R$             	Default share
		\\PHIL-WINDOWS7\prnproc$       	Printer Drivers
		\\PHIL-WINDOWS7\print$         	Printer Drivers
		\\PHIL-WINDOWS7\PerssonTechnologies	
		\\PHIL-WINDOWS7\MovieFiles     	
		\\PHIL-WINDOWS7\Movie MPEG Files Backup	
		\\PHIL-WINDOWS7\IPC$           	Remote IPC
		\\PHIL-WINDOWS7\F$             	Default share
		\\PHIL-WINDOWS7\DataStorage    	
		\\PHIL-WINDOWS7\D$             	Default share
		\\PHIL-WINDOWS7\C$             	Default share
		\\PHIL-WINDOWS7\ADMIN$         	Remote Admin
	\\PAM-WINDOWS    		
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
name_resolve_bcast: Attempting broadcast lookup for name PAM-WINDOWS<0x20>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
Unable to create directory /var/run/samba for file gencache_notrans.tdb. Error was Permission denied
tdb(__NULL__): tdb_open_ex: called with name == NULL
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=320)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\PAM-WINDOWS\W$             	Default share
		\\PAM-WINDOWS\print$         	Printer Drivers
		\\PAM-WINDOWS\IPC$           	Remote IPC
		\\PAM-WINDOWS\HP Officejet 5600 series	HP Officejet 5600 series
		\\PAM-WINDOWS\E$             	Default share
		\\PAM-WINDOWS\D$             	Default share
		\\PAM-WINDOWS\C$             	Default share
		\\PAM-WINDOWS\ADMIN$         	Remote Admin
phil@Phil-Ubuntu:~$ 

```

I will report on how PT-Phil is doing when I get to that room of the house.

---

### Post by pbpersson on 2015-03-03
Sharing is also working perfectlly on the second machine!  Thank you so much for your help!!  :-D  \\:D/

---

### Post by bab1 on 2015-03-03
> **pbpersson said:**
> ... why isn't this parameter automatically included?  Sharing now works perfectly from PHIL-UBUNTU in Nautilus.  It is really nice to see.  I have not specified any DNS servers in Ubuntu, I assumed that would be handled by DHCP. 

What works for you may not be what others need.  Your use case is in the minority.  There really is no accounting for poor ISP networking practices.  WE haven't added anything.  It is more like we removed the offending requests (wins and hosts) and insured that the NetBIOS names are available for broadcast resolution (bcast).  We could have left LM Hosts in but no one really uses that style of resolution (lmhosts) anymore.

In the majority of cases (including my configuration) the wins parameter fails silently and the hosts parameter is used to provide the NetBIOS name.  I would add to your notes that whenever you install install Ubuntu and need to use Samba, that you make the changes we made last.  You just need to add the 2 lines and all should be fine. 

If you need Samba to share files you would need to add the Samba server and edit the smb.conf file like we did and also add the shares at the bottom of that file.

Please mark this thread **solved ** as we have come to a satisfactory ending to the problem.

---

