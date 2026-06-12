---
title: "Ubuntu Server, PPTPD password in a plain text file?"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by christian12 on 2014-02-27
Hi,

my first post :) I am new to Linux world. I've work a little bit so far with it. So let me explain my question:

I have a Ubuntu 12.04 Server, which I installed a PPTPD with the apt command. It works perfectly. My question is why the username and password is into a file, no encryption? etc\ppp\chap-secrets

Does the file is protected by something? Is it possible to user username and password into a encrypted file or somewhere else?

Thanks :)

---

### Post by tomearp on 2014-02-28
```
rick@moo:~$ ls -l /etc/ppp/chap-secrets
-rw------- 1 root root 358 Jan 22 09:06 /etc/ppp/chap-secrets
rick@moo:~$ cat /etc/ppp/chap-secrets
cat: /etc/ppp/chap-secrets: Permission denied
```

Only root can access the file.

If you are concerned about security I would suggest not using PPTP, it is considered cryptographically broken. Alternatives are [L2TP/IPsec]("https://help.ubuntu.com/community/L2TPServer"), [OpenVPN]("http://openvpn.net/") or [SoftEther]("http://www.softether.org/").

---

### Post by christian12 on 2014-03-01
Hi.

Thanks for your answer. That was the answer I was hoping for xD. I was using PPTPD as it was easier to deploy and on microsoft server, it was linked (Your user) with your access over the share.

I might look for openVPN, or L2TP/IPSec.

thanks!

---

