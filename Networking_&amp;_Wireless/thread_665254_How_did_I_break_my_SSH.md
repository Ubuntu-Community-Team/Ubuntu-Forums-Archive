---
title: "How did I break my SSH?"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2008-01-12
SSH was working great, then I secured it a bit.  I had it working, after I did that, then it apparently just randomly broke.  I tried undoing all the configurations, and it still wont work.

Checklist:
-Yes my port is forwarded on my router (plus i cant even ssh localhost)
-Yes I am using "-p <port number>" in my command
-Yes I restarted the service every time after making changes, then tried connecting again

heres my config for /etc/ssh/sshd_config:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 1986
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
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*
```


```
steve@steve:~$ ssh -p 1986 localhost
Read from socket failed: Connection reset by peer

```

---

### Post by MobiusNZ on 2008-01-12
Try changing your log level to DEBUG then viewing your log files after you try to connect

---

### Post by kevdog on 2008-01-12
try with the ssh -vvv parameter

---

### Post by Hawk__0 on 2008-01-12
```
steve@steve:~$ ssh -p 1986 -vvv localhost
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 1986.
debug1: Connection established.
debug1: identity file /home/steve/.ssh/identity type -1
debug1: identity file /home/steve/.ssh/id_rsa type -1
debug1: identity file /home/steve/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
steve@steve:~$ 

```

??

---

### Post by MobiusNZ on 2008-01-12
Not sure if this helps you, but this thread is about the exact same problem
[http://ubuntuforums.org/showthread.php?t=241133](http://ubuntuforums.org/showthread.php?t=241133)

---

### Post by Hawk__0 on 2008-01-12
no, that didn't help. :(

---

### Post by dbott67 on 2008-01-12
What did you do to secure SSH?

hosts.allow / hosts.deny?
iptables?
DenyHosts?

When you removed ssh, did you purge the config files?
```
sudo apt-get purge openssh-server
```

If not, remove openssh again using the 'purge' option and then re-install.

-Dave

---

### Post by Hawk__0 on 2008-01-12
I never said I uninstalled ssh.  I will try it though... I guess...
Ok so I did that.  Apparently it doesn't like me changing the port.
I tried using port 1986, and I get the same error, however if I change it back to port 22 it works fine.

what the heck!?

---

### Post by dbott67 on 2008-01-12
After modifying the port, make sure that you restart sshd:
```
dbott@gutsy:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                                                                                                                                                [ OK ] 
```Then, do a **netstat -l -t -n** to verify that ssh is listening on the correct port (1986, in your case):
```
dbott@gutsy:~$ netstat -l -t -n
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:44536           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:54046           0.0.0.0:*               LISTEN     
tcp6       0      0 :::[COLOR=Red]1968[/COLOR]                 :::*                    LISTEN     
```I just tested this myself & it seems to work.

*[COLOR=Purple]EDIT: oops... I set mine to 1968 rather than 1986, but you get the idea.[/COLOR]*

```
dbott@gutsy:~$ ssh -p 1968 localhost
The authenticity of host '[localhost]:1968 ([127.0.0.1]:1968)' can't be established.
RSA key fingerprint is 05:f1:09:0f:dc:92:64:5b:49:de:44:21:f7:4f:eb:4b.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[localhost]:1968' (RSA) to the list of known hosts.
dbott@localhost's password: 
Linux gutsy 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri Jan 11 20:10:24 2008 from 192.168.1.196
dbott@gutsy:~$ 

```-Dave

---

### Post by Hawk__0 on 2008-01-14
```
steve@steve:~$ sudo vi /etc/ssh/sshd_config 
[sudo] password for steve:
/etc/init.d/steve@steve:~$ /etc/init.d/ssh restart

steve@steve:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
steve@steve:~$ netstat -l -t -n
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:47425           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
**tcp        0      0 127.0.0.1:1986          0.0.0.0:*               LISTEN     **
tcp        0      0 0.0.0.0:42276           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:55238           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:38797           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8112            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::6882                 :::*                    LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::21                   :::*                    LISTEN     
steve@steve:~$ ssh -p 1986 localhost
Read from socket failed: Connection reset by peer

```

Changed my port back to 1986, and restarted the service, and its a no go.

I noticed on mine, my 1986 port says tcp, and yours says tcp6.  what is with that? what does it mean?

---

### Post by dbott67 on 2008-01-14
The TCP6 is for IPv6.  Did you blacklist IPv6?  It doesn't appear that you blacklisted the module, as it's being used for VNC server & FTP, but perhaps you edited the **/etc/modprobe.d/aliases** file.

There are a couple of quirks that IPv6 has with certain routers and/or ISPs that have generated a number of threads on blacklisting IPv6 (one uses the 'blacklist' file, another the 'aliases' file, and some others using 'about:config' in Firefox).

Type the following line to see if the ipv6 module is loaded: 

```
dbott@gutsy:~$ lsmod | grep ip
ipv6                  273892  12
```

Are you employing any other techniques to secure your computer, such as:

1. TCPWrappers (using /etc/hosts.allow and /etc/hosts.deny)
2. iptables (aka firestarter firewall)
3. something else

-Dave

---

