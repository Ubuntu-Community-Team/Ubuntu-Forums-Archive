---
title: "Trying to connect to my Windows network but failing with credentials"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by Sour Mash on 2014-04-25
Hi, I've been getting deeper into Ubunto following the death of my Windows HD (currently in for warranty replacement)
I played with Ubuntu long ago to resurrect some old laptops and some of it is coming back to me but I was never proficient.
What I'm doing now is trying to run a fresh install of Ubuntu on a USB drive connected to hard disk less desktop and get that to connect to my Windows network so I save to and read from a HD on another Windows machine on the network.
Ubuntu sees the windows network and can see the NAS Drive. It sees the PC I want to connect to and even sees the disc I want to connect to on that PC but when I try and open that disc I get this error

Failed to mount Windows share: Permission denied

So I figure there should be somewhere that I should be putting my credential for accessing that PC - but I can't find where!

Everything I have read so far seems to suggest I should edit the /etc/fstab file but I have to admit I don't know how. It also feels very counter intuitive to have to edit files to access a network share but then I've become conditioned to Windows so perhaps that's what makes it feel wrong :-)

Can anyone help me through the technicalities in a dumbed down way please (or point me at an existing resource).

Thanks

J

---

### Post by bab1 on 2014-04-25
> **Sour Mash said:**
> ... What I'm doing now is trying to run a fresh install of Ubuntu on a USB drive connected to hard disk less desktop and get that to connect to my Windows network so I save to and read from a HD on another Windows machine on the network.

Ubuntu sees the windows network and can see the NAS Drive. It sees the PC I want to connect to and even sees the disc I want to connect to on that PC but when I try and open that disc I get this error

Failed to mount Windows share: Permission denied

So I figure there should be somewhere that I should be putting my credential for accessing that PC - but I can't find where!

The user names on both the Ubuntu client and the NAS must match or you need to have the underlying file and directory permissions set to allow everyone to have the correct permissions.  Samba checks the authentication (who are you) and the OS sets the authorization permissions (you can do that) at the file or directory. 
> 
Everything I have read so far seems to suggest I should edit the /etc/fstab file but I have to admit I don't know how. It also feels very counter intuitive to have to edit files to access a network share but then I've become conditioned to Windows so perhaps that's what makes it feel wrong :-)

Ownership and permissions are set at partition mount time.  It depends upon what the file system format is and what you are trying to accomplish as to whether fstab is appropriate or not.  

Typically if you are trying to mount a local Windows formatted partition, you would want to explicitly mount the partition via fstab or a script.  If you are trying to mount a remote file system (the share) then you can allow the GUI to mount it or use fstab to set the options or use a script to to the same. 
> 

Can anyone help me through the technicalities in a dumbed down way please (or point me at an existing resource).

Thanks

