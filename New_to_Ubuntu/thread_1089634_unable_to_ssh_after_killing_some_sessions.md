---
title: "unable to ssh after killing some sessions"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Cyked on 2009-03-07
Today from work I was screwing around on my system in putty was looking for info on killing sessions. I did some research on killing sessions and found something on checking sessions and killing them with a kill -9.

So I did ps -aux | grep ssh to see what was open because I know since I have set up the system I have had putty sessions lock up on me and wanted to look into. So I say from the cmd above several sessions that from my perspective were open, so I did a kill -9 command on a few PIDs. I purposefully killed the session I knew was my current ssh session and was booted, and now can not ssh in. From work the session just times out in putty, from home I get a server unexpected closed session error. I was running hostsdeny but that has been stopped for a while now. I am using iptables, but every entry for that is empty now.

Not sure what is going on. I have rebooted the system since this start, and what I have described above is the very last thing I did before this issue started. Any advice as to where I should be looking?

---

### Post by Kareeser on 2009-03-07
That's odd... a reboot should have restarted the openssh-server.

Type "openssh-server" into the terminal. What comes out?

Edit: oops... my bad. Try

```
/etc/init.d/ssh start
```

---

### Post by rhcm123 on 2009-03-07
THats funky... even if you screwed up the SSH server it would have been fixed on a reboot... maybe the daemeon is still running somehow after a reboot

post your /etc/ssh/sshd_config for me please (on the machine you want to connect to)

---

### Post by Cyked on 2009-03-07
here is what happens when i start ssh
dpaul01@tux:/etc$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                                                      
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
                                                                                            [ OK ]



```
# Package generated configuration file
# See the sshd(8) manpage for details

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
#AuthorizedKeysFile	%h/.ssh/authorized_keys

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

UsePAM yes
```

---

### Post by rhcm123 on 2009-03-07
> **Cyked said:**
> here is what happens when i start ssh
userid@tux:/etc$ /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                                                       Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key


Well that answers it pretty simply. You somehow deleted your RSA & DSA keys. (Quickly googles how to fix this :) )

Alrighy, do this:
```
sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
```
Then this:
```
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
```

When prompted for a password, i find its easier to just leave it blank by hitting enter, so you don't have to enter it at boot time.

Also, when you later try and ssh in from the client machine, it will probably complain about "HOST VERIFICATION CHANGED". This is because the key the local SSH system has on record for this machine is now different because the machine is sending out the new one you just generated. This always happens to me when i reinstall ubuntu onto my server.

To fix this, i find the simplest way is to clear my /home/USERNAME/.ssh/known_hosts file. (this will completely wipe it and make you have to confirm the first time you ssh again to your machines). If you have special host keys, do not do this.

```
 sudo echo     > /home/USERNAME/.ssh/known_hosts 
```
REMEMBER TO CHANGE YOUR USERNAME

---

### Post by Cyked on 2009-03-07
I noticed that I did not do sudo when restarting ssh.  When i do it with sudo i dont get the error i was before.

at any rate, after doing what you suggested i am still having the issue.

---

### Post by Kareeser on 2009-03-07
Do you have physical access to the machine?

If so, run this command on the machine itself:

```
ssh 127.0.0.1
```

If this works, then the ssh server is functioning according to spec. At this point, I'd blame iptables or a port forwarding problem on the outgoing router.

---

### Post by Cyked on 2009-03-07
ill try it.  im working inside the router now, going from .101 to .102 when it wasnt working (as well as from work).

---

### Post by rhcm123 on 2009-03-07
> **Cyked said:**
> ill try it.  im working inside the router now, going from .101 to .102 when it wasnt working (as well as from work).

Also try ssh-ing from the machine having issues to another computer... it might be that is something blocking it.

this also means that because you were not sudoing the restart command that your RSA and DSA keys were probably fine, just unreadable by everybody except root

---

### Post by Slim Odds on 2009-03-07
> **rhcm123 said:**
> Well that answers it pretty simply. You somehow deleted your RSA & DSA keys. (Quickly googles how to fix this :) )

Alrighy, do this:
```
sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
```Then this:
```
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
```

Probably be easier to just reinstall the openssh-server. It generates the keys automatically during install.

---

