---
title: "SCP The services allows SFTP connection only"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by Eiman on 2014-06-20
Hi there, 
We did setup a SFTP , SSH server on ubuntu, everything works fine, and we can upload files using sftp client.
SSh working fine as well, but once we we want to upload a  using **scp **command, we are getting the message : ‘The services allows SFTP connection only’
The syntax is used :  scp local_file accountname@ website.ftp.com:remote_file_uploads/file_name
Below you will find the sshd config...can you please advise?




# Package generated configuration file
# See the sshd_config(5) manpage for details


# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes


# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768


# Logging
SyslogFacility AUTH
LogLevel INFO


# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes


RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys


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


Subsystem sftp internal-sftp
#  Subsystem sftp /bin/sh -c 'umask 0002; exec /usr/libexec/openssh/sftp-server'
#  Subsystem sftp /usr/lib/openssh/sftp-server -u 0002
  ChrootDirectory /sftp/%u
  X11Forwarding no
  AllowTcpForwarding no
  ForceCommand internal-sftp
#  ForceCommand internal-sftp -u 0002


  


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
Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc

---

### Post by Lars Noodén on 2014-06-20
In your chroot environment, do you have ./usr/bin/scp in place?  The server needs that program to make a transfer using scp.  You might have to make do with just sftp.

---

### Post by Eiman on 2014-06-20
[COLOR=#000000]do you have ./usr/bin/scp  , how can I check that ? [/COLOR]

---

### Post by Eiman on 2014-06-20
I did 
root@sftp:/etc/ssh# ls /usr/bin/scp /usr/bin/scp
root@sftp:/etc/ssh#

---

### Post by Eiman on 2014-06-20
Can you pleas advise?

---

### Post by Lars Noodén on 2014-06-20
Yes you have it in the main system.   But since you appear to  have a chroot set up for ssh, 

```

 ChrootDirectory /sftp/%u

```

you'll need to have one copy there too.

Using %u means that you'll have to have a copy for each user, too.  It would be much simpler to stay with sftp and not worry  about chrooted scp.  

What's in /sftp ?  And what's in the subdirectory for each user such as /sftp/eiman/usr/bin/ ?  It's there you'll have to have the stuff for scp, if you want to run it chrooted.  That will inlclude linux-vdso.so.1, /lib/x86_64-linux-gnu/libc.so.6, /lib64/ld-linux-x86-64.so.2 and whatever else [ldd](http://manpages.ubuntu.com/manpages/trusty/en/man1/ldd.1.html) warns of.  
 
However, if you can still ssh in without having set up anything special for chroot, then something else is wrong with where you are getting the configuration file.

---

### Post by Eiman on 2014-07-03
Hi there, 
Thanks for the reply. Due to the need of using SCP next to sftp, we would like to have SCP working as well.
The content of /sftp is

drwxr-xr-x 13 root root  4096 Jun 20 14:29 .
drwxr-xr-x 25 root root  4096 Jun 27 07:41 ..
drwxr-xr-x  3 root root  4096 Sep  8  2011 account1
drwxr-xr-x  3 root root  4096 Sep  8  2011 account2




root@sftp:/etc/ssh# ls -la /sftp/account1total 140
drwxr-xr-x  3 root root   4096 Sep  8  2011 .
drwxr-xr-x 13 root root   4096 Jun 20 14:29 ..
drwxrwxrwx  4 root root 131072 Mar  9 15:04 upload

Can you please explain what do I need to do to have SCP working?

Thanks,

---

