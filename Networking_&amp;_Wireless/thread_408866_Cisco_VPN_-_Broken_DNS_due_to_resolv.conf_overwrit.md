---
title: "Cisco VPN - Broken DNS due to resolv.conf overwrite"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by ariel on 2007-04-13
Hi, I have succeded installing and configuring the Cisco VPN Client (version  4.8.00 (0490)) in my Ubuntu Edgy box.

It works fine, it connects to my work's VPN, creates the cipsec0 interface, gets an IP address, and sets /etc/resolv.conf to the appropriate domain and nameserver for my VPN.

However, about 5 seconds afterwards, my resolv.conf gets overwritten with my non-vpn configuration, which is the standard:

$ cat /etc/resolv.conf
search lan
nameserver 192.168.1.1

I even tried changing the nameserver manually and setting the VPN ones, only to find that after a minute or two, it gets overwritten again.

Of course, with the wrong DNS configuration, I can't browse the Intranet.

Can someone shed some light on how to stop the automatic resolv.conf overwrite while I am connected to the VPN?

Thanks!

---

### Post by Austin_KW on 2007-04-13
Have you installed network-manager? It watches and reconfigures your connections.

---

### Post by dday376 on 2007-04-14
I'm not sure, but you might fix it by updating:

/etc/dhcp3/dhclient.conf

You can add an alias section specifically for the cipsec0 interface, and I think you'll want to add a prepend directive to specify the necessary dns entries.

I'm not 100% sure on this, so you'll want to verify by researching exactly what you can put in dhclient.conf - I've never done any alias directives.  I do use it to prepend opendns servers in my dns search list, but I do it for all interfaces.

---

### Post by ariel on 2007-04-14
> **Austin_KW said:**
> Have you installed network-manager? It watches and reconfigures your connections.

Nope, no network manager. Plain and simple default config.

---

### Post by Austin_KW on 2007-04-14
I think dday376's solution is right, if the dhcp lease renewal is overwriting then adding prepend domain-name-server ipAddress to dhclient.conf should work. Remember to remove it when you are not using vpn or your dns lookup will be slow.

---

### Post by ariel on 2007-04-15
Thanks for the reply. 

Instead of modifying dhclient.conf every time before launching the vpn client, I found that killing the dhclient associated to the interface over which the vpn client is running does the trick.

I just do: ```
ps aux | grep dh
```

and get something like:
dhcp      7754  0.0  0.0   2400   548 ?        Ss   12:15   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

and then: sudo kill 7754

After the session, the client can be relaunched:
```
sudo dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
```

I guess it wouldn't be hard to automate this adding a few lines to my vpn startup script  but I'm too lazy for that :)

---

### Post by archon256 on 2008-02-01
I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

---

