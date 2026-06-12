---
title: "Ads in Login"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by pgp_protector on 2011-08-31
I've been around, but off of Linux for quite a while, well in working on some PHP / SOAP Projects for work I decided to try Linux again (and again & again)

Long Story Short.
I Used the install guide "The Perfect Server" from How to Forge, and it went off without any major hitches, and is up & running. I can even access my wordpress page from outside the house.

Now the real question.

When i login to my server with PuTTY from another computer I get what I can only call an Ad for cononical.com (graph this data & manage this system.....)

How do I remove this?

---

### Post by SavageWolf on 2011-08-31
[http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-change-message-of-the-day-motd-in-ubuntu-server.html) might do it.

---

### Post by cariboo on 2011-08-31
Do you mean this:

> ssh willy
cariboo@willy's password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-11-server x86_64)

 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)

0 packages can be updated.
0 updates are security updates.

No mail.
Last login: Wed Aug 31 12:42:32 2011 from 192.168.1.104


---

### Post by pgp_protector on 2011-08-31
> **cariboo907 said:**
> Do you mean this:

Actually this is what I get.
```


Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Aug 31 15:39:10 PDT 2011

  System load:  0.0                Processes:           115
  Usage of /:   0.7% of 228.01GB   Users logged in:     0
  Memory usage: 37%                IP address for eth0: 192.168.1.10
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/
Last login: Wed Aug 31 13:12:45 2011 from (SecuritySnip)

```
the **[COLOR="Red"]Graph this data and manage this system at [noparse]https://landscape.canonical.com/[/noparse][/COLOR]**
is what I'm looking at removing.

I tried doing the sudo vi /etc/motd and removing it, but it comes right back.

when trying sudo vi /etc/motd.tail it's a blank file.

---

### Post by CVGH on 2011-08-31
Look at /etc/ssh/sshd_config
Comment the BANNER line out maybe?

---

### Post by pgp_protector on 2011-08-31
> **CVGH said:**
> Look at /etc/ssh/sshd_config
Comment the BANNER line out maybe?

If I'm reading this right it is.
> 
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

Subsystem sftp /usr/lib/openssh/sftp-server

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


PrintMotd no
#Banner /etc/issue.net

---

### Post by pgp_protector on 2011-09-01
Found the adds were coming from /usr/bin/landscape-sysifo 
edited the /etc/update-motd.d/50-landscape-sysinfo file to fix it thanks to this link.

[http://kember.net/articles/removing-landscape-advert-from-ubuntu-login/](http://kember.net/articles/removing-landscape-advert-from-ubuntu-login/)



/usr/bin/landscape-sysinfo
Changed to
/usr/bin/landscape-sysinfo --exclude-sysinfo-plugins=LandscapeLink

---

### Post by pgp_protector on 2011-09-01
FYI Also it trying to make this ad go away by editing the /etc/motd it "broke" ?? the systemlink to the actual file.

To fix that I ran 
sudo ln -s /var/run/motd /etc/motd

---

### Post by madjr on 2011-09-01
glad is linux and you're allowed to remove/modify/get in the source, if it were "another" OS you get stuck with it :p

---

