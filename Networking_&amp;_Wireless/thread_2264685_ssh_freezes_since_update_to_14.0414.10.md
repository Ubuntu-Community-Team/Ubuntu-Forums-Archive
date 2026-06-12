---
title: "ssh freezes since update to 14.04/14.10"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by gtred2 on 2015-02-09
Hello,

I've a strange problem. I am using ssh to connect to some servers without any problems for a while.

After upgradind some machines from kubuntu 14.10 to ubuntu 14.04 (same for 14.10) ssh started to freeze for like 5-20 seconds from time to time.

If i ssh to a ubuntu 12.04 and from that machine to the 14.04/14.10 one i get no problems.

Client global ssh_conf

```

Host *
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

For testing i added to ~/.ssh/config
```

ServerAliveCountMax 3
ServerAliveInterval 10

```

Server sshd_config
```

Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 1024
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
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

Network including mtu is looking fine.

Any ideas?

many thanks,
Gregor

---

