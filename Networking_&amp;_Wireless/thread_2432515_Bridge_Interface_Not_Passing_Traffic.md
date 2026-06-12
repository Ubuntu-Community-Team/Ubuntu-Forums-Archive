---
title: "Bridge Interface Not Passing Traffic"
date: 2019-12-03
forum: Networking &amp; Wireless
---

### Post by pthorburn on 2019-12-03
Hello!

I am trying to setup a bridge between 2 network cards and I have successfully setup the bridge part but I have run into an issue passing traffic between the 2 interfaces.

By default it seems that in ubuntu 18.04 ufw is disabled by default and after I setup the bridge interface I have to run "sudo ufw disable" to get it to forward traffic. If i reboot the server the bridge will not pass traffic even though 'ufw status' shows that it is inactive and i will have to run 'ufw disable' after every reboot in order to get it to pass traffic. Alternatively if I enable forwarding 'ufw default allow FORWARD' and enable the firewall 'ufw enable' the bridge will pass traffic after reboot. So I have 2 solutions to my problem 1) cron job disabling the firewall after reboot or 2) enable the firewall


 My question is... I am curious as to why I need to disable a disabled firewall in order to pass traffic or is having the firewall enabled a requirement that i cannot find listed in any documentation anywhere.

Hopefully someone can shed some light!

Cheers,
Paul

---

### Post by SeijiSensei on 2019-12-03
Packet forwarding across interfaces in Ubuntu is disabled by default. Edit, with sudo, the file /etc/sysctl.conf and make sure the line that reads
```
net.ipv4.ip_forward=1
```
is not disabled with a hash mark at the beginning of the line. If it is, remove the hash mark and reboot. Any better?

---

### Post by Doug S on 2019-12-04
UFW (which I do not use) is just a front end for iptables (which I do use). In addition to what Seiji already mentioned, Suggest to look at iptables contents for all of your scenarios as to what is different.
Do:
```
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
```OR```
sudo iptables-save -c
```I just find the former easier to read.

It is odd that you have to disable ufw when it is disabled already.

---

### Post by pthorburn on 2019-12-04
Hey SeijiSensei and Doug,

Thanks for the quick reply!

Before posting I had found other solutions online and even the man for ufw had referenced changing the following setting which is similar but it i guess it only applies when UFW is enabled.
/etc/ufw/sysctl.conf
net/ipv4/ip_forward=1

Modifying the setting that SeijiSensei suggested seems to resolve the issue and everything is forwarding after reboots.

Thanks to both of you for your assistance!

Cheers,
Paul

---

