---
title: "PDC Angst"
date: 2005-08-04
forum: Networking &amp; Wireless
---

### Post by betamax on 2005-08-04
Hello,

I've been attempting to set up Ubuntu as a DHCP/SAmba/PDC for a test network in my quest to replace a windows based network with a Linux one.

I now have a running DHCP server, but so far I've had no luck with the PCD, I can see the shares setup on the server but have problems when attempting to connect workstations to the domain/server.   

The problem happens when I try and enter a admin username/password on the workstation required to join the domain. All I get is a user does not exist error.

I've attempted to login with two user accounts, but both act the same.
Heres the main section of my smb.conf, maybe I'm misssing something obvious.

Darren

====================================================

[global]
	workgroup = BUNTYNET
	netbios name = hoarybox
	server string = Samba Server

	interfaces = 192.168.0.1/255.255.255.0
	security = user
  	encrypt passwords = yes
	add machine script = /usr/sbin/useradd -d /dev/null -g workstation -s /bin/false -M %u
	
	logon script = logon.bat
	logon path = \\%L\profiles\%U
	logon drive = z:
	logon home = \\%L\%U\win_profile
	domain logons = Yes
	os level = 64
	preferred master = Yes
	domain master = Yes
	hosts allow = 192.168.1. 192.168.0.
	name resolve order = wins bcast lmhosts hosts
	wins support = no
	time server = Yes
	max log size = 1000
	log level = 0

[netlogon]
   	path = /usr/local/samba/lib/netlogon
   	writable = no
   	browsable = no

[profiles]
   	path = /home/samba-ntprof
  	browsable = no
   	writable = yes
   	create mask = 0600
   	directory mask = 0700

---

### Post by snowjunkie on 2005-09-27
Did you ever get this sorted.  I'm about to embark on a similar mission!

---

### Post by betamax on 2005-10-01
Hi,

Yes the problem wasn't the config file it was the way I had the two network cards configured.

Good luck,

Darren

---

