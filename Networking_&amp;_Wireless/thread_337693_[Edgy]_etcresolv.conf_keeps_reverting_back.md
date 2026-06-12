---
title: "[Edgy] /etc/resolv.conf keeps reverting back"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Infx on 2007-01-13
I'm using Ubuntu 6.10 64bit server edition. I also have my own DNS server in my network. It used to be on 192.168.1.15, but it's now on 192.168.1.11. So I changed /etc/resolv.conf to point to the right adres, and it worked fine (with the wrong ip in there you get enormous lag). But only a few days later it changed back to 192.168.1.15 and I have no idea what is causing this.

Also /etc/motd keeps reverting back to it's original state, that seems to happen after I reboot. But resolv.conf changed back even without a reboot!

---

### Post by Hub-1 on 2007-01-13
Usually, this happens if you are connected to a DHCP server, which in your case is most likely your modem or router. The reason why it changes back to the previous address is, because your DHCP server is probably still configured to distribute your old dns IP address to its clients. To change this, you can either reconfigure your DHCP server or tell your DHCP client not to change the nameservers. You can do this by editing  /etc/dhcp3/dhclient.conf. Disable the options you don't want changed by your DHCP client, which in your case is *domain-name-servers*:
Find the part:
```
request subnet-mask, broadcast-address, time-offset, routers
               domain-name, domain-name-servers, host-name,
               netbios-name-servers, netbios-scope;
```
Delete *domain-name-servers* or put a # in front of this line to disable it.

However, its a much better idea to reconfigure your DHCP server.

---

### Post by Maxtorm on 2008-05-02
Thank you. I did that and it also got me thinking that there is no reason why I should have dhclient running (which it was), so I did```
update-rc.d remove dhclient remove
```Unfortunately, this command returns success whether there were any references to the service in rc.d or not, so I also ran ```
update-rc.d remove dhclient3
```In any case, when I rebooted, dhclient3 was no longer listed as a running process, so I'm going to remove the cron job and see how things work over the next few days. Thanks Hub-1.

---

