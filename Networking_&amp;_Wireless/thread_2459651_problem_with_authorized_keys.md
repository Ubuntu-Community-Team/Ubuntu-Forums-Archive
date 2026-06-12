---
title: "problem with authorized_keys"
date: 2021-03-22
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-03-22
I have two servers at one location and I want to set up an offsite server to clone their data as a safety measure. 
To do that I want to set up ssh keys to allow for secure remote access.
I set one up and copied the key from the remote machine and installed it in the ~/.ssh/authorized_keys file it worked perfectly. I can now access that server without a password prompt.
I did the exact same thing on the other server and the ~/.ssh/authorized_keys file is the same except the second server keeps prompting for a password and no password works.
I've obviously overlooked something but I don't know what.
~/.ssh has 700 permissions and authorized_keys has 600 permissions on both servers, the key in the file is identical.

In the auth.log I see these messages:

```
Mar 22 00:11:11 thelma sshd[605]: rexec line 14: Deprecated option UsePrivilegeSeparation
Mar 22 00:11:11 thelma sshd[605]: rexec line 17: Deprecated option KeyRegenerationInterval
Mar 22 00:11:11 thelma sshd[605]: rexec line 18: Deprecated option ServerKeyBits
Mar 22 00:11:11 thelma sshd[605]: rexec line 30: Deprecated option RSAAuthentication
Mar 22 00:11:11 thelma sshd[605]: rexec line 37: Deprecated option RhostsRSAAuthentication
Mar 22 00:11:13 thelma sshd[605]: reprocess config line 30: Deprecated option RSAAuthentication
Mar 22 00:11:13 thelma sshd[605]: reprocess config line 37: Deprecated option RhostsRSAAuthentication
Mar 22 00:11:13 thelma sshd[764]: pam_unix(sshd:auth): authentication failure;
```
The configuration files on the first working server include:

```

# ls -ld *
-rw-r--r-- 1 root root 535195 May 29  2020 moduli
-rw-r--r-- 1 root root   1603 May 29  2020 ssh_config
drwxr-xr-x 2 root root   4096 May 29  2020 ssh_config.d
-rw-r--r-- 1 root root   3289 May 29  2020 sshd_config
drwxr-xr-x 2 root root   4096 May 29  2020 sshd_config.d
-rw-r--r-- 1 root root   3249 Feb 23  2019 sshd_config.ucf-dist
-rw-r--r-- 1 root root   1885 Jul 10  2020 sshd_config.ucf-old
-rw------- 1 root root    668 Mar 23  2007 ssh_host_dsa_key
-rw-r--r-- 1 root root    601 Mar 23  2007 ssh_host_dsa_key.pub
-rw------- 1 root root    505 Feb  5 16:46 ssh_host_ecdsa_key
-rw-r--r-- 1 root root    173 Feb  5 16:46 ssh_host_ecdsa_key.pub
-rw------- 1 root root    399 Feb  5 16:46 ssh_host_ed25519_key
-rw-r--r-- 1 root root     93 Feb  5 16:46 ssh_host_ed25519_key.pub
-rw------- 1 root root   1675 Mar 23  2007 ssh_host_rsa_key
-rw-r--r-- 1 root root    393 Mar 23  2007 ssh_host_rsa_key.pub
-rw-r--r-- 1 root root    342 Feb 28  2020 ssh_import_id
```

The configuration on the second nonworking server is different and much older.

```

-rw-r--r-- 1 root root 553122 Jan 31  2019 moduli
-rw-r--r-- 1 root root   1580 Jan 31  2019 ssh_config
-rw-r--r-- 1 root root   1910 Jul 10  2020 sshd_config
-rw-r--r-- 1 root root   3264 Jan 31  2019 sshd_config.ucf-dist
-rw------- 1 root root    668 Mar 23  2007 ssh_host_dsa_key
-rw-r--r-- 1 root root    601 Mar 23  2007 ssh_host_dsa_key.pub
-rw------- 1 root root   1675 Mar 23  2007 ssh_host_rsa_key
-rw-r--r-- 1 root root    393 Mar 23  2007 ssh_host_rsa_key.pub
-rw-r--r-- 1 root root    338 Mar  2  2019 ssh_import_id
```

