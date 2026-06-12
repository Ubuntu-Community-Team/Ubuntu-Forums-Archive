---
title: "SSH RSA Permission denied (publickey) Ubuntu 18.4 Server"
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by stopiamwarren on 2019-01-28
Hello all!

I am having a hell of a time getting RSA to work for SSH.  I created the key pair, I copied the public key to the ~/.ssh/authorized_keys file, I set the permissions for .ssh as well as authorized_keys and this is what I have enabled in sshd_config:

```
Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
ServerKeyBits 1024 
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 2m
PermitRootLogin no
StrictModes yes
PubkeyAuthentication yes
RSAAuthentication yes
AuthorizedKeysFile    .ssh/authorized_keys 
HostbasedAuthentication no
IgnoreRhosts yes
RhostsRSAAuthentication no
PasswordAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem    sftp    /usr/lib/openssh/sftp-server
allowusers username
```

Any help would be amazing, because I'm on the verge of hurling my box out the window.

Thanks!!

---

### Post by TheFu on 2019-01-28
Best not to manually copy ssh public keys. Use **ssh-copy-id**. Much easier and it won't accidentally mess up the copy, permissions, etc.

Troubleshooting : [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by stopiamwarren on 2019-01-29
Thanks for that, I started over again, and followed those steps and it's working now.  I was able to follow the same steps and setup an sftp key as well, so thanks!

---

