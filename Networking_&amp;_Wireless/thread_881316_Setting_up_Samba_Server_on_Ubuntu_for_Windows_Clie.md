---
title: "Setting up Samba Server on Ubuntu for Windows Clients"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by fhsm on 2008-08-05
Samba is killing me.  I cannot seem to get it working for love or money.

**Goal**: Share an external drive hanging off my Ubuntu system with all the windows systems on my network.  As far as security goes I'd like to protect the server from users but give users all equal full control of the whole drive.  

**What I've Done**:
I started with a fresh Ubuntu HH Desktop install and then...

```

sudo apt-get update
sudo apt-get install tasksel samba
sudo /etc/init.d/samba stop
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.BKUP
sudo touch /etc/samba/smb.conf
sudo gedit /etc/samba/smb.conf

```


Put in the following in smb.conf File: 
```

# Samba config file for sharing files on Ubuntu with Windows

#======================= Global Settings =======================
# General Settings for this Samba Server.

[global]

### Browsing/Identification ###
# Setting should match the Windows workgroup you want to share with
   	workgroup = MYWORKGROUP

# Should be set to match this systems hostname
	netbios name = UbuntuHostName

# What will show up in the "discription" area of windows
	server string = %h server (Samba, Ubuntu)

# Disable DNS proxy to keep from looking up NetBIOS names via DNS.
	dns proxy = no

# Naming service order for resolving host names to IPs
	name resolve order = lmhosts wins bcast

# Set the socket connection options (opt for Linux serving a LAN)
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

### Loggin ###
# Set Samba to use a separate log file for each machine that connects
# %m is replaced by the machine name
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# Set how much goes to syslog vs. samba/log (1 is not much)
	syslog = 1

# What to do when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d

####### Authentication #######
# "security = user" will require a local *nix account for every Samba user
### [Added: I tried with both user and share security]###
	security = user
;	security = share

# Location of username map file in form *nix user = samba/win user
	username map = /etc/samba/smbusers

# Allow users to have a null (blank) password (impt for Windows)
	null passwords = true

# Enable password encryption (required for Windows, requires smdpasswd file)
	encrypt passwords = true

# Password database (required if encrypt password = true)
	passdb backend = tdbsam

# Block root user for security
	invalid users = root
	force user = Working-HH-User-With-Access-to-Share 
        guest ok = Yes

# Unix password sync options to keep Samba and *nix PWDs matched
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes

#=========================== Share ===========================
#The settings will share the Public folder of the home directory

[Public]
# Settings for sharing the Public folder
# Limit to just the user's Public folder
;	valid users = %S

# Set permissions for the share (0700 is default; 0755 is group R/W)
	path = /media/MyDrive
	create mode = 0775
	directory mode = 0775
	browseable = yes
	read only = no
	;veto files = /*.{*}/.*/mail/bin/
	;force user = YOUR_USERNAME
	;force group = YOUR_USERGROUP

I tested lots and lots of combos of those conf options, but posting them all would make this question pages long.

```
back at the terminal 
```

sudo /etc/init.d/samba start

```

SYSTEM RESTART

```

sudo smbpasswd -a <UbuntuUser>
sudo smbpasswd -e <UbuntuUser>
sudo gedit /etc/samba/smbusers

```

Into /etc/samba/smbusers I entered: 
```

UbuntuUser = WindowsUser

```

Back at the terminal 

```

sudo chmod 0777 /media/MyDrive
sudo ufw disable
sudo /etc/init.d/samba restart

```

On Windows:
Took down its firewall and tried to map a network drive to the samba share.  Authentication failed.  Over and over again.  
After a bunch of experimentation I'm reasonably sure that something is wrong with the authentication on the Ubuntu side. I tried a packet capture on the windows system and could see the smb connection setup traffic going between server and client and each time the HH server rejected the connection.  

Why is Samba Server on Hardy rejecting connections from Windows?

Any help would be very very much appreciate!

I realize this is a long and overly detailed post but I want to try and get any possible detail someone might need to help me out on this.

---