J
What is the NAS vendor?  Is this SMB/CIFS?  What is the resource name (//SERVER/share)?   

On all of my machines I have one user name (bab).  Have you setup a consistent user name for all the machines you have?

Can we see the shares using this command```
smbtree
```...if so post the output here.

---

### Post by Sour Mash on 2014-04-27
Thanks for the response, I won't pretend to understand it all yet but I'm just pleased what I'm trying to do is doable :-)

I'm very unfamiliar with how to run commands and edit stuff in Ubuntu so I'm taking it slow.

Here's what smbtree returns

WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
		\\UBUNTU\HP-Photosmart-Plus-B210-series	HP Photosmart Plus B210 series
		\\UBUNTU\print$         	Printer Drivers
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
	\\LS-CHL738      		LinkStation
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
		\\BOSS\Z              	
		\\BOSS\Users          	
		\\BOSS\Public         	
		\\BOSS\print$         	Printer Drivers
		\\BOSS\IPC$           	Remote IPC
		\\BOSS\Incoming and Unsorted	
		\\BOSS\DVD Drive E    	
		\\BOSS\CutePDF Writer 	CutePDF Writer
		\\BOSS\Adobe PDF      	Adobe PDF

\\BOSS is the Windows machine that has the shares on it
\\BOSS\Z is the drive I want to access
\\LS-CHL738 is the NAS Drive (It's a Buffalo LinkStation)

So you're saying that I should have the same sign on credentials for the Windows and Ubuntu machines? They were not the same so I have created a new user on Ubuntu with the same credentials as Windows, is that OK?

---

### Post by Sour Mash on 2014-04-27
Well that didn't go well - Ubuntu does not now recognise me as a user :-( Tell me the username and password combo is incorrect - username is my name and password is my Windows password - I guess there's no way around this. I've just tried all the combinations of capitalisation of the user and password I can think of (it's a very simple combo!)
This is a whole new problem now - any ideas?

---

### Post by Sour Mash on 2014-04-27
Well I think I've well and truly wrecked things :-(

Is there a way I can delete the user account on the start up files? I'm thinking that if I can take the USB Hard Drive and plug it into the Windows machine I could access the files on it and remove or fix the username/password so I can then connect the drive back onto the other desktop machine and start Ubuntu. Or is this just a world of pain and I'm better off just formatting the thing and starting again? I don't want to do that as I have a bit of time invested in that drive but there's nothing I can't replace on it. 

I'm off to the garage to bit some metal with a hammer now and make something physical on my other interest, a 1972 Triumph TR6. Back later when I screw that up!

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> So you're saying that I should have the same sign on credentials for the Windows and Ubuntu machines? They were not the same so I have created a new user on Ubuntu with the same credentials as Windows, is that OK?
> 
Specifically, I asked if you had done that.  I didn't ask you *to do *anything.  With Ubuntu it's a little more difficult. On the other hand I assume //BOSS/Z  is a Windows machine.
 
Well that didn't go well - Ubuntu does not now recognise me as a user :-( 

By this I assume you can't log in as this new user?   Each machine has a local database of users.  So if you are going to have consistent interaction between these machines for CIFS sharing.  Then both machines need to have a user/pass that is recognized by the other.
> 
Tell me the username and password combo is incorrect - username is my name and password is my Windows password - I guess there's no way around this. I've just tried all the combinations of capitalisation of the user and password I can think of (it's a very simple combo!)
This is a whole new problem now - any ideas?
Lord knows what you are talking about.  Did you create a new user on the Ubuntu machine and now You can't log in as that user?

Why would you thing there is no way around this?  I have 6 machines sitting within a meter of me that I have setup with multiple users.  They all work perfectly using Samba and Windows sharing.

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Well I think I've well and truly wrecked things :-(

Is there a way I can delete the user account on the start up files?

Ubuntu is a multi user OS.  You don't need to remove user accounts to make others work.  I don't understand your problem.
> 
 I'm thinking that if I can take the USB Hard Drive and plug it into the Windows machine I could access the files on it and remove or fix the username/password so I can then connect the drive back onto the other desktop machine and start Ubuntu. Or is this just a world of pain and I'm better off just formatting the thing and starting again? I don't want to do that as I have a bit of time invested in that drive but there's nothing I can't replace on it. 

I think you should slow down a bit and not go off on your own.  I think it will be better ( and much quicker) if I ask a few questions and tell you want to do to correct what is wrong.  Most of these problems come from misunderstanding what it is you need to do to make things right.
> 
I'm off to the garage to bit some metal with a hammer now and make something physical on my other interest, a 1972 Triumph TR6. Back later when I screw that up!
I've fixed many TR-2,3,5,250 and 6 Triumphs in my day, along with MG's, Jaguars and Rolls from '63 to '82.

After you beat up the Triumph come back with your thoughts.  I'm on the west coast of the USA, so I'm going to sleep for 8 hours.

---

### Post by Sour Mash on 2014-04-27
Good advice, thank you :-) I was getting frustrated - it's not the end of the world and it can all be salvaged with time I'm sure.

I'm not sure what went wrong. I added a user account with name and password the same as the Windows machine but when I rebooted the Ubuntu machine, it asked for credentials and won't accept the username and password I created. It offers no other choice so I'm stuck with a sign on screen and I can't see a way to get passed it yet.
It sounds daft but I don't remember there being a user name and password in there before (although I know there must have been one). I can't see how I would get a list of user accounts from what I have now otherwise I'd just use the original account.

We should talk Triumphs sometime, I have a long history with them, not always good :-) [http://chinn.blogspot.co.uk/](http://chinn.blogspot.co.uk/) 

J

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Good advice, thank you :-) I was getting frustrated - it's not the end of the world and it can all be salvaged with time I'm sure.

