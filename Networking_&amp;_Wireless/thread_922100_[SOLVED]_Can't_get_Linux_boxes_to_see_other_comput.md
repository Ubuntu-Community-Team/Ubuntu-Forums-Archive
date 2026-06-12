---
title: "[SOLVED] Can't get Linux boxes to see other computers, including themselves, but Wind"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by rafe101 on 2008-09-16
I have been having a horrible time getting the networking working correctly.  I have had Ubuntu on this laptop since January, and it's never worked correctly.  I think with Gutsy it worked more often.  The Windows laptop and desktop talked fine and would see the Ubuntu laptop, so I could move things by just using them.  It was a pain, but it worked.

Recently, I put Ubuntu on the desktop, and since it's used for storage and printing, I decided to get this working right, but I can't do it.  Now I only have one computer that can see anything.  The Ubuntu machines don't even see themselves in the workgroup from the Network window.

I'm not sure what information someone might want, but this might give one some idea:

rafe@rafe-laptop:~$ smbtree
Password: 
DIDO
	\\TERESA-LAPTOP  		Teresa-laptop
Error connecting to 216.24.138.156 (No route to host)
cli_start_connection: failed to connect to TERESA-LAPTOP<20> (216.24.138.156). Error NT_STATUS_HOST_UNREACHABLE
	\\RAFE-LAPTOP    		Ubuntu
Error connecting to 127.0.1.1 (Connection refused)
cli_start_connection: failed to connect to RAFE-LAPTOP<20> (127.0.1.1). Error NT_STATUS_CONNECTION_REFUSED
	\\DIDO-DESKTOP   		dido-desktop server (Samba, Ubuntu)
Error connecting to 216.24.138.156 (No route to host)
cli_start_connection: failed to connect to DIDO-DESKTOP<20> (216.24.138.156). Error NT_STATUS_HOST_UNREACHABLE
rafe@rafe-laptop:~$

I don't know where it's getting those IPs because they don't look familiar to me.

I hope someone can help me.  I can't seem to find anything searching.

---

### Post by darco on 2008-09-17
You should post your smb.conf file located in the /etc/samba/. 
Take a look at this link [http://www.linux.com/feature/125452](http://www.linux.com/feature/125452) , webmin/swat are your friends,,,,your smbtree post is very strange

good luck
darco

---

### Post by rafe101 on 2008-09-17
Darco, thanks in advance.  For space's sake, I cut out the nulled lines, and here's what's left:

[global]

   netbios name = rafe-laptop
   workgroup = DIDO
   server string = Ubuntu
   wins support = no

   dns proxy = yes

   name resolve order = lmhosts host wins bcast

   log file = /var/log/samba/log.%m

   max log size = 1000
   syslog = 0
 
   panic action = /usr/share/samba/panic-action %d

   guest account = guest
   invalid users = root

   load printers = yes

   printing = bsd
   printcap name = /etc/printcap   
   printing = cups
   printcap name = cups

   socket options = TCP_NODELAY

   domain master = auto

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash

   winbind enum groups = yes
   winbind enum users = yes

   usershare allow guests = yes

[homes]
   comment = Home Directories
   browseable = yes
   read only = no
   create mask = 0775
   directory mask = 0775

wins support = no
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0775

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[Documents]
   path = /home/rafe/Documents
   available = yes
   browsable = yes
   public = yes
   writable = yes

Everyone here is worse than me at this stuff, so I need it to be simple to use.  No passwords or nags when sharing files.

Thanks again.

---

### Post by darco on 2008-09-17
Here a partial smb of mine and I left areas where you maybe lacking...is this a home network? Mine is and I share 1 laptop ubuntu/Vista and 2 pcs Linux MInt and Vista and do not have any sharing/password  issues using this config.

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = workgroup

# server string is the equivalent of the NT Description field
   server string = %h Laptop


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


usershare owner only = FALSE

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
   interfaces = 192.168.15.0/255.255.255.0


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = SHARE

***edit***
I have these lines commented out..
domain master = auto

idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash

winbind enum groups = yes
winbind enum users = yes


darco

---

### Post by rafe101 on 2008-09-17
Darco,

I made those changes, but now don't even see the workgroup anymore.  I had the worgroup but it was empty before.  Also, my smbtree command now returns this:

rafe@rafe-laptop:~$ smbtree
Password: 
rafe@rafe-laptop:~$ 

Nothing.

No information from smbstatus either.


rafe@rafe-laptop:~$ smbstatus
Global parameter wins support found in service section!

Samba version 3.0.28a
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files



This thing is very frustrating.

---

### Post by rafe101 on 2008-09-17
Well, this morning, the workgroup showed back up in the laptop's Network Places, but there's still nothing. in it.

---

### Post by darco on 2008-09-17
As far as I know, all PC's must have the same workgroup name in order to connect to them so I am assuming you did not physically change the other pc WG names??,.... Can you see your laptop from the other pc's? You never said if this was a home network or not.
Ubuntu/Mint  also has sharing option for individual folders and if I remember correctly when first choosing the share option it downloads specific samba (?) permissions....
darco

---

### Post by rafe101 on 2008-09-18
No, I changed them all to workgroup "DIDO", Windows from the properties and the two Ubuntus, edited in smb.conf.

Only the Windows machine consistently sees anybody, themselves included.  Even though the Ubuntu machines can't see themselves or each other (I can't ping from them or see a smbtree), I can save files to and from the Ubuntu computers using the Windows laptop.

Yeah, this is a home network, but I use the term "network" loosely.

---

### Post by rafe101 on 2008-09-19
I really simplified my smb.conf file, but still can't get it to work.  I found what seems like a good guide at [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html), but none of the checks are working for me.  Do I have to configure xinetd?  I have no idea what to do with that.

---

### Post by rafe101 on 2008-09-19
I am much closer to getting this straightened out.  There were no values in my xinetd.conf file.  I read this guide and used the sample configuration, and the laptop is at least now seeing other computers, from there, I think it's just playing with permissions.

Darco, again, thanks for your help.  I feel I owe you a beer or something.

---

### Post by darco on 2008-09-19
Dont give up....I had to go thru the same thing awhile ago. Its a learning process. The webmin app works thru your browser and its another way  to learn samba.

heres a link that another Ubuntu user swears by....

[http://www.linux.com/articles/58593](http://www.linux.com/articles/58593)

good luck

darco

---

### Post by rafe101 on 2008-09-19
I tried using webmin when you suggested it, but I got a bunch of errors like it wasn't getting permission to look at or change values.  I didn't play with too long.

---

### Post by rafe101 on 2008-09-19
Darco, I finally got it all working.  You know what I had to do?  I still could not see any information in the windows shares from the Ubuntu computers.  SMBTREE was still returning errors about not finding paths.  I tried messing with everything I could think of.  I set exceptions in the router's firewall for my mac addresses.  I turned the whole firewall off.  Finally, I set my router to use OpenDNS and put my network name in the exceptions and it all works now.

---

### Post by max5555 on 2009-11-14
> **rafe101 said:**
> ESKTOP<20> (216.24.138.156). Error NT_STATUS_HOST_UNREACHABLE

add IP and the name of the computer to /etc/hosts

---

