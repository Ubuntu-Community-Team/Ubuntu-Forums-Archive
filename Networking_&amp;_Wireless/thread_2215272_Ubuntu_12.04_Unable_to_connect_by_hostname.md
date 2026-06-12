---
title: "Ubuntu 12.04: Unable to connect by hostname"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by unix_user on 2014-04-05
Hi,
I have Ubuntu 12.04 installed at home and I can ssh to it from my Windows 7 by using Putty using the internal IP Number. Here are some details.

* sshd  is working in Ubuntu (ps -ef shows sshd fine)
* can ssh successfully  from Windows 7 using Putty using 192.168.1.x
* can NOT connect using the hostname      // was able to connect some days ago, now UNABLE to putty using hostname
* /etc/hosts has hostname entries
127.0.0.1       myhostname localhost.localdomain   localhost
127.0.0.1       myhostname.dyndns.org

* cat /etc/hostname
myhostname.dyndns.org

* from ubuntu> ping myhostname
success 0% packet loss
* from ubuntu> ping myhostname.dyndns.org
success 0% packet loss

* from Windows> ping myhostname
Ping request could not find myhostname. Please check the name and try again.
* from Windows> ping myhostname.dyndns.org
Responds with External IP address that matches with IP when login to dyndns.org


Can you please suggest if there are any other commands to try?
Thanks in advance

---