I'm not sure what went wrong. I added a user account with name and password the same as the Windows machine but when I rebooted the Ubuntu machine, it asked for credentials and won't accept the username and password I created. It offers no other choice so I'm stuck with a sign on screen and I can't see a way to get passed it yet.
It sounds daft but I don't remember there being a user name and password in there before (although I know there must have been one). I can't see how I would get a list of user accounts from what I have now otherwise I'd just use the original account.

We should talk Triumphs sometime, I have a long history with them, not always good :-) [http://chinn.blogspot.co.uk/](http://chinn.blogspot.co.uk/) 

J
Something has gone terribly wrong. That doesn't sound correct at all.  All the users you add should show up at the login screen.  Originally did you set the login screen to no password?

I'm sure there is a way to restore the original user, but It's going to be easier for you to re-install the OS.  I know that if you wanted log in at the terminal we can do that.  I can guide you on what to do.  Maybe we can eliminate  the user you just added.  We can't muck it up any worse than it is right now.

I'll read your blog on Triumphs.  I prefer MG's.  I have a mild itch to create an MGB V8 with a FI Rover engine (Not factory).  I'm hoping it stays just a thought.  ;-)

---

### Post by Sour Mash on 2014-04-27
A Sebring style MG (bubble arches, cowled headlights) with a V8 in it is about the only MG that appeals to me, I prefer my Triumphs although the TR6 is not my favourite model to work on. I prefer the Vitesse (Sports 6 in the US and very rare over there) that's a Herald with a 2 litre 6 cylinder engine in it, you can put the TR6 2.5 litre in there too along with the Lucas fuel injection you guys never got :-)

I did have the original install as no password.

Anyway, I think I'll make life easier on us all and start with a fresh install of Ubuntu 14.04 on the USB drive then we can go from there at least knowing that anything I Previously screwed up is now overwritten!

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> A Sebring style MG (bubble arches, cowled headlights) with a V8 in it is about the only MG that appeals to me, I prefer my Triumphs although the TR6 is not my favourite model to work on. I prefer the Vitesse (Sports 6 in the US and very rare over there) that's a Herald with a 2 litre 6 cylinder engine in it, you can put the TR6 2.5 litre in there too along with the Lucas fuel injection you guys never got :-)

I did have the original install as no password.

Anyway, I think I'll make life easier on us all and start with a fresh install of Ubuntu 14.04 on the USB drive then we can go from there at least knowing that anything I Previously screwed up is now overwritten!

Right.  Post here when you are done.  It's always nice to start with the defaults.  Make the user have a password please.  I'm sure this is what caused your problem.  Linux expects to manage user/pass rather than user/no_pass.

I've gone between full Sebring to dead stock sleeper.  If I did it I would use modern updates to the front suspension and use a full 5 link located rear end with MGC differential.

---

### Post by Sour Mash on 2014-04-27
OK, I'm back with a fresh install of 14.04 on the USB drive - typing this on the Ubuntu machin listening to some music from the NAS drive. However, I still can't get into the Windows machine. I get the error

Failed to retrieve share list from server: Connection timed out

So, I'm not going to do anything more but wait fro instructions :-)

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> OK, I'm back with a fresh install of 14.04 on the USB drive - typing this on the Ubuntu machin listening to some music from the NAS drive. However, I still can't get into the Windows machine. I get the error

Failed to retrieve share list from server: Connection timed out

So, I'm not going to do anything more but wait fro instructions :-)

Let's start with the diagnosis.  This is going to output a lot of data.  You can capture it to a text file and then past to the editor between the ```
 blocks by using the [SIZE=5]# [/SIZE] icon in at the top of the Advance Editor.  Post the output of this from the terminal (Cntl+Alt+t)[CODE]smbtree -d3
```

This will show what Samba is attempting to do.

---

### Post by Sour Mash on 2014-04-27
Here we go

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
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
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name LS-CHL738<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LS-CHL738<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LS-CHL738<0x20>
resolve_hosts: getaddrinfo failed for name LS-CHL738 [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name BOSS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BOSS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name BOSS<0x20>
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 81.200.64.50 at port 445
Connecting to 81.200.64.50 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f54166046a0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5416603750] mpx_fde[(nil)] fd[12] - disabling
jason@Ubuntu:~$ 

```

I hope this means something to you because it's baffling to me :-)

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Here we go

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
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
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name LS-CHL738<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LS-CHL738<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LS-CHL738<0x20>
resolve_hosts: getaddrinfo failed for name LS-CHL738 [Name or service not known]
[COLOR="#0000FF"][B]name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )[/B][/COLOR]
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name BOSS<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BOSS<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
[COLOR="#FF0000"]resolve_hosts: Attempting host lookup for name BOSS<0x20>[/COLOR]
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
[COLOR="#FF0000"]Connecting to 81.200.64.50 at port 445
Connecting to 81.200.64.50 at port 139[/COLOR]
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f54166046a0] mpx_fde[(nil)] fd[11] - disabling
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f5416603750] mpx_fde[(nil)] fd[12] - disabling
jason@Ubuntu:~$ 