The first server is running 20.4.2 LTS
The second is still running 18.04.5 LTS

My understanding is that a Depreciated option should still work, but may be removed in the future. So I'm not sure if I should go in and edit the /etc/ssh/sshd_config file  or if that will solve the problem. Apparently when I do upgrade the second server the ssh config files will be replaced.

---

### Post by TheFu on 2021-03-23
Check for differences in the sshd_config file - I'd use **meld** for that. Just copy both files to your workstation somewhere - perhaps /tmp/ and do the compare. sdiff or diff can be used, but meld is really nice.

It would be very helpful if you clearly showed what directories are being displayed.
```
# ls -ld *
```
isn't exactly helpful, though I'm not sure what this has to do with it.  There are 2 config files that matter in /etc/ssh/. Those are the server daemon config, sshd_config and the default client config, ssh_config.  Since client configs should be per-userid and go into ~/.ssh/config, without knowing which userid is running the ssh commands and knowing that the keys were generated and pushed from that client to the server system, I'll just have to be confused.

Client is the machine running the **ssh userid@remote** command. It has nothing to do with location.  
Server machine is "remote" which a client ssh command (or scp, sftp, rsync, sshfs, vim, rdiff-backup, rsnapshot, rbackup, x2go .....) would be targeted towards.

Using **ssh-copy-id** to push ssh keys from the client to the server prevents human errors caused by manual copy efforts. Don't manually copy them, unless you are on Windows which doesn't have ssh-copy-id.

---

### Post by rsteinmetz70112 on 2021-03-24
> **TheFu said:**
> Check for differences in the sshd_config file - I'd use **meld** for that. Just copy both files to your workstation somewhere - perhaps /tmp/ and do the compare. sdiff or diff can be used, but meld is really nice.

It would be very helpful if you clearly showed what directories are being displayed.
```
# ls -ld *
```
isn't exactly helpful, though I'm not sure what this has to do with it.  

The two lists are the /etc/ssh files on the two computers. I included it to show they were different, the primary difference is the configuration directories but they are empty.
I ran diff on the two ~/.ssh/authorized_keys files and confirmed they were the same.
I ran diff on the /etc/ssh/sshd_config - the result is below:

