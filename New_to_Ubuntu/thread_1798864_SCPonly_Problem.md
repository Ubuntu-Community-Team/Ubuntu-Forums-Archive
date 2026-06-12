---
title: "SCPonly Problem"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by trevor_obba on 2011-07-06
I am running apache server 2.2.14 on ubuntu server (Lucid 10.04). Users  are not allowed to login locally or remotely through SSH to the server,  however I would like users to be able to sftp to the server.

I thought of using “scponly” which will give users an alternative shell,  the problem is that I have 3,000 which authenticate to LDAP.

As I cannot change their shell in LDAP I wrote a script to create  /etc/passwd from ldap. Now I have 3,000 user’s /etc/passwd in a file, I  can change their shell in the file however how do I tell sftp to read  the users shell from the file?

Basically, how do configure the server, so that the Shell is read from  the file and at the same time users can authenticate to LDAP to use  sftp? 

Any suggestion of a better way to solve the problem?
Can you help? Please.

---

### Post by trevor_obba on 2011-07-28
I figure it out; I modified my /etc/ldap.conf to include the following:
“nss_override_attribute_value loginShell /usr/bin/scponly”
And all 3,000 users inherited the login shell “/usr/bin/scponly” on the machine.

The next problem is how do to I chroot 3,000 sftp users
According to the scponly documentation you will need to specify each user’s home directory to chroot
Unfortunately I have 3,000 different home directories in different directory structure like:
/home/mouse/c4/worker01/usename
/home/angore/c5/worker02/usename
/home/puma/a2/worker03/username

All users authenticate to LDAP 
The openssh solution involves modifying /etc/ssh/sshd_config
# Use the following line to *replace* any existing 'Subsystem' line
Subsystem       sftp    internal-sftp

# These lines must appear at the *end* of sshd_config
Match Group sftponly
        ChrootDirectory %h
        ForceCommand internal-sftp
	AllowTcpForwarding no

The problem with the above is how do I specify 3,000 LDAP users “ChrootDirectory” and also make all users a member of sftponly.

How do I chroot sftp, (all users) bearing in mind that all 3,000 users  have different directory structure and all authenticate to LDAP?

Can you help or suggest a way to solve the problem? Please

---