### Post by rhcm123 on 2009-03-07
> **Slim Odds said:**
> Probably be easier to just reinstall the openssh-server. It generates the keys automatically during install.

Or you can keep using the same server and just make new keys? :) Is it simpler to change a lock or to get a new door?

---

### Post by Slim Odds on 2009-03-07
> **rhcm123 said:**
> Or you can keep using the same server and just make new keys? :) Is it simpler to change a lock or to get a new door?

Software is not hardware   ;)

---

### Post by Cyked on 2009-03-07
> **Kareeser said:**
> Do you have physical access to the machine?

If so, run this command on the machine itself:

```
ssh 127.0.0.1
```

If this works, then the ssh server is functioning according to spec. At this point, I'd blame iptables or a port forwarding problem on the outgoing router.

that worked fine.  I uninstalled ssh and restarted the service.  The port i was using prev. is still the same.  i connected from an outside source and am still getting error connection refused on the correct ssh port being used, and connection timeout error when using port 22.  Something is still jacked up like the port is listening for the connection, but the system has no idea what to do with it so its refused.  is there a file somewhere that the iptables might have been saved I need to clear?

---

### Post by rhcm123 on 2009-03-07
> **Slim Odds said:**
> Software is not hardware   ;)

by server i meant ssh-server

---

### Post by Kareeser on 2009-03-07
oh heck. I'm on rhcm123's side, just for kicks...

If you REALLY get down to the fine FINE details... regenerating the RSA and DSA keys is more environmentally friendly, as you won't tax your processor/ethernet card as much as if you were removing and reinstalling the server ;)

---

### Post by Cyked on 2009-03-07
Not sure if this will help, my auth.log seems really screwy....  not sure why there is nothing in it before 3/6 20:17.

