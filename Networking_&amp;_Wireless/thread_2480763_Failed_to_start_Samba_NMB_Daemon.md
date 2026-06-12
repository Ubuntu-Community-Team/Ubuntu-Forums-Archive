---
title: "Failed to start Samba NMB Daemon"
date: 2022-11-09
forum: Networking &amp; Wireless
---

### Post by johndid on 2022-11-09
Hi,

After I updated my Ubuntu Server 20.04 lts I found out that the NMB Daemon service has some problems to start.
So I run it manually via my Cockpit's GUI, but it gets terminated after a little while:

here is a screenshot of the log in the WEBGUI:

[[IMG]https://thumbs2.imgbox.com/b0/8f/z4eEzBsc_t.jpg[/IMG]](https://imgbox.com/z4eEzBsc)

So, I disabled it. However, the sharing of folders works regularly. 
What can the issue be?
Thanks

---

### Post by TheFu on 2022-11-09
There are too many possible issues to list them all, based on the information provided.

An OS upgrade leaves cruft around .... how many upgrades has this system been subjected?  Was it a fresh install in 2006 with Ubuntu 6.06 and has it been upgraded LTS-to-LTS all this time, leaving cruft behind with each LTS upgrade?  Or something else?  Just asking, because many things change over time, even between 1 LTS to the next LTS.  Since 2016, Samba has changed greatly as MSFT started taking security more serious. They've introduced new, more secure, SMB versions and changed default settings to be a little more secure too.  For everyone who isn't MSFT trying to be compatible with as many different devices as possible, it is very hard.  I think today, Samba defaults try to make Win10 client connections the easiest, which can screw over any older version of Windows and other devices like streaming sticks and TVs.

The first thing I'd do, assuming samba is actually needed (why?), would be to purge the samba packages completely, then install them new and set the shares by manually editing the /etc/samba/smb.conf file. May want to install wsdd avahi-daemon packages so Win1X can  browse shares too.

 I've never needed to touch any nmb.conf settings - - ever.  Don't forget to use smbpasswd to create samba user accounts.  Also, beware that with almost every LTS release, the Samba guys are trying to catch up to MSFT CIFS default settings which improve security and break access for older devices, including media players and Android apps.  Win7 supports version SMB v2.1 at the highest.  I think Win10 supports SMB v3.11 and Win11 supports SMB v3.11 at least.

To see the actual protocols your Samba server is supporting, nmap can be used:
```
sudo nmap --script smb-protocols 172.16.22.14
```
Use the correct IP address of your Samba server.
Mine returns : 
```
...
Host script results:
| smb-protocols: 
|   dialects: 
|     2.10
|     3.00
|     3.02
|_    3.11

```  I specifically don't allow any SMB lower than 2.1 here.  Some android apps require NT1 SMB version.  I just use sftp from android (Ghost Commander), if the data isn't available through the LAN nextcloud server.  Between ssh, rsync, scp, sftp, sshfs, pretty much any computer has secure, fast, access to all the data on the LAN.  Of course, some devices want to use a different protocol.  My Kodi and Jellyfin systems use NFS or DLNA.  The Kodi guys all recommend against using CIFS/Samba.  But if you have MS-Windows clients and WinSCP/Filezilla don't fit your needs, samba is the only real solution remaining.

---

### Post by johndid on 2022-11-10
Hi,
Same old Ubuntu server 20.04 LTS since the very beginning. I regularly update and upgrade packages for security and bug issues.

I too ran across many issues trying to make SAMBA on linux and Windows work together over the last years.
Now, every device with Windows, Linux, or Android as OS on my LAN can get access to my shared folders created in Ubuntu......[B]except one!
[/B]
There has been no way to make my **Windows 10 laptop** get access to my shared folder on Ubuntu. This laptop runs the same Windows 10 version as my Windows desktop PC which has no problem with accessing the
aformentioned folders on linux. The laptop also has a distro linux installed in dual boot which has no problem to access the shared folders. Thus, the issues lies on the laptop's Windows OS.
I tried anything to fix the problem but I failed each time (disabling firewall, installing SMB 1/CIFS on windows...everything I could think of).

I also thought that the issue with the Samba NMB Daemon might have something to do with my problem, so I turned here to get another chance to fix it. 

As for the nmap command:

```

sudo nmap --script smb-protocols 192.168.3.10

Starting Nmap 7.80 ( https://nmap.org ) at 2022-11-10 12:26 UTC
Nmap scan report for 192.168.3.10
Host is up (0.000089s latency).
Not shown: 990 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
82/tcp   filtered xfer
139/tcp  open     netbios-ssn
445/tcp  open     microsoft-ds
631/tcp  open     ipp
5000/tcp filtered upnp
8000/tcp filtered http-alt
8083/tcp filtered us-srv
9000/tcp filtered cslistener
9090/tcp open     zeus-admin

Host script results:
| smb-protocols:
|   dialects:
|     2.02
|     2.10
|     3.00
|     3.02
|_    3.11



```

Thanks

---

### Post by TheFu on 2022-11-10
If you are just copying files around, use sftp.  WinSCP or FileZilla or the built-in MSFT sftp.exe or PuTTY's psftp.exe will all work from the Windows side.
Samba has been a PoS to get working in recent years.

---

### Post by johndid on 2022-11-10
> **TheFu said:**
> If you are just copying files around, use sftp.  WinSCP or FileZilla or the built-in MSFT sftp.exe or PuTTY's psftp.exe will all work from the Windows side.
Samba has been a PoS to get working in recent years.

Yes, I turn to sftp (filezilla mostly) if I need to copy files around and can't rely on Samba, but I'd like to fix the samba issue and, above all, understand what is wrong with it on my Windows 10 laptop. There might be cases when I need to use Samba necessary on other people's LANs.
Thanks

---

### Post by TheFu on 2022-11-10
> **johndid said:**
> Yes, I turn to sftp (filezilla mostly) if I need to copy files around and can't rely on Samba, but I'd like to fix the samba issue and, above all, understand what is wrong with it on my Windows 10 laptop. There might be cases when I need to use Samba necessary on other people's LANs.
Thanks

Morbius1 posts about samba in these forums are usually the best guides for getting things working. He has a knack for reading into the details to recognize the real issue in a configuration.  I'm inclined to think that the problem is from all the tinkering on the Windows laptop side trying to get things working.  Enabling NT1 samba wasn't a good idea.  I'd use a backup from before that change to "put it back".  Lacking that, a fresh install after a wipe.

I'm lucky. Since Win7, samba is kinda just worked for me.  OTOH, I barely use Windows anymore and keep zero files on Windows storage.

---

### Post by johndid on 2022-11-10
Ok. Thanks

---

### Post by Morbius1 on 2022-11-10
> Now, every device with Windows, Linux, or Android as OS on my LAN can get access to my shared folders created in Ubuntu......except one!

There has been no way to make my Windows 10 laptop get access to my shared folder on Ubuntu. This laptop runs the same Windows 10 version as my Windows desktop PC which has no problem with accessing the aformentioned folders on linux. The laptop also has a distro linux installed in dual boot which has no problem to access the shared folders. Thus, the issues lies on the laptop's Windows OS.
If everyone else can connect to the Ubuntu server except one Win10 machine I would have to agree that the culprit sounds like the one Win10 machine.

I would see if Samba itself works from that machine by accessing it directly.

In WIn10 open explorer and access the ubuntu server it by it's ip address:
```
\\192.168.3.10
```
You can also connect to it by it's mDNS hostname ( a hostname.local syntax )from Windows:
```
\\ubuntu-server-host-name.local
```
If you are using Ubuntu server not Ubuntu desktop you will need to install avahi on the Ubuntu machine for this to work:
```
sudo apt install avahi-daemon
```

**[COLOR="#FF0000"]EDIT: Sorry, I got sloppy. The wsdd package is available in Ubuntu 22.04 not 20.04 so this won't work for you:[/COLOR]**

If you are trying to "discover" then access a share on that machine from WIn10 ( Explorer > Network > Server > Share ) you will need to install another package on Ubuntu.

Windows no longer uses nmbd - NetBIOS to discover things in the network. It uses WS-Discovery so it no longer needs SMBv1 ( NT1 ). 

You can implement the server part of that in ubuntu by installing wsdd:
```
sudo apt install wsdd
```

In all the above cases it requires that the Win10 machine in question and the Ubuntu server are in the same subnet which may very well be the underlying problem here.

---

### Post by johndid on 2022-11-11
> **Morbius1 said:**
> If everyone else can connect to the Ubuntu server except one Win10 machine I would have to agree that the culprit sounds like the one Win10 machine.

I would see if Samba itself works from that machine by accessing it directly.

In WIn10 open explorer and access the ubuntu server it by it's ip address:
```
\\192.168.3.10
```


No doubt. The problem lies definitely on the Windows laptop 

I got this error message when I try to connect to my Ubuntu server machine (192.168.3.10) via Windows 10 explorer:

[https://imgbox.com/y9KxmH3k](https://imgbox.com/y9KxmH3k)

And of course, Ubuntu server and the Windows laptop are in the same subnet: 192.168.3.0/24

Thanks

---

