---
title: "Trouble with OpenVPN server on 8.10"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by NitroBooster on 2008-11-05
Been messing around with this all evening...

First I tried to install the 2.0.9 from a tar ball. 

Somewhere it went wrong, I deleted the directory it was in and decided to try the latest package with apt-get

> 

adminuser@0984576786:~$ sudo apt-get install openvpn network-manager-openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version.
network-manager-openvpn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
adminuser@0984576786:~$ 

adminuser@0984576786:~$ sudo /etc/init.d/openvpn start
[sudo] password for adminuser: 
sudo: /etc/init.d/openvpn: command not found

adminuser@0984576786:~$ /etc/init.d/openvpn start
bash: /etc/init.d/openvpn: No such file or directory



How could that be and how do I fix that?

> 
adminuser@0984576786:/etc/openvpn$ sudo su
root@0984576786:/etc/openvpn# /etc/init.d/openvpn start
bash: /etc/init.d/openvpn: Permission denied
root@0984576786:/etc/openvpn# 


??

---

### Post by SpaceTeddy on 2008-11-05
try to purge the packet (only the openvpn) - something is really wrong there... 

```
sudo apt-get remove --purge openvpn
```

then check if the files were really ALL removed.
then empty you packet cache to make sure you will do a freshdownload:
```
sudo apt-get clean
```

and then reinstall again
```
sudo apt-get install openvpn
```

if the start/stop script still does not work after that, what does
```
which openvpn
ls /etc/init.d
```
say ? is the execuable listed correctly ? or is it not there. Also, is there an openvpn script in init.d ? is there one linked in /etc/rc2.d ?

this is weird...

---

### Post by NitroBooster on 2008-11-06
> **SpaceTeddy said:**
> 
say ? is the execuable listed correctly ? or is it not there. Also, is there an openvpn script in init.d ? is there one linked in /etc/rc2.d ?

this is weird...

That was the problem.

Yeah, I didn't uninstall the 2.0.9 all the way apparently, so the new apt-get install did not go in right.

Anyway, I did what you have suggested, and manually removed the reminence of the old package, and started over , and it worked.

Cheers

---

