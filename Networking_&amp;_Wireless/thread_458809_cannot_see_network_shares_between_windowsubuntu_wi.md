---
title: "cannot see network shares between windows/ubuntu with samba"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by yellowband on 2007-05-30
Hi

I'm having an issue with setting up some shared folders between a windows vista and ubuntu 7.04 computer.  Both computers can access the internet (wirelessly).  I can ping one computer from the other by IP address but not by hostname.  I can also ping the gateway and dns servers.  I think the reason i cannot ping by hostname is because i am using openDNS on both of my machines.

anyways, i have set up samba according to ubuntuguide.org, and that did not work.  i have tried a few samba configurations, and even SWAT, but i still cannot see my shared ubuntu folders in windows.  Further, i canoot see my windows computer under "network" in ubuntu either.  

any help would be great as i have exhausted all of my knowledge and ideas.  thanks a lot.

---

### Post by yellowband on 2007-05-30
woah this is wacky

in windows, out of desparation, i tried to get to my music folder on the ubuntu box by typing in:

\\192.168.1.100\media1

and it worked.  whats going on here?  i mpaaed the network drive so i don't lose it, but by don't the network shares show up on in the network places folder where they should be?

---

### Post by cubbyboy57 on 2007-06-03
Thanks to this: [http://forums.fedoraforum.org/archive/index.php/t-19967.html]("http://forums.fedoraforum.org/archive/index.php/t-19967.html")

** notice I am in a root shell / type sudo in front of the command if you are not root **

You can set up the directory you want to share anywhere. The important thing is that the directory and file ownerships are set up correctly. I did it like this- 

root# useradd -c “Network Filestore” -m -g users -p secret netfiles
root# mkdir /export
root# chmod 766 /export
root# chown netfiles /export
root# chgrp users /export

Now we need to create an entry in the Samba password file for our netfiles username.

root# smbpasswd -a netfiles
New SMB password: secret
Retype SMB password: secret

I backed up the original smb.conf then created a new smb.conf file:

root# cp /etc/samba/smb.conf /etc/samba/smb.conf.orig
root# rm /etc/samba/smb.conf
root# cd /etc/samba
root@mymachine:/etc/samba#pico smb.conf 

I put in the following:

[global]
workgroup = WORKGROUP
netbios name = ubuntu
security = SHARE
wins support = yes

[DellE510]
comment = File storage on DellE510
path = /export
force user = netfiles
force group = users
read only = No
guest ok = Yes
available = yes
browsable = yes
public = yes
writable = yes

Control+x and saved the file as smb.conf

When I went to the System/Administration/Shared Folders I saw my /export listed. I clicked on the General Properties tab, I saw WORKGROUP in the domain/workgroup box.  I check the this computer is WINS server box (this seemed to open the UDP/TCP ports required)

To restart samba I did:
root# cd /etc/init.d/
root@mymachine:/etc/init.d/# ./samba restart (or start if it isn't running)

  
On my XP box I see the linux folder /export - as Samba(ubuntu) under WORKGROUP with a folder named DellE510.
I have to watch what I put in the folder when I am on the linux box --as I don't login as netfiles, so I have to chown/chgrp to netfiles/users for them to be accessible to the WinXP boxes, the other way doesn't matter.

Hope it helps someone - I am excited that my 2 boxes can share files!:popcorn:

---

### Post by Adapted.Cat on 2007-06-04
> **yellowband said:**
> 
in windows, out of desparation, i tried to get to my music folder on the ubuntu box by typing in:

\\192.168.1.100\media1

and it worked.  whats going on here?

There are two things going wrong here - browsing and name resolution. Browsing is easy
to fix - simply add "browsable = yes" to either the global section or the per-share sections
of your smb.conf file. Name resolution takes some explaining. For Microsoft's own bizarre
reasons, SMB has its own computer naming system distinct from DNS. You can set up one
of your machines to provide naming services, but it is much MUCH easier to simply edit the
LMHOSTS file. You'll find this in Windows in one of the following directories, or something like it:
C:\WINDOWS\SYSTEM32\DRIVERS\ETC
C:\WINDOWS\DRIVERS\ETC

Contained in there are the HOSTS file and the LMHOSTS file - both in a similar format - which
allow you to specify names for given hosts. It's best to keep these files as short as possible,
as Windows doesn't cache them and so reads through every line of the file every time it needs
to look something up. The format is:
<host_address> <host_name> [<alternative> ...]

If you use notepad to edit it, make sure it doesn't save as hosts.txt or lmhosts.txt - this
is wrong. The filename should have no extension.

In addition to SMB name resolution, it sounds like you're having a problem with IP name
resolution - which is why you can't ping. If you're using a DNS service like OpenDNS, what
this does is it associates the external IP address of DSL/Cable modem with the name you've
selected. Your modem then forwards packets to you. Very few cable modems will allow
internal hosts to access the external address, so such packets simply disappear.

To compensate you can simply add the OpenDNS domain name to your HOSTS file, using
the internal address of the machine you're after. For instance, if I have a website on
192.168.1.100, known locally as servmach, and I want it to listen for connections on the
address server.machine.some.domain, then when I want to connect to it from another
machine on the local network I put these lines in the other machine's HOSTS/LMHOSTS:
HOSTS: 192.168.1.100 servmach server.machine.some.domain
LMHOSTS: 192.168.1.100 servmach

In Linux and other Unix variants, those same files are in /etc/hosts and /etc/samba/lmhosts

---

