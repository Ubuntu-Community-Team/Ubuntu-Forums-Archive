---
title: "SSH: &quot;No credentials cache found&quot;"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by liquid circuit on 2007-08-29
I'm trying to get SSH working on my Feisty box, and I'm a complete noob at this, so keep that in mind if I am asking something that should be obvious.

I'm able to log in to the server (from the same box) via *ssh user@computer*, *ssh user@192.168.0.101*, *ssh localhost*, and *ssh user@127.0.0.1*.  So that's cool...

My problem is that I'm behind a router, and I wanted to see if I'd be able to log in using the portforwarding I set up on the router.  I'm currently using port 22, and TCP on that port is forwarded (in the router) to the LAN IP address of the host.  sshd is configured to operate on that port, and I ran *sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT* to open the port in Ubuntu.  I've restarted sshd since updating all the configs.

From a terminal on the (SAME) host/server box, I tried running *ssh user@999.999.999.999*, **where 999.999.999.999 is the IP address of my router**, but it just sits there and eventually (~2 minutes later) states "*Connection closed by 24.224.151.249*".

When I run the same command with the verbose options I get the following:

```
user@computer:~$ ssh -v -v -v user@999.999.999.999
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 999.999.999.999 [999.999.999.999] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent


```

I have a feeling that the issue may simply be due to the fact that I am attempting to connect to the external IP address of the router from a computer behind the same router... however I can also easily fathom that there may be another cause for this.

Can anybody explain to me what is going on, or whether this is normal...?  For the moment, I'd just like it to work correctly if I need to log in from outside my home network for some reason (I can worry about extra security later, but I need to see it work before I can do that).

---

### Post by kevdog on 2007-08-29
How did you set up your keys???

---