```
Mar  6 20:09:01 tux CRON[6811]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 20:17:01 tux CRON[6909]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 20:39:01 tux CRON[7175]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 20:59:02 tux sshd[7419]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  6 21:09:01 tux CRON[7542]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 21:17:01 tux CRON[7641]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 21:39:01 tux CRON[7906]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 22:09:01 tux CRON[8270]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 22:17:01 tux CRON[8368]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 22:39:01 tux CRON[8633]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 23:09:01 tux CRON[8996]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 23:17:01 tux CRON[9094]: pam_unix(cron:account): account root has expired (account expired)
Mar  6 23:39:01 tux CRON[9359]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 00:09:01 tux CRON[9722]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 00:17:01 tux CRON[9820]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 00:39:01 tux CRON[10085]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 01:09:01 tux CRON[10448]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 01:17:01 tux CRON[10546]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 01:39:01 tux CRON[10811]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 02:09:01 tux CRON[11174]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 02:17:01 tux CRON[11272]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 02:39:01 tux CRON[11537]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 03:09:01 tux CRON[11900]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 03:17:01 tux CRON[11998]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 03:39:01 tux CRON[12263]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 04:09:01 tux CRON[12626]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 04:17:01 tux CRON[12724]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 04:39:01 tux CRON[12989]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 05:09:01 tux CRON[13352]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 05:17:01 tux CRON[13450]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 05:39:01 tux CRON[13715]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 06:09:01 tux CRON[14078]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 06:17:01 tux CRON[14176]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 06:25:01 tux CRON[14273]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 06:39:01 tux CRON[14442]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 07:09:01 tux CRON[14805]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 07:17:01 tux CRON[14903]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 07:30:01 tux CRON[15060]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 07:39:01 tux CRON[15169]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 08:09:01 tux CRON[15532]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 08:17:01 tux CRON[15776]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 08:39:01 tux CRON[16084]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 09:09:01 tux CRON[16448]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 09:17:01 tux CRON[16546]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 09:39:01 tux CRON[16813]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 10:09:01 tux CRON[17175]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 10:17:01 tux CRON[17273]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 10:39:01 tux CRON[17539]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 11:02:46 tux sshd[17843]: error writing /proc/self/oom_adj: Permission denied
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 1025 on :: failed: Address already in use.
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 1025 on 0.0.0.0 failed: Address already in use.
Mar  7 11:02:46 tux sshd[17843]: fatal: Cannot bind any address.
Mar  7 11:04:05 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 11:06:02 tux sshd[17930]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:09:01 tux CRON[17969]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 11:17:01 tux CRON[18067]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 11:39:01 tux CRON[18335]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 11:44:06 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
Mar  7 11:44:24 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
Mar  7 11:45:03 tux sshd[18415]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:45:29 tux sshd[18421]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:46:12 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/bin/echo
Mar  7 11:46:22 tux sshd[18434]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:46:37 tux sshd[18454]: error writing /proc/self/oom_adj: Permission denied
Mar  7 11:46:37 tux sshd[18454]: error: Bind to port 1025 on :: failed: Address already in use.
Mar  7 11:46:38 tux sshd[18454]: error: Bind to port 1025 on 0.0.0.0 failed: Address already in use.
Mar  7 11:46:38 tux sshd[18454]: fatal: Cannot bind any address.
Mar  7 11:46:47 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh restart
Mar  7 11:46:47 tux sshd[4770]: Received signal 15; terminating.
Mar  7 11:46:47 tux sshd[18476]: Server listening on :: port 1025.
Mar  7 11:46:47 tux sshd[18476]: Server listening on 0.0.0.0 port 1025.
Mar  7 11:46:55 tux sshd[18482]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:48:39 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh stop
Mar  7 11:48:39 tux sshd[18476]: Received signal 15; terminating.
Mar  7 11:49:06 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/bin/echo
Mar  7 11:49:13 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
Mar  7 11:49:22 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
Mar  7 11:50:51 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh start
Mar  7 11:50:51 tux sshd[18593]: Server listening on :: port 1025.
Mar  7 11:50:51 tux sshd[18593]: Server listening on 0.0.0.0 port 1025.
Mar  7 11:51:15 tux sshd[18602]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:52:45 tux sshd[18650]: error writing /proc/self/oom_adj: Permission denied
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 1025 on :: failed: Address already in use.
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 1025 on 0.0.0.0 failed: Address already in use.
Mar  7 11:52:45 tux sshd[18650]: fatal: Cannot bind any address.
Mar  7 11:54:12 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/sbin/dpkg-reconfigure openssh-server
Mar  7 11:54:13 tux sshd[18593]: Received signal 15; terminating.
Mar  7 11:54:13 tux sshd[18752]: Server listening on :: port 1025.
Mar  7 11:54:13 tux sshd[18752]: Server listening on 0.0.0.0 port 1025.
Mar  7 11:55:01 tux sshd[18767]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 12:09:01 tux CRON[18939]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 12:17:01 tux CRON[19037]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 12:39:01 tux CRON[19303]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 13:09:01 tux CRON[19666]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 13:17:01 tux CRON[19764]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 13:39:01 tux CRON[20030]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 14:09:01 tux CRON[20395]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 14:17:01 tux CRON[20494]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 14:39:01 tux CRON[20759]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 14:51:48 tux sshd[20915]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost  user=test
Mar  7 14:51:50 tux sshd[20915]: Failed password for test from 127.0.0.1 port 55084 ssh2
Mar  7 14:51:53 tux sshd[20915]: Accepted password for test from 127.0.0.1 port 55084 ssh2
Mar  7 14:51:53 tux sshd[20915]: pam_unix(sshd:session): session opened for user test by (uid=0)
Mar  7 14:51:56 tux sshd[20915]: pam_unix(sshd:session): session closed for user test
Mar  7 14:52:25 tux sshd[21017]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 14:52:59 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables -l
Mar  7 14:53:02 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables -l
Mar  7 14:53:04 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables -L
Mar  7 14:53:05 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables -L
Mar  7 14:56:46 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/etc/init.d/ssh stop
Mar  7 14:56:46 tux sshd[18752]: Received signal 15; terminating.
Mar  7 14:56:50 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/apt-get install ssh
Mar  7 14:59:20 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables-restore
Mar  7 14:59:25 tux sudo:  test : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/sbin/iptables-restore
Mar  7 15:00:08 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/sbin/iptables -
Mar  7 15:00:14 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/sbin/iptables -L
Mar  7 15:02:28 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/apt-get reinstall ssh
Mar  7 15:03:25 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/apt-get remove openssh-server
Mar  7 15:03:48 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/apt-get install ssh
Mar  7 15:04:00 tux sshd[21406]: Server listening on :: port 1025.
Mar  7 15:04:00 tux sshd[21406]: Server listening on 0.0.0.0 port 1025.
Mar  7 15:04:13 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh start
Mar  7 15:04:33 tux sshd[21441]: Accepted password for test from 127.0.0.1 port 57578 ssh2
Mar  7 15:04:33 tux sshd[21441]: pam_unix(sshd:session): session opened for user test by (uid=0)
Mar  7 15:04:36 tux sshd[21441]: pam_unix(sshd:session): session closed for user test
Mar  7 15:04:46 tux sshd[21538]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 15:07:34 tux sshd[21572]: refused connect from 67.159.137.225 (67.159.137.225)
Mar  7 15:09:01 tux CRON[21591]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 15:17:01 tux CRON[21704]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 15:17:42 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/apt-get remove denyhosts
Mar  7 15:18:55 tux sshd[21764]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 15:19:06 tux sshd[21768]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 15:39:01 tux CRON[22009]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 16:09:01 tux CRON[22374]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 16:17:01 tux CRON[22472]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 16:39:01 tux CRON[22737]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 16:50:17 tux sudo: pam_unix(sudo:auth): authentication failure; logname=test uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=test
Mar  7 16:50:22 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh stop
Mar  7 16:50:22 tux sshd[21406]: Received signal 15; terminating.
Mar  7 16:50:40 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/bin/rm /etc/ssh/ssh_host_dsa_key /etc/ssh/ssh_host_dsa_key.pub /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_rsa_key.pub
Mar  7 16:50:52 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/bin/rm /etc/ssh/ssh_host_*
Mar  7 16:51:13 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/sbin/dpkg-reconfigure openssh-server
Mar  7 16:51:17 tux sshd[22990]: Server listening on :: port 1025.
Mar  7 16:51:17 tux sshd[22990]: Server listening on 0.0.0.0 port 1025.
Mar  7 16:52:59 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/bin/rm .ssh/known_hosts
Mar  7 16:53:51 tux sshd[23035]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 16:56:55 tux sudo:  test : TTY=pts/0 ; PWD=/home/test ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-blacklist
Mar  7 16:58:19 tux sudo:  test : TTY=pts/0 ; PWD=/home/test ; USER=root ; COMMAND=/usr/bin/ssh-vulnkey
Mar  7 17:01:25 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh stop
Mar  7 17:01:26 tux sshd[22990]: Received signal 15; terminating.
Mar  7 17:01:30 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/etc/init.d/ssh start
Mar  7 17:01:31 tux sshd[23211]: Server listening on :: port 1025.
Mar  7 17:01:31 tux sshd[23211]: Server listening on 0.0.0.0 port 1025.
Mar  7 17:01:41 tux sshd[23217]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:03:45 tux sshd[23244]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:04:23 tux sshd[23252]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:09:01 tux CRON[23391]: pam_unix(cron:account): account root has expired (account expired)
Mar  7 17:10:06 tux sudo:  test : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/nano /var/log/auth.log
```