```

I hope this means something to you because it's baffling to me :-)
The bottom line is it is looking to the ISP for NETBIOS NAME resolution.  It should not do this EVER!  You can see this by the lines I have highlighted above in [COLOR="#FF0000"]red[/COLOR].

To correct that we need to limit Samba to broadcasting on the local LAN.  It is the only thing that is working anyway as shown by the lines highlighted above in [COLOR="#0000FF"]**blue**[/COLOR].

I'm looking for a line in the smb.conf file that has *"name resolve order" * in it.  To see if it is there do this```
cat /etc/samba/smb.conf | grep name resolve order
```...and post the output back here.

---

### Post by Sour Mash on 2014-04-27
Here you go

```
jason@Ubuntu:~$ cat /etc/samba/smb.conf | grep name resolve order
grep: resolve: No such file or directory
grep: order: No such file or directory
jason@Ubuntu:~$ 

```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Here you go

```
jason@Ubuntu:~$ cat /etc/samba/smb.conf | grep name resolve order
grep: resolve: No such file or directory
grep: order: No such file or directory
jason@Ubuntu:~$ 

```
Let's try it again with only one term for grep to use```
cat /etc/samba/smb.conf | grep resolve
```...the correct answer is that you should get nothing back.

---

### Post by Sour Mash on 2014-04-27
That doesn't give me anything either

```
jason@Ubuntu:~$ cat /etc/samba/smb.conf | grep resolve
jason@Ubuntu:~$ 

```

J

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> That doesn't give me anything either

```
jason@Ubuntu:~$ cat /etc/samba/smb.conf | grep resolve
jason@Ubuntu:~$ 

```

J

As I thought.  We need to edit the smb.conf file.  We want to add this line to the [global] section```
name resolve order = bcast
```... you can put it right below the workgroup declaration.

You have to edit the file as the root user, so we need to use this command```
sudo nano /etc/samba/smb.conf
```

After you have added the line and save the file we need to restart the smbd (Samba daemon) with this command```
sudo service smbd restart
```

Then try and browse the share again or try smbtree.

---

### Post by Sour Mash on 2014-04-27
Sorry I don't understand where I need to put the text, I'm looking at the smb.conf file

---

### Post by Sour Mash on 2014-04-27
Does it go in here?

```
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

