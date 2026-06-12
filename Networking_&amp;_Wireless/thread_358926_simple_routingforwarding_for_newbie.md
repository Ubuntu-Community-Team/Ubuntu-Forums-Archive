---
title: "simple routing/forwarding for newbie"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by tuokor on 2007-02-11
Hi, I'm trying to make my old pc to act as a linux server and router. It would act also as a firewall for my other pc which would be connected trough the ubuntu server which has access to internet via dhcp. During the server installation eth0 was configured automatically to use dhcp. My other pc is connected to the other network card (eth1). how do i configure the eth1 interface?
I looked the iptables configuration from this address:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

but how do I configure the /etc/network/interfaces file? now there is only the eth0 configuration.

Looking the ubuntuhelp about network configuration there was a note about static ip-address.

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html)

Do I use static config to eth1?

---

### Post by tuokor on 2007-02-11
to simplify this question. I need to share my internet connection. the net is connected to my linux server. it gets everything trough dhcp. how do i share this connection with my windows pc???

---

### Post by pedalwrench on 2007-02-11
you may want to look here

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

