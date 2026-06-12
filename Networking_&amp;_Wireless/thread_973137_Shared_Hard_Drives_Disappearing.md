---
title: "Shared Hard Drives Disappearing"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by mdmcaf on 2008-11-06
I've recently upgraded to Ubuntu 8.10 and installed a wireless NIC into my machine (a linksys wmp54g). I have three partitions (two are external and one is a folder on the internal drive) and a printer shared from the machine to an Apple Laptop (running 10.5) and a WinXP laptop. I can see the drives and the printer at certain points but they disappear after a while.

No number of reboots on any of the machines or different methods of connecting seems to fix the problem - one minute it'll be working just fine and the next it won't be working at all.

I have noticed two odd things however -

1. Even though the Ubuntu machine is assigned an IP address and can connect to the internet it cannot be pinged from either of my laptops.

2. In the printer preferences on the Apple it reports the printer as being connected and ready to print.


Any help would be greatly appreciated.

---

### Post by dmizer on 2008-11-06
Sounds like you have a firewall interfering.

Please post the output of the following command:
```
sudo iptables -L
```

---

### Post by mdmcaf on 2008-11-07
thanks for your reply. this is the result that i get it - 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by AlexanderDGreat on 2009-09-09
Hi I don't know if I would be any help, but I also experience disappearing shared folders in my Ubuntu Jaunty 9.04 so I just manually add my shared folder in my /etc/samba/smb.conf file

[shared_folder]
path = /home/(username)/(folder)
read only = no
writeable = yes
browsable = yes


etc, etc...

---

