---
title: "[HOW-TO] Wake on Lan over the Internet (Wake on WAN)"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Matuku on 2009-12-23
Is there anyway to make the default wakeonlan program use hostnames instead of IP addresses? I couldn't find anything on the man pages but I swear I used to use it in such a way before 9.10.

---

### Post by Matuku on 2009-12-23
As far as I've managed to ascertain the two programs in the Ubuntu Repos that deal with wake on lan (wakeonlan and etherwake) don't have any ability to use hostnames rather than IP Addresses to wake over the internet; if you've got an external IP that often changes (as some ISPs provide) then you'll want to use a dynamic DNS service and a hostname.

As such, I've written the following bash script:

```

#!/bin/bash
SERVERIP=$(host HOSTNAME | grep -o -P "(:?\d+.?){4}")
wakeonlan -i $SERVERIP HWADDRESS
exit

```

where HOSTNAME is your hostname and HWADDRESS is the MAC Address of the box you want to wake. You'll also need to forward port 9 on your router so that it will send the wakeonlan signal to the right place (this is the broadcast address for most routers but some may have another method if they don't allow you to forward to the broadcast address).

Hope this is useful :)

---

### Post by cariboo on 2009-12-23
Please don't create multiple threads on the same subject. I have merged your two threads.

---