Should it say server listening on 0.0.0.0 for my ssh port?

---

### Post by rhcm123 on 2009-03-07
> **Cyked said:**
> 
Should it say server listening on 0.0.0.0 for my ssh port?

No, and that's your problem. It's not listening on a valid address.
Change your sshd.conf to look like this:

```

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress <YOUR STATIC IP (e.g. 192.168.2.150)
Protocol 2


```

---

### Post by Cyked on 2009-03-07
i changed it to the static IP with no change. i changed it 127.0.0.1 and now getting connection refused.  i restarted ssh after each change. also when i checked it the line was commented out.

The only other thing I was doing yesteday was adding entries to iptables.  Obviously i didnt add my internal IP address.  I have stopped, and even removed denyhosts, so that shouldnt be affecting either.

---

### Post by rhcm123 on 2009-03-07
> **Cyked said:**
> i changed it to the static IP with no change. i changed it 127.0.0.1 and now getting connection refused.  i restarted ssh after each change. also when i checked it the line was commented out.

The only other thing I was doing yesteday was adding entries to iptables.  Obviously i didnt add my internal IP address.  I have stopped, and even removed denyhosts, so that shouldnt be affecting either.

Make sure that the line is not commented out. Also, after changing it to your server's static ip, restart networking

---

### Post by Cyked on 2009-03-07
No dice.  Still getting "server unexpected closed network connection".

