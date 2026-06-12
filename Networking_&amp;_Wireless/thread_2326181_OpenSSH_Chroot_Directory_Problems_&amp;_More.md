---
title: "OpenSSH Chroot Directory Problems &amp; More"
date: 2016-05-29
forum: Networking &amp; Wireless
---

### Post by Zenzija on 2016-05-29
Hey Guys & Gals,

This has been an ongoing nightmare for the past month. I've been working on trying to get my SSH Server to be default "home" directory for groupx.

I've got OpenSSH running on my 14.04 LTS. I have my Network Drive "J" stored in /media/share/storage. I can cd to it and view files, etc. I can connect via sftp using FileZilla on the root account and if I remove this bulk text and delete the user from the group, I can login to my "Home" directory. My network drive is mounted through cifs and fstab. sshfs refused to work for me, and I spent a few weeks trying to figure that out, and just gave up. Windows share is //sm-server/j or //192.168.1.112/j

Match Group groupx
ChrootDirectory /media/share/
ForceCommand internal-sftp
AllowTcpForwarding no
PermitTunnel no
X11Forwarding no


I've followed the guide; [http://ubuntuforums.org/showthread.php?t=1401258&highlight=OpenSSH+ChrootDirectory](http://ubuntuforums.org/showthread.php?t=1401258&highlight=OpenSSH+ChrootDirectory) at the bottom, however I do have a question in regards to this specifically; does it need to be root.root or root:root. Also, I don't use root to login, I have another username, is it still root.root/root:root or username.username/username:username?

If I try to chmod /media, I get "chmod: changing permissions of '/media/storage': Permission denied. This is a Windows share, so that somewhat sounds right?


> # Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 40
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

Match Group usergroup

ChrootDirectory /media/share/
ForceCommand internal-sftp
AllowTcpForwarding no
PermitTunnel no
X11Forwarding no


This is my fstab;
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=5f2dbb81-1a0a-48a6-a878-c9a19b5f78a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c102ca61-434c-4976-8087-bdf2e8867ad3 none            swap    sw              0       0
//sm-server/j   /media/share/storage    cifs    credentials=/home/username/.smbcredentials,iocharset=utf8,gid=1001,file_mode=0777,dir_mode=0777 0 0


This is what happens when I connect with FileZilla.
> Status:	Connecting to <redacted>:40...
Response:	fzSftp started, protocol_version=5
Command:	open "dreadstarx@<redacted>" 40
Command:	Pass: *************
Error:	Network error: Software caused connection abort
Error:	Could not connect to server

Where am I going wrong? I'm tired of trying to figure this out on my own...

---

