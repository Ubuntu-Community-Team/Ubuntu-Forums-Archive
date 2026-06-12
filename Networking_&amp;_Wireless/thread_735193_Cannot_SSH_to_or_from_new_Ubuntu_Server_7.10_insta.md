---
title: "Cannot SSH to or from new Ubuntu Server 7.10 install"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by hds17 on 2008-03-25
Hi All,

I am sure this has been answered somewhere before but I just can not seem to find an answer that works.  Sorry for the repetitive question.

I have just completed an install of server 7.10.

I can ping the new box and ping other server from it.  

I can not SSH to the new box or from the new box.

I have SSH server installed. Have have manually restarted the ssh and I have rebooted, but no joy.  Any suggestion or if you could point me to a good thread on this, I would be deeply appreciative.

Regards,

MM

---

### Post by cenwesi on 2008-03-25
If you have firewall installed, then you need to open up port 22.
also on your router, you might need to forward port 22.

try and use this site as a guide/reference:  [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

PS: if you change the port to something else, then you need to also adjust that on your firewall,router and /etc/ssh/ssh_config and sshd_config file

---

### Post by hds17 on 2008-03-25
Thanks for the quick reply,  I am connected to an internal LOCAL Lan.  Does the Firewall install automatically during the install?  I ask because I do not recall seeing or selecting that option.

---

### Post by hds17 on 2008-03-25
Not sure if this will help:  

 ssh -vvv 192.136.x.xxx
OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.136.x.xxx [192.136.x.xxx] port 22.

It is very strange.  I can ssh localhost and can ssh the box's IP from the box.  I can not ssh off the box or to the box from another box.   I did not install a firewall so I do not know how to see if one is enabled.

Any thoughts?

Thanks!

---

