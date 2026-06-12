---
title: "ssh: connection refused when connecting from external network"
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by portin-daniel on 2015-07-31
I'm having trouble connecting to my computer from an external network using ssh. The computer is behind a router for which port forwarding has been set up; I can connect over the local network. When I attempt to connect from an external network (using a Chromebook running Debian), I encounter the following error:

```

(jessie)dportin@localhost:~$ ssh -vvv -p <forwarded_port> dportin@<routerip>
OpenSSH_6.7p1 Debian-5, OpenSSL 1.0.1k 8 Jan 2015
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 22: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to <router_ip> [<router_ip?] port <forwarded_port>.
debug1: connect to address <router_ip> port <forwarded_port>: Connection refused
ssh: connect to host <router_ip> port <forwarded_port>: Connection refused
```

Here is my sshd_config file:

```

Port <forwarded_port>
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 1024
MaxStartups 10:30:60
MaxSessions 10
SyslogFacility AUTH
LogLevel DEBUG
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication no 
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
```

The sshd process is running and listening on the forwarded port:

```

dportin@dportin-xubuntu:~$ ps -ef | grep sshd
root      5760     1  0 12:47 ?        00:00:00 /usr/sbin/sshd -D
```

```

dportin@dportin-xubuntu:~$ sudo lsof -i TCP -P | grep LISTEN
sshd      5760    root    3u  IPv4  54688      0t0  TCP *:<forwarded_port> (LISTEN)
```

```

dportin@dportin-xubuntu:~$ sudo netstat -tulpn | grep sshd
tcp        0      0 0.0.0.0:<forwarded_port>            0.0.0.0:*               LISTEN      5760/sshd
```

I don't see any information in /var/log/auth.log corresponding to connection attempts, but tcpdump does register requests (everything looks normal when a successful connecti
on is made over the local network). I have also disabled ufw. I don't think the router or local network is the problem (someone smarter than myself manages it, and uses ssh without problem). Any help or direction would be appreciated! I'm fairly new to this stuff, and don't know if I'm leaving out any pertinent information.

**Edit: **This must be a problem with iptables/ufw, since I see blocks in kern.log corresponding to ssh/telnet attempts (not on the local network). I set up iptables to allow connections over the relevant port. Is there some secret I'm missing?

---

### Post by TheFu on 2015-07-31
Did you setup ssh-keys between the client and server?
 The server config file shown doesn't support passwords.

---

### Post by portin-daniel on 2015-07-31
> **TheFu said:**
> Did you setup ssh-keys between the client and server?
 The server config file shown doesn't support passwords.

Yeah. I can connect using key-based authentication on my local network. It's connecting from an external network that fails.

---

### Post by TheFu on 2015-07-31
Ok ... have you created a ~/.ssh/config file?  That will make dealing with odd ports, different IPs and different userids much easier.

Also, please stop the server and rerun it in non-daemon mode with debug data enabled. You'll be able to watch the connection ... or see that no connection is getting to the server at all.  I think the cmd you need is:  **sudo /usr/sbin/sshd -d** - it would be nice to have the port on 22 internally and let the router do port translation for external connections. Anyway, that's how I do it. Letting the ~/.ssh/config file handle the different ports so I never have to remember if -p or -P is needed for all the different cmds.

---

### Post by portin-daniel on 2015-07-31
> **TheFu said:**
> Ok ... have you created a ~/.ssh/config file?  That will make dealing with odd ports, different IPs and different userids much easier.

Also, please stop the server and rerun it in non-daemon mode with debug data enabled. You'll be able to watch the connection ... or see that no connection is getting to the server at all.  I think the cmd you need is:  **sudo /usr/sbin/sshd -d** - it would be nice to have the port on 22 internally and let the router do port translation for external connections. Anyway, that's how I do it. Letting the ~/.ssh/config file handle the different ports so I never have to remember if -p or -P is needed for all the different cmds.

Do you mean /etc/ssh/sshd_config on the server or a configuration file on the client machine by ~/.ssh/config? I posted my sshd_config above, where I added the 'Port <forwarded_port>' directive and set the logging level to debug mode. I'll try restarting the sever in non-daemon mode and monitoring the output the next chance I get to connect remotely. The latest collection of logs I gathered suggested that I was being blocked by ufw, however, so I suspect that the firewall isn't configured correctly.

---

### Post by TheFu on 2015-07-31
The file specified is client-side. I just find it sooooo much easier to put settings into there.  2 stanzas - 1 for internal use and one for use over the internet.

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has a ufw example for ssh.

**sudo iptables -L** is how to check the firewall rules.

---

### Post by portin-daniel on 2015-08-01
> **TheFu said:**
> The file specified is client-side. I just find it sooooo much easier to put settings into there.  2 stanzas - 1 for internal use and one for use over the internet.[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has a ufw example for ssh.**sudo iptables -L** is how to check the firewall rules.Thanks for the link. It turns out that I configured ufw incorrectly, and the problem wasn't very interesting (just frustrating to deal with). Thanks for your help!

---

### Post by TheFu on 2015-08-01
> **portin-daniel said:**
> Thanks for the link. It turns out that I configured ufw incorrectly, and the problem wasn't very interesting (just frustrating to deal with). Thanks for your help!

We all make tiny mistakes from time to time. No worries. How to work through issues is just as important as the final solution. Sometimes the answer isn't this quick to reveal itself.

Thanks for saying what the fix was too. Would be nice if you posted the **ufw** cmds needed for others to learn.

---