Well I narrowed something down. I can't connect from a machine outside my network (not work), and I can't connect internally from my windows box.  BUT, I can connect from my work laptop from inside the network.

---

### Post by Cyked on 2009-03-07
It seems denyhosts is still screwing with something even though I removed it.  So I get get in through ssh from my windows machine now.

Any ideas why this happened?

---

### Post by rhcm123 on 2009-03-09
> **Cyked said:**
> It seems denyhosts is still screwing with something even though I removed it.  So I get get in through ssh from my windows machine now.

Any ideas why this happened?

Check ufw, iptables, and denyhosts. If nessecary, backup your configureation and run sudo apt-get --purge remove to try and kill it.

---

### Post by Cyked on 2009-03-09
I removed denyhosts and deleted files associated with it (hosts.deny, .allow, etc).  iptables is empty, so unless there is some file somewhere that keeps a copy, idk....

> sudo apt-get --purge remove to try and kill it.  
Which are you referring to here, denyhosts?

---

### Post by Cyked on 2009-03-09
Here is the auth log from the past few days after playing around with the 

```
Mar  6 20:59:02 tux sshd[7419]: refused connect from 192.168.1.101 (192.168.1.101)
_Mar  7 11:02:46 tux sshd[17843]: error writing /proc/self/oom_adj: Permission denied_
_Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22on :: failed: Address already in use._
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22on 0.0.0.0 failed: Address already in use.
Mar  7 11:02:46 tux sshd[17843]: fatal: Cannot bind any address.
Mar  7 11:04:05 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 11:06:02 tux sshd[17930]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:45:03 tux sshd[18415]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:45:29 tux sshd[18421]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:46:22 tux sshd[18434]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:46:37 tux sshd[18454]: error writing /proc/self/oom_adj: Permission denied
Mar  7 11:46:37 tux sshd[18454]: error: Bind to port 22on :: failed: Address already in use.
Mar  7 11:46:38 tux sshd[18454]: error: Bind to port 22on 0.0.0.0 failed: Address already in use.
Mar  7 11:46:38 tux sshd[18454]: fatal: Cannot bind any address.
Mar  7 11:46:47 tux sshd[4770]: Received signal 15; terminating.
Mar  7 11:46:47 tux sshd[18476]: Server listening on :: port 22.
Mar  7 11:46:47 tux sshd[18476]: Server listening on 0.0.0.0 port 22.
Mar  7 11:46:55 tux sshd[18482]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:48:39 tux sshd[18476]: Received signal 15; terminating.
Mar  7 11:50:51 tux sshd[18593]: Server listening on :: port 22.
Mar  7 11:50:51 tux sshd[18593]: Server listening on 0.0.0.0 port 22.
Mar  7 11:51:15 tux sshd[18602]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 11:52:45 tux sshd[18650]: error writing /proc/self/oom_adj: Permission denied
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22on :: failed: Address already in use.
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22on 0.0.0.0 failed: Address already in use.
Mar  7 11:52:45 tux sshd[18650]: fatal: Cannot bind any address.
Mar  7 11:54:13 tux sshd[18593]: Received signal 15; terminating.
Mar  7 11:54:13 tux sshd[18752]: Server listening on :: port 22.
Mar  7 11:54:13 tux sshd[18752]: Server listening on 0.0.0.0 port 22.
Mar  7 11:55:01 tux sshd[18767]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 14:51:48 tux sshd[20915]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost  user=loginid
Mar  7 14:51:50 tux sshd[20915]: Failed password for loginid from 127.0.0.1 port 55084 ssh2
Mar  7 14:51:53 tux sshd[20915]: Accepted password for loginid from 127.0.0.1 port 55084 ssh2
Mar  7 14:51:53 tux sshd[20915]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 14:51:56 tux sshd[20915]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 14:52:25 tux sshd[21017]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 14:56:46 tux sshd[18752]: Received signal 15; terminating.
Mar  7 15:04:00 tux sshd[21406]: Server listening on :: port 22.
Mar  7 15:04:00 tux sshd[21406]: Server listening on 0.0.0.0 port 22.
Mar  7 15:04:33 tux sshd[21441]: Accepted password for loginid from 127.0.0.1 port 57578 ssh2
Mar  7 15:04:33 tux sshd[21441]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 15:04:36 tux sshd[21441]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 15:04:46 tux sshd[21538]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 15:07:34 tux sshd[21572]: refused connect from 67.159.x.x (67.159.x.x)
Mar  7 15:18:55 tux sshd[21764]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 15:19:06 tux sshd[21768]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 16:50:22 tux sshd[21406]: Received signal 15; terminating.
Mar  7 16:51:17 tux sshd[22990]: Server listening on :: port 22.
Mar  7 16:51:17 tux sshd[22990]: Server listening on 0.0.0.0 port 22.
Mar  7 16:53:51 tux sshd[23035]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:01:26 tux sshd[22990]: Received signal 15; terminating.
Mar  7 17:01:31 tux sshd[23211]: Server listening on :: port 22.
Mar  7 17:01:31 tux sshd[23211]: Server listening on 0.0.0.0 port 22.
Mar  7 17:01:41 tux sshd[23217]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:03:45 tux sshd[23244]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:04:23 tux sshd[23252]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:23:14 tux sshd[23211]: Received signal 15; terminating.
Mar  7 17:23:15 tux sshd[23683]: Server listening on :: port 22.
Mar  7 17:23:15 tux sshd[23683]: Server listening on 0.0.0.0 port 22.
Mar  7 17:23:30 tux sshd[23691]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:24:13 tux sshd[23701]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:24:48 tux sshd[23709]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 17:25:38 tux sshd[23720]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:10:47 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:11:33 tux sshd[23683]: Received signal 15; terminating.
Mar  7 18:11:33 tux sshd[24334]: Server listening on :: port 22.
Mar  7 18:11:33 tux sshd[24334]: Server listening on 0.0.0.0 port 22.
Mar  7 18:11:41 tux sshd[24340]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:11:53 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:12:04 tux sshd[24334]: Received signal 15; terminating.
Mar  7 18:12:04 tux sshd[24363]: Server listening on 192.168.1.102 port 22.
Mar  7 18:12:10 tux sshd[24369]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:13:33 tux sshd[24363]: Received signal 15; terminating.
Mar  7 18:13:33 tux sshd[24414]: Server listening on 192.168.1.102 port 22.
Mar  7 18:13:58 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:14:10 tux sshd[24414]: Received signal 15; terminating.
Mar  7 18:14:10 tux sshd[24449]: Server listening on 127.0.0.1 port 22.
Mar  7 18:15:37 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:15:50 tux sshd[24449]: Received signal 15; terminating.
Mar  7 18:15:50 tux sshd[24497]: Server listening on 192.168.1.102 port 22.
Mar  7 18:15:58 tux sshd[24504]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:26:49 tux sshd[24497]: Received signal 15; terminating.
Mar  7 18:26:49 tux sshd[24682]: Server listening on 192.168.1.102 port 22.
Mar  7 18:26:54 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:43:07 tux sshd[24682]: Received SIGHUP; restarting.
Mar  7 18:43:07 tux sshd[25003]: Server listening on 192.168.1.102 port 22.
Mar  7 18:43:12 tux sshd[25003]: Received signal 15; terminating.
Mar  7 18:43:12 tux sshd[25037]: Server listening on 192.168.1.102 port 22.
Mar  7 18:43:23 tux sshd[25043]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:43:43 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:43:51 tux sshd[25037]: Received signal 15; terminating.
Mar  7 18:43:51 tux sshd[25069]: Server listening on :: port 22.
Mar  7 18:43:51 tux sshd[25069]: Server listening on 0.0.0.0 port 22.
Mar  7 18:43:53 tux sshd[25069]: Received SIGHUP; restarting.
Mar  7 18:43:53 tux sshd[25177]: Server listening on :: port 22.
Mar  7 18:43:53 tux sshd[25177]: Server listening on 0.0.0.0 port 22.
Mar  7 18:44:01 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/init.d ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  7 18:44:38 tux sshd[25200]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost  user=loginid 
Mar  7 18:44:40 tux sshd[25200]: Failed password for loginid from 127.0.0.1 port 40561 ssh2
Mar  7 18:44:42 tux sshd[25200]: Accepted password for loginid from 127.0.0.1 port 40561 ssh2
Mar  7 18:44:42 tux sshd[25200]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 18:44:44 tux sshd[25200]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 18:46:23 tux sshd[25177]: Received signal 15; terminating.
Mar  7 18:46:23 tux sshd[25339]: Server listening on 192.168.1.102 port 22.
Mar  7 18:46:25 tux sshd[25339]: Received SIGHUP; restarting.
Mar  7 18:46:25 tux sshd[25447]: Server listening on 192.168.1.102 port 22.
Mar  7 18:48:07 tux sshd[25485]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=tux.local  user=loginid 
Mar  7 18:48:09 tux sshd[25485]: Failed password for loginid from 192.168.1.102 port 39648 ssh2
Mar  7 18:48:11 tux sshd[25485]: Accepted password for loginid from 192.168.1.102 port 39648 ssh2
Mar  7 18:48:11 tux sshd[25485]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 18:48:12 tux sshd[25485]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 18:48:20 tux sshd[25583]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 18:50:21 tux sshd[25614]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 19:00:35 tux sshd[25741]: refused connect from 192.168.1.101 (192.168.1.101)
Mar  7 19:02:43 tux sshd[25767]: Accepted password for loginid from 192.168.1.108 port 1111 ssh2
Mar  7 19:02:43 tux sshd[25767]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 19:09:38 tux sshd[25905]: Accepted password for loginid from 192.168.1.101 port 3872 ssh2
Mar  7 19:09:38 tux sshd[25905]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 19:09:41 tux sshd[25905]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 19:22:48 tux sshd[26228]: Accepted password for loginid from 192.168.1.101 port 4163 ssh2
Mar  7 19:22:48 tux sshd[26228]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
Mar  7 19:23:12 tux sshd[26228]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 19:24:21 tux sshd[25767]: pam_unix(sshd:session): session closed for user loginid 
Mar  7 19:25:32 tux sshd[4765]: Server listening on 192.168.1.102 port 22.
Mar  7 21:34:06 tux sudo:  loginid : TTY=pts/0 ; PWD=/etc/ssh ; USER=root ; COMMAND=/usr/bin/nano /etc/ssh/sshd_config
Mar  9 08:46:18 tux sshd[31145]: Accepted password for loginid from 209.36.x.x port 4674 ssh2
Mar  9 08:46:18 tux sshd[31145]: pam_unix(sshd:session): session opened for user loginid by (uid=0)
```