```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Sorry I don't understand where I need to put the text, I'm looking at the smb.conf file

There should be a section similar to this```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup =  WORKGROUP
[COLOR="#0000FF"]name resolve order =  bcast[/COLOR]

```
Put the line I gave you just below the workgroup line.  Just as I have highlighted in blue above.

This configures the smbd daemon correctly each time the daemon is started.

After saving the file you will need to restart the daemon with the command I gave you.

---

### Post by Sour Mash on 2014-04-27
Grr, I get this

```
jason@Ubuntu:~$ sudo service smbd restart
[sudo] password for jason: 
smbd: unrecognized service
jason@Ubuntu:~$ 

```

I edited the file and saved as per your instructions so the file now reads 

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
name resolve order = bcast

# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)


```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Grr, I get this

```
jason@Ubuntu:~$ sudo service smbd restart
[sudo] password for jason: 
smbd: unrecognized service
jason@Ubuntu:~$ 

```

You can just reboot the entire machine.  We can figure out what they renamed the daemon to later on.  :-)

After the machine comes back up just do this```
smbtree -d3
```
I want to see if we can get this done tonight.

---

### Post by Sour Mash on 2014-04-27
OK rebooted, interestingly it didn't request a password (I stepped out whilst it rebooted so not sure what occurred, when I returned it was sat there at the desktop)

Here's the output

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Connecting to 192.168.84.9 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f28233f81e0] mpx_fde[(nil)] fd[6] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
jason@Ubuntu:~$ 

```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> OK rebooted, interestingly it didn't request a password (I stepped out whilst it rebooted so not sure what occurred, when I returned it was sat there at the desktop)

Here's the output

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Connecting to 192.168.84.9 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f28233f81e0] mpx_fde[(nil)] fd[6] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
[COLOR="#0000FF"][B]name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )[/B][/COLOR]
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
[COLOR="#FF0000"]SPNEGO login failed: Logon failure[/COLOR]
jason@Ubuntu:~$ 

```
We have made progress.  The blue above shows we can now resolve the name BOSS.  Unfortunately the red says we have a login failure.  Did you provide the password when smbtree asked for it?

---

### Post by Sour Mash on 2014-04-27
Yes, password provided, let me try again just to make sure I didn't mistype

---

### Post by Sour Mash on 2014-04-27
Same result so I'm sure it wasn't my tryping :-)

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Same result so I'm sure it wasn't my tryping :-)

Try smbtree -d3 again, only this time just hit enter.  Don't login at all.  What are the last few lines?

---

### Post by Sour Mash on 2014-04-27
Ran smbtree -d3 again and did not supply a password



```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f7b9e142e00] mpx_fde[(nil)] fd[12] - disabling
jason@Ubuntu:~$ 

```

NB, just noticed that the Windows machine is rebooting, I suspect it's just done some updates, should I run again when it's up?

---

### Post by Sour Mash on 2014-04-27
I ran it again anyway, no password supplied, just hit enter

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
jason@Ubuntu:~$ 

```

What is SPNEGO login?

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Ran smbtree -d3 again and did not supply a password



```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f7b9e142e00] mpx_fde[(nil)] fd[12] - disabling
jason@Ubuntu:~$ 

