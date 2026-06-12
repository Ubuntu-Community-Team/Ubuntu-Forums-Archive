---
title: "match user does not work in sshd_config"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by kingl on 2015-09-02
To whom it may concern:

i have 64bit 14.04.1 ubuntu server.

OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014

what i am trying to do is to allow 3 users to login through ssh .

for which i put 

AllowUsers user1 user2 user3

it's working fine.

[B]and 2 can log in using password and 1 user can only login using ssh key:

Match user user3
PasswordAuthentication no[/B]
 
I also tried 
 
PasswordAuthentication no
Match user !user3
    PasswordAuthentication yes
 
And
 
Match user user3
PasswordAuthentication no
Match user otherusers
PasswordAuthentication yes

Once I added that, it would disable password login for all users.

any help is appreciated.

sshd_config content:

Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
UsePrivilegeSeparation yes
 
KeyRegenerationInterval 3600
ServerKeyBits 1024
 
SyslogFacility AUTH
LogLevel INFO
 
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
AllowUsers user1 user2 user3
 
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
 
PermitEmptyPasswords no
ChallengeResponseAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
 
Subsystem sftp /usr/lib/openssh/sftp-server
 
UsePAM yes

---