Other n00b question.  Why when there is an accept for login for ssh it reads.... "Accepted password for loginid from 192.168.1.101 port 3872 ssh2"..... What's with the port 3872, 4674, etc... why is it that that number seems to be random?

---

### Post by Cyked on 2009-03-10
I hate doing this normally, but... bump

---

### Post by bodhi.zazen on 2009-03-10
If you were using denyhosts you need to clear your ip address(es) form 

/etc/hosts.deny

If that does not fix your problem , output of 

```
sudo iptables -L -v
```

---

### Post by Cyked on 2009-03-10
> **bodhi.zazen said:**
> If you were using denyhosts you need to clear your ip address(es) form 

/etc/hosts.deny

If that does not fix your problem , output of 

```
sudo iptables -L -v
```

Sorry if it was not clear, the issue is resolved at this point, I'm just looking for an answer to WTF happened.

To resolve I cleared the contents of denyhosts, ultimately I ended up removing the hosts.deny file and everything starting working again.  My question is, why did denyhosts become an issue again since I have not had that service running, and STILL had issues using SSH after rebooting AND stopping denyhosts?


iptables is empty right now since the tables were not saved because of the reboot.

---

### Post by Cyked on 2009-03-10
Finding something new now as well.....

I found this on the forums:
[http://ubuntuforums.org/showthread.php?p=6450387](http://ubuntuforums.org/showthread.php?p=6450387)


I'm seeing something similar when greping auth.log 
If I do cat /var/log/auth.log | grep failed I get this:

```
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 1025 on 0.0.0.0 failed: Address already in use.
Mar  7 21:28:42 tux gdm[5175]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.

```

If I simply grep for ssh it works fine, though I am seeing the same error output if I grep for other words in that log file.  I'm fairly certain greping for "failed" worked previous to this snafu.

---

### Post by rhcm123 on 2009-03-11
> **Cyked said:**
> Finding something new now as well.....

I found this on the forums:
[http://ubuntuforums.org/showthread.php?p=6450387](http://ubuntuforums.org/showthread.php?p=6450387)


I'm seeing something similar when greping auth.log 
If I do cat /var/log/auth.log | grep failed I get this:

```
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 1025 on 0.0.0.0 failed: Address already in use.
Mar  7 21:28:42 tux gdm[5175]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.

```

If I simply grep for ssh it works fine, though I am seeing the same error output if I grep for other words in that log file.  I'm fairly certain greping for "failed" worked previous to this snafu.

Could you grep for "error" (without the quotes) and also, according to the error log you dumped, your session bus isn't starting. dbus is used for ssh (among other things). For instance, when you log in you start up the dbus-daemon. Each ssh session starts up dbus. It appears it is not listening on any appropriate port/protocol. Open up session.conf (that's what it's called in fedora, it's usally in either /etc/X11/Xsession.d/75dbus_dbus-launch, or you can write your own and specifiy it with a command)

---

### Post by Cyked on 2009-03-12
Here is what I get when grepping error.  Since it is all from the 7th does that mean it is no longer an issue?

```
Mar  7 11:02:46 tux sshd[17843]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 11:46:37 tux sshd[18454]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:46:37 tux sshd[18454]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:46:38 tux sshd[18454]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 11:52:45 tux sshd[18650]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.

```


Also, from what I got out of checking the 75dbus file, i went to look at /X11/Xsessions.options, and use-session-dbus is in there.  I think I'm good now since I am only see these errors from the 7th and nothing new.  

Hopefully I am not wrong in the assumption :)

