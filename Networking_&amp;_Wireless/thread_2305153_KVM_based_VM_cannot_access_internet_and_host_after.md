---
title: "KVM based VM cannot access internet and host after creating static network"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by er-it-pchaturvedi on 2015-12-03
[FONT=Arial]My vm is unable to access host machine or internet when i set following in my /etc/network/interfaces of the guest vm[/FONT]
[FONT=Arial]auto eth0 
iface eth0 inet static 
address 192.168.122.184 
netmask 255.255.255.0[/FONT]
[FONT=Arial]i can ping to other guests on same host with this configuration, but i can not ping either my host machine or the internet[/FONT]
[FONT=Arial]whereas if i replace it with dhcp[/FONT]
[FONT=Arial]auto eth0 iface eth0 inet dhcp[/FONT]
[FONT=Arial]then i am able to reach my host as well a internet.[/FONT]
[FONT=Arial]I want to use static ip for my guests, but because of above issue i am not able to use it. Please help[/FONT]
[FONT=Arial]I have a running cassandra cluster with this static ip setup, so i do not want to change the basics. please suggest answers for this situation.[/FONT]
[FONT=Arial]
I am using default NAT networking

Thanks !!


[/FONT]

---

### Post by rslater on 2015-12-03
Try adding the gateway address (your router IP) and the address(es) of your dns-nameserver(s).  When set to DHCP the system will be adding these for you.  For static IP addressing, you must specify them.

Have a look at this link [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

Best regards.

---