```
< # Package generated configuration file
< # See the sshd(8) manpage for details
---
> #     $OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $
4,7c3,16
< # What ports, IPs and protocols we listen for
< Port 22
< # Use these options to restrict which interfaces/protocols sshd will bind to
< #ListenAddress ::
---
> # This is the sshd server system-wide configuration file.  See
> # sshd_config(5) for more information.
>
> # This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin
>
> # The strategy used for options in the default sshd_config shipped with
> # OpenSSH is to specify options with their default value where
> # possible, but leave them commented.  Uncommented options override the
> # default value.
>
> Include /etc/ssh/sshd_config.d/*.conf
>
> #Port 22
> #AddressFamily any
9,18c18,25
< Protocol 2
< # HostKeys for protocol version 2
< HostKey /etc/ssh/ssh_host_rsa_key
< HostKey /etc/ssh/ssh_host_dsa_key
< #Privilege Separation is turned on for security
< UsePrivilegeSeparation yes
<
< # Lifetime and size of ephemeral version 1 server key
< KeyRegenerationInterval 3600
< ServerKeyBits 1024
---
> #ListenAddress ::
>
> #HostKey /etc/ssh/ssh_host_rsa_key
> #HostKey /etc/ssh/ssh_host_ecdsa_key
> #HostKey /etc/ssh/ssh_host_ed25519_key
>
> # Ciphers and keying
> #RekeyLimit default none
21,22c28,29
< SyslogFacility AUTH
< LogLevel INFO
---
> #SyslogFacility AUTH
> #LogLevel INFO
25,32d31
< LoginGraceTime 120
< PermitRootLogin prohibit-password
< #PermitRootLogin yes
< StrictModes yes
<
< RSAAuthentication yes
< PubkeyAuthentication yes
< #AuthorizedKeysFile   %h/.ssh/authorized_keys
33a33,53
> #LoginGraceTime 2m
> #PermitRootLogin prohibit-password
> #StrictModes yes
> #MaxAuthTries 6
> #MaxSessions 10
>
> #PubkeyAuthentication yes
>
> # Expect .ssh/authorized_keys2 to be disregarded by default in future.
> #AuthorizedKeysFile   .ssh/authorized_keys .ssh/authorized_keys2
>
> #AuthorizedPrincipalsFile none
>
> #AuthorizedKeysCommand none
> #AuthorizedKeysCommandUser nobody
>
> # For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
> #HostbasedAuthentication no
> # Change to yes if you don't trust ~/.ssh/known_hosts for
> # HostbasedAuthentication
> #IgnoreUserKnownHosts no
35,41c55
< IgnoreRhosts yes
< # For this to work you will also need host keys in /etc/ssh_known_hosts
< RhostsRSAAuthentication no
< # similar for protocol version 2
< HostbasedAuthentication no
< # Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
< #IgnoreUserKnownHosts yes
---
> #IgnoreRhosts yes
43,44c57,59
< # To enable empty passwords, change to yes (NOT RECOMMENDED)
< PermitEmptyPasswords yes
---
> # To disable tunneled clear text passwords, change to no here!
> #PasswordAuthentication yes
> #PermitEmptyPasswords no
50,52d64
< # Change to no to disable tunnelled clear text passwords
< PasswordAuthentication yes
<
55d66
< #KerberosGetAFSToken no
57a69
> #KerberosGetAFSToken no
61a74,75
> #GSSAPIStrictAcceptorCheck yes
> #GSSAPIKeyExchange no
62a77,90
> # Set this to 'yes' to enable PAM authentication, account processing,
> # and session processing. If this is enabled, PAM authentication will
> # be allowed through the ChallengeResponseAuthentication and
> # PasswordAuthentication.  Depending on your PAM configuration,
> # PAM authentication via ChallengeResponseAuthentication may bypass
> # the setting of "PermitRootLogin without-password".
> # If you just want the PAM account and session checks to run without
> # PAM authentication, then enable this but set PasswordAuthentication
> # and ChallengeResponseAuthentication to 'no'.
> UsePAM yes
>
> #AllowAgentForwarding yes
> #AllowTcpForwarding yes
> #GatewayPorts no
64c92,94
< X11DisplayOffset 10
---
> #X11DisplayOffset 10
> #X11UseLocalhost yes
> #PermitTTY yes
66,68c96,107
< PrintLastLog yes
< TCPKeepAlive yes
< #UseLogin no
---
> #PrintLastLog yes
> #TCPKeepAlive yes
> #PermitUserEnvironment no
> #Compression delayed
> #ClientAliveInterval 0
> #ClientAliveCountMax 3
> #UseDNS no
> #PidFile /var/run/sshd.pid
> #MaxStartups 10:30:100
> #PermitTunnel no
> #ChrootDirectory none
> #VersionAddendum none
70,71c109,110
< #MaxStartups 10:30:60
< #Banner /etc/issue.net
---
> # no default banner path
> #Banner none
76c115,116

```

I copied the sshd_config from the working machine and used it on the not working machine and I was still prompted for a a password. 

The working machines is  Ubuntu 20.04.2 LTS OpenSSH_8.2p1 Ubuntu-4ubuntu0.2, OpenSSL 1.1.1f  31 Mar 2020
The nonworking one is Ubuntu 18.04.5 LTS OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
The 18.04 is a little odd because the version of ssh is dated prior to the release of 18.04.


> There are 2 config files that matter in /etc/ssh/. Those are the server daemon config, sshd_config and the default client config, ssh_config.  Since client configs should be per-userid and go into ~/.ssh/config, without knowing which userid is running the ssh commands and knowing that the keys were generated and pushed from that client to the server system, I'll just have to be confused.

I'm confused by why it's not working. 
There is no ssh_config in either ~/.ssh/ yet one of the machines works. The only files in the ~/.ssh/ are 

```
-a:~/.ssh# ls -ld *
-rw------- 1 root root  785 Mar 18 22:05 authorized_keys
-rw------- 1 root root 1675 Jul  9  2020 id_rsa
-rw-r--r-- 1 root root  393 Jul  9  2020 id_rsa.pub
-rw-r--r-- 1 root root 3388 Jun 20  2020 known_hosts
```


