---
title: "[SOLVED] ssh_exchange_identification: Connection closed by remote host"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by connors2647 on 2014-05-01
After upgrading from 13.10 to 14.04 I could no longer _**SSH -> proxy connect**_ or _**SSH HOP**_ to my internal network machines.

Here is my error Messages and Solution fix

**OLD VERSION - .ssh/config**
```
Host someserver
    HostName someaddress
    User user
    Port 22

Host mcon
    HostName 192.168.1.100
    User mcon
    ForwardAgent yes
    Port 22
    ProxyCommand ssh -q someserver nc -q0 mcon 22

```



**Shell**
```
sudo ssh -vvv mcon
[sudo] password for mcon: 
OpenSSH_6.6, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /root/.ssh/config
debug1: /root/.ssh/config line 15: Applying options for mcon
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Hostname has changed; re-reading configuration
debug1: Reading configuration data /root/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Executing proxy command: exec ssh -q someserver nc -q0 mcon 22
debug1: permanently_set_uid: 0/0
debug1: permanently_drop_suid: 0
debug3: Incorrect RSA1 identifier
debug3: Could not load "/root/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6p1 Ubuntu-2ubuntu1
ssh_exchange_identification: Connection closed by remote host

```

**SOLUTION - .ssh/config**
```
Host someserver
    HostName someaddress
    User user
    Port 22

Host mcon
    HostName 192.168.1.100
    User mcon
    ForwardAgent yes
    Port 22
    **ProxyCommand ssh someserver nc %h %p**

```

I hope this helps someone out there. It took me a couple of days to solve.

---

### Post by Lars Noodén on 2014-05-01
With the newer versions of openssh-client you can also use the [-W option](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html) to forward the connection.  

```

ProxyCommand ssh someserver -W %h:%p

```

That way you do not even need netcat.

---

