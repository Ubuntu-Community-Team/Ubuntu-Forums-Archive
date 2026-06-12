---
title: "Xubuntu: Important file missing from 7.10 (gutsy)"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by gjhicks on 2008-02-16
Hi,

Am using Xubuntu 7.10 (gutsy) and found that the "DNS" dialog of the network setup gui did not work.  It was not possible to add any DNS values.

Discovered that the problem was caused by there being no '/etc/resolv.conf' for the network setup gui to read.

_Quick fix solution:_ 

Open a terminal, become root user (sudo su) and type: **echo "nameserver 127.0.0.1" > /etc/resolv.conf**  Actually, any IP address will do, it is just to create the resolv.conf file.

Go back to the network setup gui and you will be able to add the proper DNS addresses and delete the 127.0.0.1 address.

According to another user (hyperair below) an empty resolv.conf file will suffice.  This may be true for ubuntu but it does not work in xubuntu.

_Proper solution:_

The network setup gui should look to see if a resolv.conf exists and, if it does not, create  the file with some default values.

Bye, Geoff

---

### Post by hyperair on 2008-02-16
I think the file you meant is /etc/resolv.conf. Also, that command can be done without having to resort to using sudo su. Just use:```
sudo "echo nameserver 127.0.0.1 > /etc/resolv.conf"
``` or.. ```
echo "nameserver 127.0.0.1" | sudo tee /etc/resolv.conf
```

In fact, I believe just creating an empty /etc/resolv.conf file will suffice: ```
sudo touch /etc/resolv.conf
```

---

### Post by gjhicks on 2008-02-16
Hyperair,

Thanks for the information, have corrected the post

Geoff.

---

