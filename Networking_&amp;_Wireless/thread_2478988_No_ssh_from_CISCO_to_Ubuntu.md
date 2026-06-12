---
title: "No ssh from CISCO to Ubuntu"
date: 2022-09-11
forum: Networking &amp; Wireless
---

### Post by zamorojo on 2022-09-11
I have problems when making ssh from CISCO SWitch to my Ubuntu 22.04.1, 
I have to make SCP copies from cisco machine and save them in my repository inside Ubuntu. 
ssh Ubuntu ==> Cisco = OK 
ssh Cisco ==> Ubuntu = Fail  
error is the following: 
[Connection to 192.168.11.126 aborted: error status 0]
 
C2960C# *Jan 2 00:40:13.830: %SSH-3-NO_MATCH: No matching kex algorithm found: client diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1 server curve25519-sha256,curve25519-sha256@libssh .org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman -group18-sha512,diffie-hellman-group14-sha256 

I have modified my ssh_config file several times but I can't get it out. . someone who can guide me ..... Thanks !!!!

---

### Post by TheFu on 2022-09-11
You can "pull" or "push" from ubuntu, so the problem isn't really a show-stopper.

I suspect the cisco version of ssh is too old and doesn't use the default ciphers.

Check the connection using **ssh -vvvvv**.  ssh, scp, sftp, all use the same connections.  BTW, last year the ssh team suggested that scp be deprecated, but you'll want to make plans for alternative workflows over the next few years.  Deprecation is usually a 3-5 yr pre-warning.

---

### Post by SeijiSensei on 2022-09-11
Connecting to 22.04 SSH servers from older clients have problems with key ciphers. Connecting from a Centos 6.7 machine requires that I add:

```
ssh -v user@host -oHostkeyAlgorithms=+ssh-rsa
```

Or add it to /etc/ssh/ssh_config.

DK about connecting from Ciscos, I don't see rsa in the list in your posting.

---

### Post by TheFu on 2022-09-11
diffie-hellman was deprecated.  [https://www.openssh.com/legacy.html](https://www.openssh.com/legacy.html) 
The curve25519 should be fine.  I've been using ed25519 as my default ssh-keys for about 5 yrs now.

---