> Client is the machine running the **ssh userid@remote** command. It has nothing to do with location.  
Server machine is "remote" which a client ssh command (or scp, sftp, rsync, sshfs, vim, rdiff-backup, rsnapshot, rbackup, x2go .....) would be started on.

Using **ssh-copy-id** to push ssh keys from the client to the server prevents human errors caused by manual copy efforts. Don't manually copy them, unless you are on Windows which doesn't have ssh-copy-id.

---

### Post by TheFu on 2021-03-24
Well, the ~/.ssh/authorized_keys for each system should NOT be the same.  Each should have the public key from the other system, assuming you actually want to be able to ssh from each to the other.  That usually isn't required.

> There is no ssh_config in either ~/.ssh/ yet one of the machines works. The only files in the ~/.ssh/ are 
Config files in ~/.ssh/ are optional.  If you want one, create it. It shouldn't look anything like the main one in /etc/ssh/, so don't bother copying that over.  Also, the /etc/ssh/ssh_config ---> ~/.ssh/config - it has a different name.

Why use RSA keys?  

My statement:
> Server machine is "remote" which a client ssh command (or scp, sftp, rsync, sshfs, vim, rdiff-backup, rsnapshot, rbackup, x2go .....) would be started on.
Is incorrect and confusing. Sorry. I don't know what happened.

I think you are having trouble with separating ssh-client and ssh-server from generic client and generic server OR hardware client and hardware server.

A client is the system that initiates the connection to the server.  
The server has a service process listening for client connections.
Say bob is the ssh client and jane is the ssh server. Jane has the ssh-server process running - that happens automatically when the ssh-server package is installed. The name of the server daemon is "sshd" - check the process table for that - or use  **service ssh status** to see it running.
```
bob:~/ $ ssh jane
```
That will make an ssh connection from "bob" to "jane". If no keys can be found correctly exchanged AND configured, then a password will be requested.

Now, if we want jane to ssh into bob, it would be
```
jane:~/ $ ssh bob
```
In this case, bob is the ssh-server, running sshd, and jane is the ssh client.

I've assumed that the usernames on bob and jane are the same, whatever they are.  It is the name, not the uid that matters.

Wrapping your head around which is the client and which is the server can take some getting used to.

[https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386) has details about using more secure ssh-keys and using ssh-copy-id.  If you want bob --> jane   AND jane --> bob, then you'll need to run those 2 commands on each system, just pointing to the opposite system in the ssh-copy-id command.  The ed25519 keys are currently the recommended keys to be used with ssh.

---

### Post by rsteinmetz70112 on 2021-03-25
OK Thanks. I've gotten it working now. I'm not sure exactly what did it. 

I tried a few different /etc/ssh/sshd_config files including the distribution default. Then I discovered that the  permissions on /home/user was 0755 but since since ~/.ssh was 0700 and authorized_keys was 0600, I'm still not sure why or if the permissions on the users home directory has any effect on ssh but I changed its permissions to 0700.

---

### Post by TheFu on 2021-03-25
> **rsteinmetz70112 said:**
> OK Thanks. I've gotten it working now. I'm not sure exactly what did it. 

I tried a few different /etc/ssh/sshd_config files including the distribution default. Then I discovered that the  permissions on /home/user was 0755 but since since ~/.ssh was 0700 and authorized_keys was 0600, I'm still not sure why or if the permissions on the users home directory has any effect on ssh but I changed its permissions to 0700.

Yes, ssh will refuse to work if the ~/.ssh/ directory has the wrong permissions.  Did I mention that using ssh-copy-id was a good idea since to wouldn't screw up stuff that humans commonly get wrong?  ssh was protecting you from yourself.

---

### Post by rsteinmetz70112 on 2021-03-25
> **TheFu said:**
> Yes, ssh will refuse to work if the ~/.ssh/ directory has the wrong permissions.  Did I mention that using ssh-copy-id was a good idea since to wouldn't screw up stuff that humans commonly get wrong?  ssh was protecting you from yourself.

except .ssh was correct. It was the home directory above it that was more open.

---

### Post by TheFu on 2021-03-25
> **rsteinmetz70112 said:**
> except .ssh was correct. It was the home directory above it that was more open.

That doesn't matter.  I have HOMEs with 755, 775, and 770 permissions. It was something else.

---