---

### Post by rhcm123 on 2009-03-19
> **Cyked said:**
> Here is what I get when grepping error.  Since it is all from the 7th does that mean it is no longer an issue?

```
Mar  7 11:02:46 tux sshd[17843]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:02:46 tux sshd[17843]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 11:46:37 tux sshd[18454]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:46:37 tux sshd[18454]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:46:38 tux sshd[18454]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 11:52:45 tux sshd[18650]: error writing /proc/self/oom_adj: Permission de                                             nied
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22 on :: failed: Address                                              already in use.
Mar  7 11:52:45 tux sshd[18650]: error: Bind to port 22 on 0.0.0.0 failed: Add                                             ress already in use.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.
Mar  7 21:28:42 tux gdm[5175]: Autolaunch error: X11 initialization failed.

```


Also, from what I got out of checking the 75dbus file, i went to look at /X11/Xsessions.options, and use-session-dbus is in there.  I think I'm good now since I am only see these errors from the 7th and nothing new.  

Hopefully I am not wrong in the assumption :)

Alright cool. Just one quick question. When you start the sshd, do you use "sudo /etc/init.d/sshd restart" or no sudo?

---

### Post by Cyked on 2009-03-20
I'm using sudo /etc/init.d/ssh restart
If I do sshd I get cmd not found.  If I do not use sudo I get errors about not being able to load host keys.

---

### Post by rhcm123 on 2009-03-21
> **Cyked said:**
> I'm using sudo /etc/init.d/ssh restart
If I do sshd I get cmd not found.  If I do not use sudo I get errors about not being able to load host keys.

ok
i've had people have this entire problem because they tried to restart without sudo (always funny when they figure that out)

---

### Post by Cyked on 2009-03-21
sshd is just the openssh version, correct?

---

### Post by rhcm123 on 2009-03-21
> **Cyked said:**
> sshd is just the openssh version, correct?
yeah, but you restart it with /etc/init.d/ssh

---

### Post by Cyked on 2009-03-22
> **rhcm123 said:**
> yeah, but you restart it with /etc/init.d/ssh

Right.  

Thanks again!  I appreciate it.

---

### Post by rhcm123 on 2009-03-22
> **Cyked said:**
> Right.  

Thanks again!  I appreciate it.

no problems

---

