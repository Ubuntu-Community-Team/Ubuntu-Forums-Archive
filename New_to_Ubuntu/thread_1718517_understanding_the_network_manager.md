---
title: "understanding the network manager"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-03-31
hi all,
I used the network manager to configure my eth0 interface.It is working fine. 
I have found the nameserver entries in /etc/resolv.conf files. 
But the /etc/network/interfaces file does not carry the ip, netmask,  gateway,network and broadcast entries. It only has a entry for the lo  interface.:confused:
where are the settings for eth0 as done by the network manager, stored  in case of ubuntu?
can someone help me out with this information? 
regards
nishith

---

### Post by sully101 on 2011-04-06
If you issue the command

sudo ifconfig eth0

in a terminal you should see it.

What are you trying to achieve?

---

### Post by dineshs on 2011-04-06
> where are the settings for eth0 as done by the network manager, stored in case of ubuntu?
in /etc/NetworkManager/system-connections
Try opening it using ```
gksudo nautilus /etc/NetworkManager/system-connections
```You will see seperate files for eth0, eth1, DSL .....if they exist.The modifications made(eg IP mask gateway DNS etc) via NM GUI will be saved here in respective files.
> But the /etc/network/interfaces file does not carry the ip, netmask, gateway,network and broadcast entries. It only has a entry for the lo interface.If you want Network manager to manage your devices /etc/network/interfaces should contain only that.

---

