---
title: "SSH problem"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-07-26
Hi folks,

server
Ubuntu 7.04 server amd64
(router IP - 192.168.0.11)

workstation
Ubuntu 7.04 desktop i386
(router IP - 192.168.0.12)


Server can connect the workstation and browse remotely with;
$ ssh -Y satimis@192.168.0.12 rox

But workstation can't connect the server with;
$ ssh -Y satimis@192.168.0.11 nano```

ssh: connect to host 192.168.0.11 port 22: Connection refused
```

Server
# cat /etc/ssh/ssh_config```

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
    PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
    Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```


Secondly unable to restart ssh
$ sudo /etc/init.d/ssh restart
Password:
sudo: /etc/init.d/ssh: command not found


$ ls /etc/init.d/ | grep ssh
No printout

$ which ssh
/usr/bin/ssh
ssh is running.


Please help


B.R.
satimis

---

### Post by dreadlord_chris on 2007-07-26
> **satimis said:**
> Hi folks,

server
Ubuntu 7.04 server amd64
(router IP - 192.168.0.11)

workstation
Ubuntu 7.04 desktop i386
(router IP - 192.168.0.12)


Server can connect the workstation and browse remotely with;
$ ssh -Y satimis@192.168.0.12 rox

But workstation can't connect the server with;
$ ssh -Y satimis@192.168.0.11 nano```

ssh: connect to host 192.168.0.11 port 22: Connection refused
```

Server
# cat /etc/ssh/ssh_config```

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
    PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
    Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```


Secondly unable to restart ssh
$ sudo /etc/init.d/ssh restart
Password:
sudo: /etc/init.d/ssh: command not found


$ ls /etc/init.d/ | grep ssh
No printout

$ which ssh
/usr/bin/ssh
ssh is running.


Please help


B.R.
satimis

You need to install the OpenSSH *Server* to get the daemon
```

sudo apt-get install openssh-server

```

---

### Post by satimis on 2007-07-26
> **dreadlord_chris said:**
> You need to install the OpenSSH *Server* to get the daemon
```

sudo apt-get install openssh-server

```
Hi dreadlord_chris,


Tks for your advice.


$ sudo apt-get install openssh-server
went through w/o complaint,

$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                              [ OK ]


On workstation;
$ ssh -Y satimis@192.168.0.11 nano
satimis@192.168.0.11's password:

Error reading /home/satimis/.nano_history:  Permission denied

Press Enter to continue starting nano.

Error opening terminal: unknown.


Server:
$ sudo cat /home/satimis/.nano_history 
```

canonical
cdrom
universe

```


Workstation:
$ sudo cat /home/satimis/.nano_history 
No printout.


Any advice.  TIA


B.R.
satimis

---

### Post by buntunub on 2007-07-26
There is really a wonderful sshfs wiki on the ubuntu wiki. Have a look at it. You need to first setup your server for this to work and it seems  your trying to connect with strange protocalls too.

"$ sudo /etc/init.d/ssh restart
* Restarting OpenBSD Secure Shell server... [ OK ]


On workstation;
$ ssh -Y satimis@192.168.0.11 nano
satimis@192.168.0.11's password:

Error reading /home/satimis/.nano_history: Permission denied

Press Enter to continue starting nano.

Error opening terminal: unknown."

ssh -Y was for MAC's, or so ive heard. I believe what your looking for is

ssh -X satimis@192.168.0.11

OR

ssh satimis@192.168.0.11

See if you can connect with either of those. The -X option will allow you to forward X11 apps over your network server to client, IF your server is setup correctly. Again, there are precisely detailed Wiki's on Ubuntu Wiki that will tell you all you ever could want to know about how to do this for SSH, sshfs, so on and so forth. The easiest way is to use shared rsa keys so that you dont have to worry about passwords for logins too. sshfs allows you to actually setup mountpoints for ssh shares via fuse. For that you will need sshfs and fuse installed and setup and then it simply could not be easier to get working after that, again, that is ONLY if you actually read and follow the posted Wiki's.

---

### Post by dreadlord_chris on 2007-07-26
> **satimis said:**
> Hi dreadlord_chris,


Tks for your advice.


$ sudo apt-get install openssh-server
went through w/o complaint,

$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                              [ OK ]


On workstation;
$ ssh -Y satimis@192.168.0.11 nano
satimis@192.168.0.11's password:

Error reading /home/satimis/.nano_history:  Permission denied

Press Enter to continue starting nano.

Error opening terminal: unknown.


Server:
$ sudo cat /home/satimis/.nano_history 
```