```

NB, just noticed that the Windows machine is rebooting, I suspect it's just done some updates, should I run again when it's up?

Yes run it again.  The last line changed and I believe it's due to the Windows machine being unavailable.

When do you need to stop for the evening?  I will be available tomorrow.

---

### Post by Sour Mash on 2014-04-27
I'm OK to keep playing for a little while yet as long as you are :-) The Windows machine is up again and I've re-run

```
jason@Ubuntu:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Connecting to 192.168.84.9 at port 139
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7f73b66e81e0] mpx_fde[(nil)] fd[6] - disabling
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\LS-CHL738      		LinkStation
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name LS-CHL738<0x20>
Got a positive name query response from 192.168.84.9 ( 192.168.84.9 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.9 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LS-CHL738\lp             	Network Printer for Windows
		\\LS-CHL738\info           	LinkStation Utilities
		\\LS-CHL738\share          	LinkStation folder
		\\LS-CHL738\IPC$           	IPC Service (LinkStation)
	\\BOSS           		Boss
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
jason@Ubuntu:~$ 

```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> I ran it again anyway, no password supplied, just hit enter

```
jason@Ubuntu:~$ smbtree -d3
...

name_resolve_bcast: Attempting broadcast lookup for name BOSS<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
jason@Ubuntu:~$ 

```

What is SPNEGO login?

That stands for Simple and Protected GSSAPI Negotiation Mechanism.  You can have different types of failure and still browse the shares.  So it's no big deal.  In fact I think the user name jason is not bing recognized.  Therefore Windows is treating you as an anonymous (guest) user.  This is not bad in its own right.  It's the same as just hitting enter at the prompt.

My theory is that you need to allow guest users (everyone?) or provide the user jason permission to access the share.

Not said very well.  I hope you understand.  What are the permissions on the Windows share.  Are the other machines off?

---

### Post by Sour Mash on 2014-04-27
I've just noticed that it's "jason" in Ubuntu and "Jason" in Windows, that wouldn't be helping would it? Is it easy to change the username to Jason in Ubuntu? (because I can't change it in Windows as it thinks there is already an account by that name!)

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> I've just noticed that it's "jason" in Ubuntu and "Jason" in Windows, that wouldn't be helping would it? Is it easy to change the username to Jason in Ubuntu? (because I can't change it in Windows as it thinks there is already an account by that name!)
I'm not sure that makes a difference.  Linux is case sensitive.  Windows is case insensitive.  So from Linux to Windows it shouldn't matter.  In fact for your use you should be able to just hit enter and have access.  It's just a simple home network, correct?

How about looking at the Windows permissions or making a new share (temp) that is available to everyone.  If you notice LS-CHL738 is pretty happy with the user jason's creds.

---

### Post by Sour Mash on 2014-04-27
It's a pretty standard Windows network - the Windows desktop is hardwired to the router, the NAS is Wifi to the WiFi base, the Ubuntu desktop is hardwired to the router. Let me make the Z drive on the Windows machine accept anyone and we'll see if that does the trick

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> It's a pretty standard Windows network - the Windows desktop is hardwired to the router, the NAS is Wifi to the WiFi base, the Ubuntu desktop is hardwired to the router. Let me make the Z drive on the Windows machine accept anyone and we'll see if that does the trick

Great.  I think it will answer a lot.

---

### Post by Sour Mash on 2014-04-27
This is weird

OK so I opened up the Z drive to everyone and went back to Ubuntu to browse the files, when I try and open BOSS I am asked for a password, so I type that in and then get the error message

```
Failed to mount Windows share: Cannot allocate memory
```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> This is weird

OK so I opened up the Z drive to everyone and went back to Ubuntu to browse the files, when I try and open BOSS I am asked for a password, so I type that in and then get the error message

```
Failed to mount Windows share: Cannot allocate memory
```

Stolen from [here]("http://ubuntuforums.org/newreply.php?do=newreply&p=13005202"):
> ... right click the shared folder on Windows and open the Properties dialog. The two tabs of interest are Sharing and Security. I had to grant the local user access on BOTH tabs. Initially, I had only done this on the Sharing tab. It's unfortunate the error message - "cannot allocate memory" - was not more helpful.

See if this solution works.

[COLOR="#0000FF"]Edit: one of these is for file and directory permissions (authorization) and the other is for access (authentication) to the share.  The user jason (Jason or JASON) needs both. [/COLOR]

---

### Post by Sour Mash on 2014-04-27
Hmm, the share tab was fine but then there was no sign of the permission in the security tab so I've changed that and it's now propagating, when it's done I'll have another check to see if I can open it up in Ubuntu

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Hmm, the share tab was fine but then there was no sign of the permission in the security tab so I've changed that and it's now propagating, when it's done I'll have another check to see if I can open it up in Ubuntu

My guess is the share Z  spans the entire disk, so you can't make a separate share on that.  Tell me you only have a few GB on the share Z.    ;-)

---

### Post by Sour Mash on 2014-04-27
err it's a 1TB drive but it's only 92% full ;-)

It's done now, time to test

---

### Post by Sour Mash on 2014-04-27
Nope, same error message when I try and open up Z
```
Failed to mount Windows share: Cannot allocate memory
```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Nope, same error message when I try and open up Z
```
Failed to mount Windows share: Cannot allocate memory
```

Before we go too much further I think we need to make a new share on directory with just a few text files.  Maybe just a single directory in the users home directory (Windows).  I don't want to have more than a few files in this directory so I can see if this is a load problem with BIG files and a lot of them in one directory.

---

### Post by Sour Mash on 2014-04-27
OK - small directory in the C drive of the Windows machine with two small txt files in it created, and I get the same failed to mount error in Ubuntu when I try and open it.

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> OK - small directory in the C drive of the Windows machine with two small txt files in it created, and I get the same failed to mount error in Ubuntu when I try and open it.

Then that rules out the registry problem that Windows 7 had around 2010.  Most of the stuff you find on Google with this problem we have just ruled out.  This is Windows 7 I assume.  What happens if you open a share on the NAS?  Does it really open and allow you to access files?  Do you have another Windows machine with shares?

---

### Post by Sour Mash on 2014-04-27
It's Vista. The NAS is behaving fine, I've been playing music and video files off it whilst we've been doing this.
I have a phone and tablet running Android and both can access the Windows shares OK. There are some video files on there that play fine on those devices so access is good.

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> It's Vista. The NAS is behaving fine, I've been playing music and video files off it whilst we've been doing this.
I have a phone and tablet running Android and both can access the Windows shares OK. There are some video files on there that play fine on those devices so access is good.

Let's try another Ubuntu tool.  This is smbclient.  We will try and access the host BOSS directly from Ubuntu.  Post the output of this```
smbclient -d3 -L boss
```...use your password,

---

### Post by Sour Mash on 2014-04-27
Here's the output, password used

```
jason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	Adobe PDF       Printer   Adobe PDF
	CutePDF Writer  Printer   CutePDF Writer
	DVD Drive E     Disk      
	Incoming and Unsorted Disk      
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Public          Disk      
	Temp            Disk      
	Test            Disk      
	Users           Disk      
	Z               Disk      
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$ 
```

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Here's the output, password used

```
jason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	Adobe PDF       Printer   Adobe PDF
	CutePDF Writer  Printer   CutePDF Writer
	DVD Drive E     Disk      
	Incoming and Unsorted Disk      
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Public          Disk      
	Temp            Disk      
	Test            Disk      
	Users           Disk      
	Z               Disk      
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$ 
```
Do the same thing without the password.  This share is Windows Vista and I can drag out my Vista laptop if I need to.

---

### Post by Sour Mash on 2014-04-27
Here's the output without using the password

```
jason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$ 

```

I'm going to turn in for the night, thanks for your help so far, catch you tomorrow.

J

---

### Post by bab1 on 2014-04-27
> **Sour Mash said:**
> Here's the output without using the password

```
jason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
[COLOR="#0000FF"]**Anonymous login successful**[/COLOR]
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$ 

```

I'm going to turn in for the night, thanks for your help so far, catch you tomorrow. 

J

The anonymous login was successful.  See the blue above.  I have to think about that...

---

### Post by Sour Mash on 2014-04-28
[QUOTE=bab1][QUOTE=Sour Mash]OK, I shut down the Windows for 15 mins and left the rest of the network running, I then booted up the Windows machine and tried to open the shares, same error
```
Failed to mount Windows share: Cannot allocate memory
```

:-([/QUOTE]

From the Ubuntu terminal, what do you get from this```

smbclient -d3 -L boss 

```[/QUOTE]

I have to go out on a mission of mercy, back in about 2 hours.

First running with a password, second run without

j```
ason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	Adobe PDF       Printer   Adobe PDF
	CutePDF Writer  Printer   CutePDF Writer
	DVD Drive E     Disk      
	Incoming and Unsorted Disk      
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Public          Disk      
	Temp            Disk      
	Test            Disk      
	Users           Disk      
	Z               Disk      
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[BOSS] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$ smbclient -d3 -L boss
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.84.2 bcast=192.168.84.255 netmask=255.255.255.0
Client started (version 4.1.6-Ubuntu).
Enter jason's password: 
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 445
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name boss<0x20>
Got a positive name query response from 192.168.84.3 ( 192.168.84.3 )
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: No such file or directory
Connecting to 192.168.84.3 at port 139
Doing spnego session setup (blob length=30)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6002 Service Pack 2] Server=[Windows Vista (TM) Ultimate 6.0]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
jason@Ubuntu:~$
```

---

### Post by bab1 on 2014-04-28
> **Sour Mash said:**
> I have to go out on a mission of mercy, back in about 2 hours.

I'll talk to you then.

Edit:  In looking at the responses it appears that both of them are working fine.  I wonder if this has something to do with the GUI interface which works slightly different.  Just a thought...

---

### Post by Sour Mash on 2014-04-28
I'm back - not sure about the GUI thought. I think I might just try and start again with Windows shares, reset all the security on the shares back to nothing and then share it without restrictions. Thinking about it, if the NAS share is OK then my problem is on the Windows machine?

---

### Post by bab1 on 2014-04-28
> **Sour Mash said:**
> I'm back - not sure about the GUI thought. I think I might just try and start again with Windows shares, reset all the security on the shares back to nothing and then share it without restrictions. Thinking about it, if the NAS share is OK then my problem is on the Windows machine?
Maybe, maybe not.  I need to see if you have actually created a Samba user.  You need both Ubuntu and Samba.  What do you get from this command```
sudo pdbedit -L 
```

---

### Post by Sour Mash on 2014-04-28
I get this
```
jason@Ubuntu:~$ sudo pdbedit -L
[sudo] password for jason: 
sudo: pdbedit: command not found
jason@Ubuntu:~$ 

```

I'm going to show my ignorance now, is SAMBA part of Ubuntu or something extra? I haven't installed anything other than the distro of 14.04 from the Ubuntu site

---

### Post by Sour Mash on 2014-04-28
Just looking at the software reveals some "fix" for Samba
```
Fix For Ubuntu 14.04 .. Make sure Samba is not installed. Then open terminal & type "sudo apt-get install gksu"  (Without The Quotes). 

Then type gksu-properties

In the dialogue that follows set authentication mode to "sudo" and grab mode to "enable"

Now Install Samba everything should be working & it show up on Unity Bar & Search.

Basically its the same steps Trevor Lane Ray did for 13.04
```

Should I go through this and install Samba?

---

### Post by bab1 on 2014-04-28
> Failed to mount Windows share: Cannot allocate memory
Just as a final not to all of this.  The problem turned out to  be a matter of too restrictive permissions on the Windows machine.  This stopped all users from accessing the Master Browse List and accessing the share: //boss/z.  After remaking the share and rebooting the Windows machine the problem  went away.

---

### Post by Sour Mash on 2014-04-29
Thanks for your patience and perseverance with this, very much appreciated :-)

---