### Post by liquid circuit on 2007-08-30
Well, I as per [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto") I ran the following command:
```
ssh-keygen -t dsa
```
But I then stopped following the instructions for keys (bad idea?), as I wanted it to work with my password at first.  If I ever need to log in to this computer from outside the network, it will probably be from a computer that I am not able to put a key on easily (ie: random non-techy friends computers).  I don't think I fully understand this whole key authentication thing, so I decided to skip it for the moment.  If I understand correctly, I would need to get a key (that was generated on the host) onto the client computer in-order to log in to my host/server from that client?

---

### Post by kevdog on 2007-08-30
The documentation is good, but somewhat dated, the command you want (if you want to generate keys is)
ssh-keygen -t rsa -b 2048

Can you post your /etc/ssh/sshd_config file??

Go ahead and generate the keys, then
cd ~/.ssh
cat id_rsa.pub > authorized_keys

Also post your ~/.ssh/config file if you have one

---

### Post by liquid circuit on 2007-08-30
I ran those commands and tried to connect again:
```
user@computer:~/.ssh$ ssh -v -v -v user@999.999.999.999
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 999.999.999.999 [999.999.999.999] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug3: Not a RSA1 key file /home/user/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

```

Also, ~/.ssh/config does not exist, however I have the following in /etc/ssh/sshd_config
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
PasswordAuthentication yes

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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

---

### Post by kevdog on 2007-08-30
Can you list all the contents of your .ssh folder.  There shouldnt be that many files.

Also try resetting the server

sudo /etc/init.d/ssh restart

---

### Post by liquid circuit on 2007-08-30
yeah, I restarted sshd, and got the same errors.

```
user@computer:~/.ssh$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ OK ] 
user@computer:~/.ssh$ ssh -v -v -v user@999.999.999.999
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 999.999.999.999 [999.999.999.999] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug3: Not a RSA1 key file /home/user/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
```

```
user@computer:~/.ssh$ ls
authorized_keys  id_dsa  id_dsa.pub  id_rsa  id_rsa.pub  known_hosts

```

---

### Post by kevdog on 2007-08-30
delete the dsa keys -- You dont need them anyway.  I think they might be screwing things up.

---

### Post by liquid circuit on 2007-08-30
Same error :(: (thanks for the help btw!)
```
user@computer:~/.ssh$ rm id_dsa
user@computer:~/.ssh$ rm id_dsa.pub
user@computer:~/.ssh$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ OK ] 
user@computer:~/.ssh$ ssh -v -v -v user@999.999.999.999
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 999.999.999.999 [999.999.999.999] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent

```

---

### Post by kevdog on 2007-08-30
WTF -- 

Ok I really dont know what is going on, but how about reinstalling the ssh server.  Here is how to do:

```
sudo aptitude purge openssh-server

sudo cp /etc/apt/sources.list /etc/apt/sources.list.`date '+%F'`

echo 'deb http://ubuntu.tolero.org/ edgy main' | sudo tee -a /etc/apt/sources.list
sudo aptitude update
sudo aptitude install openssh-server
sudo aptitude upgrade
sudo aptitude install libpam-abl
sudo /etc/init.d/ssh restart
```

Im having you use the tolero patched version of the openssh-server.  The only difference between this version and the old version, is that after 3 guesses with an incorrect password on the server, it locks you out for 5 minutes.

---

### Post by liquid circuit on 2007-08-31
Okay, I did all that without any errors.  I was able to connect successfully via *ssh user@computer*, but I still can't connect via my router's external IP address.

FYI: Since I last made an attempt at connecting I have installed Firestarter.  I did open port 22 for the time being in it, and applied the policy.  Port 22 (TCP) is also still forwarded from the router to the internal IP address of the computer I am running this from/trying to connect to.

Firestarter showed an active connection from my router's external IP address when I made the following SSH connection attempt, however the ssh command just sat there on the second last line for ~2 minutes before returning the connection closed message; here's the output (which seeeeems to indicate some progress):
```
user@computer:~$ ssh -vvv user@999.999.999.999
OpenSSH_4.3p2 Debian-tolero.org+5ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 999.999.999.999 [999.999.999.999] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-tolero.org+5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-tolero.org+5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-tolero.org+5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 999.999.999.999

```

Less debug messages ==  progress??

(coincidentally, I had JUST downgraded wine to an older version about an hour ago so uTorrent would work correctly again... the sudo aptitude upgrade forced an upgrade back to the version I was having problems with... oh well!  time to downgrade again!! two steps forward, one step back ;))

---

### Post by kevdog on 2007-08-31
I have the same server setup as you, and receive the exact same messages as you, however where you messages stop, mine keeps going.  You get:

debug1: SSH2_MSG_KEXINIT sent
Connection closed by 999.999.999.999

I get
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
....
...
....

So something is telling me you are not receiving the signal.  Do you have a firewall installed?? Or did you open up port 22 on the firewall??
Again I dont believe ssh localhost goes through the firewall since its "internal".  But I think ssh IP address needs to bounce outside the firewall and then return.  What IP address are you using, a WAN or LAN address?

Is your daemon running -- post:
sudo ps -ef | grep ssh

---

### Post by kevdog on 2007-08-31
What do you get when you do

telnet <WAN IP ADDRESS> 22

---

### Post by liquid circuit on 2007-08-31
There's a firewall in the router (of course) with Port 22 (TCP) forwarded to the LAN address of the computer.  I also just installed Firestarter as the firewall on the computer and opened Port 22 (I didn't at first, and got much less output... then realized I forgot to apply the policy to open the port... my last post contained the output from AFTER I opened the port, so I'm pretty sure its getting through the firewalls.)

When I run the ssh command I am using the WAN address for the router; my reasoning for doing this is to test if I will be able to connect to my computer via ssh if I am across town on another network. I can connect with no problems at all when I use the LAN address for the computer.  I just tried to connect to the LAN address of the router (192.168.0.1) and the connection was refused (which didn't surprise me of course), however I have now quadruple-checked (or more) that the router is set to forward port 22 to the correct LAN address.

```
user@computer:~$ **sudo ps -ef | grep ssh**
user      5734  5692  0 Aug30 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
root     14478     1  0 01:46 ?        00:00:00 /usr/sbin/sshd
user     18455 18120  0 02:41 pts/2    00:00:00 grep ssh

```

The telnet command sat there for a while before the connection was closed:
```
user@computer:~$ **telnet 999.999.999.999 22**
Trying 999.999.999.999...
Connected to 999.999.999.999.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-tolero.org+5ubuntu1
Connection closed by foreign host.
```

---

### Post by kevdog on 2007-08-31
Ok, next step

Do you have a line in your /etc/hosts.allow file that states:
sshd:ALL

---

### Post by liquid circuit on 2007-08-31
I did not actually, but I have now added it.  Anything I should do for it to take effect?
```
user@computer:~$ cat /etc/hosts.allow 
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and 
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

hotwayd: 127.0.0.1
sshd: ALL
```

---

### Post by kevdog on 2007-08-31
I dont think so (if it doesnt work restart the ssh server).  Just try to connect and tell me what happens

---

### Post by liquid circuit on 2007-08-31
restarted sshd, same output from ssh; last line before connection is closed is still "debug1: SSH2_MSG_KEXINIT sent"

---

### Post by kevdog on 2007-08-31
Try rebooting, also, whats in your /etc/hosts.deny file?

---

### Post by liquid circuit on 2007-08-31
/etc/hosts.deny is empty (just comments), and rebooting didn't change anything.

---

### Post by kevdog on 2007-08-31
Ill see if I can find something tomorrow.  Im confused at this point, and need some time to think about it and look around. I surprised that adding to the /etc/hosts.allow file didnt do anything.

Can you post just for kicks your /etc/ssh/sshd_config file?

---

### Post by kevdog on 2007-08-31
Also check dmesg, /var/lob/syslog.  Maybe these logs will explain in greater detail why the connection failed.

---

### Post by liquid circuit on 2007-08-31
/etc/ssh/sshd_config:
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
PermitRootLogin yes
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

I have zero experience reading the dmesg, but from what I can see nothing pops out:
```
[    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 (Ubuntu Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fdf0000 end: 000000001fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fef0000 size: 0000000000003000 end: 000000001fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fef3000 size: 000000000000d000 end: 000000001ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fef3000 - 000000001ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f38c0
[    0.000000] Entering add_active_range(0, 0, 130800) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130800
[    0.000000]   HighMem    130800 ->   130800
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130800
[    0.000000] On node 0 totalpages: 130800
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125715 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 P4M80P                                ) @ 0x000f7820
[    0.000000] ACPI: RSDT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef3040
[    0.000000] ACPI: FADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef30c0
[    0.000000] ACPI: MADT (v001 P4M80P AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fef8340
[    0.000000] ACPI: DSDT (v001 P4M80P AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
[    0.000000] Detected 3000.461 MHz processor.
[   20.152294] Built 1 zonelists.  Total pages: 129779
[   20.152298] Kernel command line: root=UUID=f3167288-8514-49e9-8d66-893d17a78230 ro quiet splash
[   20.152455] mapped APIC to ffffd000 (fee00000)
[   20.152458] mapped IOAPIC to ffffc000 (fec00000)
[   20.152461] Enabling fast FPU save and restore... done.
[   20.152464] Enabling unmasked SIMD FPU exception support... done.
[   20.152475] Initializing CPU#0
[   20.152577] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   20.153670] Console: colour VGA+ 80x25
[   20.154017] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.154287] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.163335] Memory: 507664k/523200k available (2019k kernel code, 15052k reserved, 902k data, 328k init, 0k highmem)
[   20.163344] virtual kernel memory layout:
[   20.163346]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   20.163347]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.163348]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   20.163349]     lowmem  : 0xc0000000 - 0xdfef0000   ( 510 MB)
[   20.163350]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
[   20.163351]       .data : 0xc02f8c85 - 0xc03da6d4   ( 902 kB)
[   20.163352]       .text : 0xc0100000 - 0xc02f8c85   (2019 kB)
[   20.163355] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.222507] Calibrating delay using timer specific routine.. 6004.81 BogoMIPS (lpj=3002406)
[   20.222552] Security Framework v1.0.0 initialized
[   20.222556] SELinux:  Disabled at boot.
[   20.222577] Mount-cache hash table entries: 512
[   20.222711] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001
[   20.222720] monitor/mwait feature present.
[   20.222722] using mwait in idle threads.
[   20.222729] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.222732] CPU: L2 cache: 1024K
[   20.222734] CPU: Physical Processor ID: 0
[   20.222736] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000641d 00000000 00000001
[   20.222747] Compat vDSO mapped to ffffe000.
[   20.222750] Remapping vsyscall page to ffffe000
[   20.222765] Checking 'hlt' instruction... OK.
[   20.226590] SMP alternatives: switching to UP code
[   20.226864] Early unpacking initramfs... done
[   20.503005] ACPI: Core revision 20060707
[   20.507072] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   20.514529] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   20.514555] SMP alternatives: switching to SMP code
[   20.514640] Booting processor 1/1 eip 3000
[   20.525024] Initializing CPU#1
[   20.585094] Calibrating delay using timer specific routine.. 5999.15 BogoMIPS (lpj=2999577)
[   20.585105] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000001
[   20.585113] monitor/mwait feature present.
[   20.585120] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.585123] CPU: L2 cache: 1024K
[   20.585126] CPU: Physical Processor ID: 0
[   20.585128] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000641d 00000000 00000001
[   20.585507] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   20.585554] Total of 2 processors activated (12003.96 BogoMIPS).
[   20.586329] ENABLING IO-APIC IRQs
[   20.586651] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.697982] checking TSC synchronization across 2 CPUs: passed.
[    0.000998] Brought up 2 CPUs
[    0.129611] migration_cost=81
[    0.129933] Booting paravirtualized kernel on bare hardware
[    0.130041] Time:  3:43:22  Date: 07/31/107
[    0.130075] NET: Registered protocol family 16
[    0.130176] EISA bus registered
[    0.130182] ACPI: bus type pci registered
[    0.138203] PCI: PCI BIOS revision 2.10 entry at 0xf9f20, last bus=1
[    0.138205] PCI: Using configuration type 1
[    0.138207] Setting up standard PCI resources
[    0.153990] ACPI: Interpreter enabled
[    0.153996] ACPI: Using IOAPIC for interrupt routing
[    0.154894] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.154904] PCI: Probing PCI hardware (bus 00)
[    0.156271] Boot video device is 0000:01:00.0
[    0.156390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212677] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.213092] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.213500] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.213896] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.214258] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.214610] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.214979] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.215324] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.215918] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.216484] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.216916] ACPI: PCI Interrupt Link [ALKC] (IRQs *22), disabled.
[    0.217401] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.219468] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.219479] pnp: PnP ACPI init
[    0.223691] pnp: PnP ACPI: found 9 devices
[    0.223698] PnPBIOS: Disabled by ACPI PNP
[    0.223773] PCI: Using ACPI for IRQ routing
[    0.223776] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.235041] NET: Registered protocol family 8
[    0.235044] NET: Registered protocol family 20
[    0.235479] pnp: 00:02: ioport range 0x400-0x47f could not be reserved
[    0.235483] pnp: 00:02: ioport range 0x500-0x50f has been reserved
[    0.235881] PCI: Bridge: 0000:00:01.0
[    0.235886]   IO window: b000-bfff
[    0.235891]   MEM window: fde00000-fdefffff
[    0.235896]   PREFETCH window: e8000000-f7ffffff
[    0.235916] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.235955] NET: Registered protocol family 2
[    0.249054] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.249149] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    0.249263] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[    0.249322] TCP: Hash tables configured (established 16384 bind 8192)
[    0.249324] TCP reno registered
[    0.252177] checking if image is initramfs... it is
[    0.800539] Freeing initrd memory: 6782k freed
[    0.801278] audit: initializing netlink socket (disabled)
[    0.801296] audit(1188531802.539:1): initialized
[    0.801532] VFS: Disk quotas dquot_6.5.1
[    0.801560] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.801628] io scheduler noop registered
[    0.801632] io scheduler anticipatory registered
[    0.801634] io scheduler deadline registered
[    0.801650] io scheduler cfq registered (default)
[    6.307235] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[    6.307250] PCI: Bypassing VIA 8237 APIC De-Assert Message
[    6.307509] isapnp: Scanning for PnP cards...
[    6.662335] isapnp: No Plug & Play device found
[    6.692184] Real Time Clock Driver v1.12ac
[    6.692254] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.692954] mice: PS/2 mouse device common for all mice
[    6.693721] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.693907] input: Macintosh mouse button emulation as /class/input/input0
[    6.693950] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    6.693955] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    6.694307] PNP: No PS/2 controller found. Probing ports directly.
[    6.694734] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.694740] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.694889] EISA: Probing bus 0 at eisa.0
[    6.694934] EISA: Detected 0 cards.
[    6.725008] TCP cubic registered
[    6.725018] NET: Registered protocol family 1
[    6.725048] Starting balanced_irq
[    6.725056] Using IPI No-Shortcut mode
[    6.725150] ACPI: (supports S0 S1 S4 S5)
[    6.725201]   Magic number: 3:342:716
[    6.725389] Time: tsc clocksource has been installed.
[    6.725749] Freeing unused kernel memory: 328k freed
[    7.931899] Capability LSM initialized
[    7.969046] ACPI: Fan [FAN] (on)
[    7.973434] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    7.973445] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    7.975025] ACPI: Thermal Zone [THRM] (52 C)
[    8.472533] SCSI subsystem initialized
[    8.543265] libata version 2.20 loaded.
[    8.567838] usbcore: registered new interface driver usbfs
[    8.567873] usbcore: registered new interface driver hub
[    8.567910] usbcore: registered new device driver usb
[    8.622241] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[    8.625627] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    8.625640] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 16
[    8.625765] eth0: VIA Rhine II at 0x1c000, 00:16:17:9d:7d:a2, IRQ 16.
[    8.626492] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    8.633100] sata_via 0000:00:0f.0: version 2.1
[    8.633689] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    8.633700] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[    8.633734] sata_via 0000:00:0f.0: routed to hard irq line 11
[    8.633823] ata1: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 17
[    8.633859] ata2: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 17
[    8.633880] scsi0 : sata_via
[    8.637794] USB Universal Host Controller Interface driver v3.0
[    8.660837] FDC 0 is a post-1991 82077
[    8.834763] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    8.844966] ATA: abnormal status 0x7F on port 0x0001ec07
[    8.845000] scsi1 : sata_via
[    9.046136] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    9.056337] ATA: abnormal status 0x7F on port 0x0001e407
[    9.057450] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    9.057465] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[    9.057489] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    9.057682] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    9.057721] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000d000
[    9.057886] usb usb1: configuration #1 chosen from 1 choice
[    9.057931] hub 1-0:1.0: USB hub found
[    9.057946] hub 1-0:1.0: 2 ports detected
[    9.159488] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[    9.159506] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    9.159541] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    9.159567] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000cc00
[    9.159725] usb usb2: configuration #1 chosen from 1 choice
[    9.159774] hub 2-0:1.0: USB hub found
[    9.159785] hub 2-0:1.0: 2 ports detected
[    9.261680] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[    9.261698] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    9.261735] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    9.261763] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000c800
[    9.261932] usb usb3: configuration #1 chosen from 1 choice
[    9.261977] hub 3-0:1.0: USB hub found
[    9.261990] hub 3-0:1.0: 2 ports detected
[    9.362867] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[    9.362886] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    9.362920] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    9.362948] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000c400
[    9.363097] usb usb4: configuration #1 chosen from 1 choice
[    9.363146] hub 4-0:1.0: USB hub found
[    9.363156] hub 4-0:1.0: 2 ports detected
[    9.464103] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[    9.464123] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    9.464159] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    9.464215] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdfff000
[    9.464225] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    9.464371] usb usb5: configuration #1 chosen from 1 choice
[    9.464414] hub 5-0:1.0: USB hub found
[    9.464425] hub 5-0:1.0: 8 ports detected
[    9.566414] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    9.566456] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[    9.566478] VP_IDE: chipset revision 6
[    9.566482] VP_IDE: not 100% native mode: will probe irqs later
[    9.566502] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    9.566517]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:DMA
[    9.566536]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[    9.566552] Probing IDE interface ide0...
[    9.952207] hda: WDC WD200BB-75AUA1, ATA DISK drive
[   10.206764] hdb: WDC WD400EB-00CPF0, ATA DISK drive
[   10.261246] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   10.284275] Probing IDE interface ide1...
[   10.467142] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   10.639269] usb 2-1: configuration #1 chosen from 1 choice
[   10.642217] hub 2-1:1.0: USB hub found
[   10.645161] hub 2-1:1.0: 3 ports detected
[   10.771852] hdc: HL-DT-STDVD-RAM GSA-H55N, ATAPI CD/DVD-ROM drive
[   10.932884] usb 2-1.2: new full speed USB device using uhci_hcd and address 3
[   11.027667] hdd: WDC WD153BA, ATA DISK drive
[   11.077848] usb 2-1.2: configuration #1 chosen from 1 choice
[   11.080795] ide1 at 0x170-0x177,0x376 on irq 15
[   11.109169] hda: max request size: 128KiB
[   11.111921] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[   11.111933] hda: cache flushes not supported
[   11.111986]  hda: hda1 hda2 hda3 hda4
[   11.133600] hdb: max request size: 128KiB
[   11.134649] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   11.134657] hdb: cache flushes not supported
[   11.134688]  hdb: hdb1
[   11.140300] hdd: max request size: 128KiB
[   11.141085] hdd: 30043440 sectors (15382 MB) w/2048KiB Cache, CHS=29805/16/63, UDMA(33)
[   11.141091] hdd: cache flushes not supported
[   11.141116]  hdd: hdd1
[   11.162212] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   11.162228] Uniform CD-ROM driver Revision: 3.20
[   11.260670] usb 2-1.3: new full speed USB device using uhci_hcd and address 4
[   11.405535] usb 2-1.3: configuration #1 chosen from 1 choice
[   11.411571] usbcore: registered new interface driver hiddev
[   11.416525] input: Logitech Logitech BT Mini-Receiver as /class/input/input1
[   11.416550] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:10.1-1.2
[   11.424515] input: Logitech Logitech BT Mini-Receiver as /class/input/input2
[   11.424603] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:10.1-1.3
[   11.424624] usbcore: registered new interface driver usbhid
[   11.424630] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   11.585859] Attempting manual resume
[   11.585864] swsusp: Resume From Partition 3:2
[   11.585866] PM: Checking swsusp image.
[   11.598993] PM: Resume from disk failed.
[   11.625248] kjournald starting.  Commit interval 5 seconds
[   11.625262] EXT3-fs: mounted filesystem with ordered data mode.
[   24.362869] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   24.969076] NET: Registered protocol family 10
[   24.969218] lo: Disabled Privacy Extensions
[   26.112750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.159711] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.213732] Linux agpgart interface v0.102 (c) Dave Jones
[   26.244645] agpgart: Detected VIA VT3314 chipset
[   26.258940] agpgart: AGP aperture is 256M @ 0xd0000000
[   26.701839] input: PC Speaker as /class/input/input3
[   27.333163] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 19
[   27.511582] fuse init (API version 7.8)
[   27.577904] lp: driver loaded but no devices found
[   27.710825] Bluetooth: Core ver 2.11
[   27.711115] NET: Registered protocol family 31
[   27.711119] Bluetooth: HCI device and connection manager initialized
[   27.711124] Bluetooth: HCI socket layer initialized
[   27.713874] Bluetooth: L2CAP ver 2.8
[   27.713879] Bluetooth: L2CAP socket layer initialized
[   27.725009] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   27.766609] Adding 498004k swap on /dev/disk/by-uuid/bd6d229b-1453-4cbd-8edb-229dfc48ff52.  Priority:-1 extents:1 across:498004k
[   27.912652] EXT3 FS on hda3, internal journal
[   28.231528] kjournald starting.  Commit interval 5 seconds
[   28.231655] EXT3 FS on hda4, internal journal
[   28.231661] EXT3-fs: mounted filesystem with ordered data mode.
[   30.010975] NET: Registered protocol family 17
[   35.197054] ibm_acpi: ec object not found
[   35.242913] Using specific hotkey driver
[   35.266063] No dock devices found.
[   35.285334] input: Power Button (FF) as /class/input/input4
[   35.285373] ACPI: Power Button (FF) [PWRF]
[   35.285430] input: Power Button (CM) as /class/input/input5
[   35.285459] ACPI: Power Button (CM) [PWRB]
[   35.285510] input: Sleep Button (CM) as /class/input/input6
[   35.285551] ACPI: Sleep Button (CM) [SLPB]
[   35.493534] pcc_acpi: loading...
[   35.748323] eth0: no IPv6 routers present
[   39.003025] [drm] Initialized drm 1.1.0 20060810
[   39.015264] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   39.015865] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   39.722530] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   39.722561] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.722675] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   39.870569] ppdev: user-space parallel port driver
[   40.026491] [drm] Setting GART location based on new memory map
[   40.026504] [drm] Loading R200 Microcode
[   40.026602] [drm] writeback test succeeded in 1 usecs
[   40.948160] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   40.948605] apm: disabled - APM is not SMP safe.
[   41.138838] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.206366] Netfilter messages via NETLINK v0.30.
[   41.223272] nf_conntrack version 0.5.0 (4087 buckets, 32696 max)
[   42.272895] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   42.374637] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   42.387776] NFSD: starting 90-second grace period
[   44.207591] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.207646]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.207768]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.207846]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.207883]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.207951]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.208022]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.208090]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.208203]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.208281]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.208352]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.208419]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.208516]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.208594]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.208652]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.208729]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.208826]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.208894]  =======================
[   44.208923] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.208960]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.209148]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.209222]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.209278]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.209369]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.209440]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.209507]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.209621]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.209698]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.209742]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.209808]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.209928]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.210030]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.210112]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.210190]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.210287]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.210329]  =======================
[   44.210382] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.210420]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.210633]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.210683]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.210715]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.210781]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.210852]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.210945]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.211008]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.211059]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.211129]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.211169]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.211290]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.211417]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.211499]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.211553]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.211624]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.211691]  =======================
[   44.216059] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.216081]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.216193]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.216222]  [<c011658f>] smp_apic_timer_interrupt+0x6f/0x80
[   44.216269]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.216324]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.216364]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.216418]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.216440]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.216457]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.216556]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.216586]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.216620]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.216649]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.216699]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.216744]  =======================
[   44.216748] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.216759]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.216878]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.216909]  [<c011658f>] smp_apic_timer_interrupt+0x6f/0x80
[   44.216954]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.217008]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.217047]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.217101]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.217122]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.217138]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.217238]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.217268]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.217301]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.217332]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.217381]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.217422]  =======================
[   44.221125] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.221143]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.221258]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.221270]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.221303]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.221330]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.221348]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.221389]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.221430]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.221480]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.221500]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.221514]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.221609]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.221639]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.221673]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.221701]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.221750]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.221795]  =======================
[   44.221799] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.221811]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.221930]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.221943]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.221977]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.222006]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.222025]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.222064]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.222104]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.222157]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.222179]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.222196]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.222294]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.222323]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.222358]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.222385]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.222434]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.222479]  =======================
[   44.222483] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.222496]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.222614]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.222627]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.222661]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.222690]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.222707]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.222746]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.222788]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.222837]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.222858]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.222875]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.222976]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.223006]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.223040]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.223070]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.223118]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.223163]  =======================
[   44.260629] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.260686]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.260815]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.260844]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.260854]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.260902]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.260924]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.260967]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.261009]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.261065]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.261089]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.261106]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.261206]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.261236]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.261267]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.261294]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.261343]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.261386]  =======================
[   44.261390] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.261399]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.261501]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.261521]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.261526]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.261562]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.261579]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.261616]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.261649]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.261695]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.261711]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.261724]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.261810]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.261834]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.261862]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.261886]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.261926]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.261963]  =======================
[   44.261965] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.261975]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.262078]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.262099]  [<c02f4fd1>] _spin_unlock+0x11/0x30
[   44.262103]  [<c0176f74>] get_unused_fd+0xa4/0xc0
[   44.262139]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.262155]  [<e0902b41>] usbhid_init_reports+0x71/0xf0 [usbhid]
[   44.262191]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.262224]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.262269]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.262285]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.262298]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.262384]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.262408]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.262436]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.262460]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.262500]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.262537]  =======================
[   44.264319] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.264334]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.264448]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.264511]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.264569]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.264598]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.264689]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.264751]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.264816]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.264868]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.264938]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.265004]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.265124]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.265202]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.265284]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.265336]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.265457]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.265524]  =======================
[   44.265553] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.265590]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.265753]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.265815]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.265897]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.265975]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.265991]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.266078]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.266141]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.266266]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.266336]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.266377]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.266498]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.266551]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.266657]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.266759]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.266879]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.266971]  =======================
[   44.267305] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.267344]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.267508]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.267571]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.267653]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.267755]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.267846]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.267933]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.267999]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.268075]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.268120]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.268185]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.268330]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.268383]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.268489]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.268541]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.268661]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.268728]  =======================
[   44.268781] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.268843]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.268982]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.269021]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.269103]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.269205]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.269248]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.269310]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.269398]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.269450]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.269471]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.269511]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.269633]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.269686]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.269719]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.269796]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.269868]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.269935]  =======================
[   44.269964] BUG: at drivers/hid/hid-core.c:780 implement()
[   44.269977]  [<e08fa5b4>] hid_output_report+0x234/0x2e0 [hid]
[   44.270141]  [<e09024e8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   44.270203]  [<c02f39d3>] schedule_timeout+0x53/0xd0
[   44.270261]  [<c013c8cd>] finish_wait+0x2d/0x70
[   44.270363]  [<e09027ab>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   44.270429]  [<c013c7f0>] autoremove_wake_function+0x0/0x50
[   44.270515]  [<e0904a86>] hiddev_ioctl+0x456/0xb50 [usbhid]
[   44.270578]  [<c015b9be>] filemap_nopage+0x30e/0x420
[   44.270679]  [<c011ed98>] kunmap_atomic+0x38/0x90
[   44.270699]  [<c0166714>] __handle_mm_fault+0x294/0xaa0
[   44.270814]  [<c0177245>] nameidata_to_filp+0x35/0x40
[   44.270936]  [<c0184e88>] do_ioctl+0x78/0x90
[   44.270963]  [<c0184efc>] vfs_ioctl+0x5c/0x2a0
[   44.270996]  [<c01851b2>] sys_ioctl+0x72/0x90
[   44.271050]  [<c0103360>] sysenter_past_esp+0x69/0xa9
[   44.271121]  [<c02f0033>] atm_register_sysfs+0x3/0xb0
[   44.271188]  =======================
[   44.327034] Bluetooth: RFCOMM socket layer initialized
[   44.327050] Bluetooth: RFCOMM TTY layer initialized
[   44.327054] Bluetooth: RFCOMM ver 1.8
[   44.446125] usb 2-1.1: new full speed USB device using uhci_hcd and address 5
[   44.572153] usb 2-1.1: configuration #1 chosen from 1 choice
[   44.781123] Bluetooth: HCI USB driver ver 2.9
[   44.785312] usbcore: registered new interface driver hci_usb
[   47.710806] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   47.710879] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   47.711293] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   47.984931] [drm] Setting GART location based on new memory map
[   47.984944] [drm] Loading R200 Microcode
[   47.985015] [drm] writeback test succeeded in 1 usecs
[   50.395773] input: Logitech Bluetooth Mouse as /class/input/input7
[   54.879057] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   54.879309] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   54.879521] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   55.145021] [drm] Setting GART location based on new memory map
[   55.145032] [drm] Loading R200 Microcode
[   55.145105] [drm] writeback test succeeded in 1 usecs
[   70.815839] input: Logitech Bluetooth Keyboard as /class/input/input8
```

And then finally we have:
```
user@computer:~$ cat /var/log/syslog
Aug 31 03:51:12 computer syslogd 1.4.1#20ubuntu4: restart.
Aug 31 03:51:12 computer anacron[5881]: Job `cron.daily' terminated
Aug 31 03:54:06 computer anacron[5881]: Job `cron.weekly' started
Aug 31 03:54:06 computer anacron[7058]: Updated timestamp for job `cron.weekly' to 2007-08-31
Aug 31 03:54:46 computer syslogd 1.4.1#20ubuntu4: restart.
Aug 31 03:54:46 computer anacron[5881]: Job `cron.weekly' terminated
Aug 31 03:54:46 computer anacron[5881]: Normal exit (2 jobs run)
Aug 31 04:17:02 computer /USR/SBIN/CRON[7749]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 04:27:02 computer gconfd (root-8023): starting (version 2.18.0.1), pid 8023 user 'root'
Aug 31 04:27:02 computer gconfd (root-8023): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 31 04:27:02 computer gconfd (root-8023): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 31 04:27:02 computer gconfd (root-8023): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 31 04:27:02 computer gconfd (root-8023): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 31 04:27:02 computer gconfd (root-8023): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

```

At this point I am incredibly appreciative that you have been so diligent in helping me troubleshoot this.  I've posted a couple threads on here for other issues before and haven't gotten any responses at all, although I was never really discouraged by that since I understood those issues were niche/specific hardware related so it would be less likely to get in-depth assistance/solid fixes.  Also, since my day-job is providing tech support for mobile data devices (Blackberry's, Windows Mobile device's, Symbian devices, laptops) with one of the major American wireless providers, I sympathize with you for wanting to figure out what the hell is going wrong here!  I know when I can't fix something that I think I should be able to, it burns away in the back of my mind all day long (I hate saying, "guess what?  Warranty time!").  Regardless, your help is much appreciated.

---

### Post by kevdog on 2007-08-31
You can obviously ssh to "yourself" without a problem so I dont think its a problem with the server set up per-se, just authentication.  Do you have another machine on your LAN that you can try to ssh into your box?  This way, it would take the router out of the loop, although my guess is the router isnt the problem because it seems at least the port is getting forwarded.  Have you tried connecting from a remote machine with either ssh (linux) or putty(windows or ssh cygwin/windows)?  Even though you dont have the key with you right now, you should get an error message saying authentication method failed -- no public key or methods left to try (or something like that!!).

---

### Post by liquid circuit on 2007-09-03
I was able to successfully log in via ssh from my girlfriend's OS X laptop (via the LAN address), so thats all good.  And I was also able to ssh into my girlfriend's laptop from the Ubuntu box. :):confused:

---

### Post by kevdog on 2007-09-03
I dont know if the problem is solved but it sounds like its working like what you want.

---

### Post by liquid circuit on 2007-09-03
Kind of, but not really.  I'm able to log in from a computer inside my LAN, but I get the impression I won't be able to log in from outside the LAN.  Being able to log in from inside the LAN is great for maintenance/repair, however I'd like to be able to log in from outside so that I can scp files off of my computer to a friend's computer.  I do some music production as a hobby, and if I am doing some collaboration with someone else at their house I may suddenly forget/realize I need a file/plugin that is on my computer at home, and I'd like to be able to copy that file from my computer at home to the computer I am working on.  So, I was attempting to use the WAN address of the router to test if this would work... but I was doing that from inside the LAN...  confused yet? ;)  And that is still not working yet.  I haven't actually had the chance to test ssh from outside the LAN using the WAN address of the router.

---

### Post by kevdog on 2007-09-03
I understand what you want to do, although I usually find that something like using samba or nfs inside the LAN is usually preferrable to me since I trust all the computers inside the LAN.  Id be curious to know is this actually worked from a computer located outside your LAN -- as youve stated you havent been able to try this.  When you do please let us know.

---

### Post by heni on 2007-10-01
I had the same error message.
I've fixed problem by replacing string "GSSAPIAuthentication yes" by "GSSAPIAuthentication no" in /etc/ssh/ssh_config file on client laptop.

---