canonical
cdrom
universe

```


Workstation:
$ sudo cat /home/satimis/.nano_history 
No printout.


Any advice.  TIA


B.R.
satimis

does the file /home/satimis/.nano_history exist on the workstation?
```

ls -la /home/satimis/.nano_history

```
if the output of that command is: *No such file or directory* then:
```

touch /home/satimis/.nano_history

```
will probably fix you up...

---

### Post by dreadlord_chris on 2007-07-26
> **buntunub said:**
> ssh -Y was for MAC's, or so ive heard.

-Y is for forwarding *Trusted* X11 connextions

---

### Post by satimis on 2007-07-26
> **buntunub said:**
> There is really a wonderful sshfs wiki on the ubuntu wiki. Have a look at it. You need to first setup your server for this to work and it seems  your trying to connect with strange protocalls too.

"$ sudo /etc/init.d/ssh restart
* Restarting OpenBSD Secure Shell server... [ OK ]


On workstation;
$ ssh -Y satimis@192.168.0.11 nano
satimis@192.168.0.11's password:

Error reading /home/satimis/.nano_history: Permission denied

Press Enter to continue starting nano.

Error opening terminal: unknown."

ssh -Y was for MAC's, or so ive heard. I believe what your looking for is

ssh -X satimis@192.168.0.11

OR

ssh satimis@192.168.0.11

See if you can connect with either of those. The -X option will allow you to forward X11 apps over your network server to client, IF your server is setup correctly. Again, there are precisely detailed Wiki's on Ubuntu Wiki that will tell you all you ever could want to know about how to do this for SSH, sshfs, so on and so forth. The easiest way is to use shared rsa keys so that you dont have to worry about passwords for logins too. sshfs allows you to actually setup mountpoints for ssh shares via fuse. For that you will need sshfs and fuse installed and setup and then it simply could not be easier to get working after that, again, that is ONLY if you actually read and follow the posted Wiki's.
Hi buntunub,

On workstation;

1)
with either
$ ssh satimis@192.168.0.12

or
$ ssh -X satimis@192.168.0.12

I can connection the server.


2)
with;
$ ssh -Y satimis@192.168.0.12 rox/vim/firefox

I can connect the server and start either of the application there except "nano"


On server

1)
With;
$ ssh -Y satimis@192.168.0.11 rox/vim/firefox

I can start either of the above application remotely.


2)
With;
$ ssh -Y satimis@192.168.0.11 nano```

....
Error reading /home/satimis/.nano_history:  Permission denied

Press Enter to continue starting nano.

Error opening terminal: unknown.
```


Server:
$ sudo cat /home/satimis/.nano_history```

canonical
cdrom
universe

```

Workstation
$ sudo cat /home/satimis/.nano_history```

poweroff
power
cursor
Section Monitor
vertical
horizon

```

satimis

---

### Post by satimis on 2007-07-26
> **dreadlord_chris said:**
> does the file /home/satimis/.nano_history exist on the workstation?
```

ls -la /home/satimis/.nano_history

```
if the output of that command is: *No such file or directory* then:
```

touch /home/satimis/.nano_history

```
will probably fix you up...
Hi dreadlord,

Server:
$ sudo cat /home/satimis/.nano_history
```

canonical
cdrom
universe

```

Workstation
$ sudo cat /home/satimis/.nano_history
```

poweroff
power
cursor
Section Monitor
vertical
horizon

```

Problem still remains, but ONLY nano.


B.R.
satimis

---

### Post by satimis on 2007-07-26
> **dreadlord_chris said:**
> -Y is for forwarding *Trusted* X11 connextions
Noted.


I tried -Y/-X or without option.  Problem on "nano" still remains.

satimis

---

