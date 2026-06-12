---
title: "DNS Issue after removing Bind9"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by jay.kelly on 2014-01-09
Hello All,
I recently installed Ubuntu Server 13.10 which was assigned a static IP and worked great. I decided to install Bind9 and later decided that I didn't need it and removed it. Now my server will not resolve names. Ive checked the resolv.conf file and it shows the correct DNS server however I cannot resolve still. Im assuming the server is still trying to using the bind9 service to resolve instead of the outside DNS server. Whats strange is when I switch to dhcp everything works fine. My eth0 config includes the following.


auto eth0
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 69.94.156.1

Is there a way to rebuild the resolvconf resolve.conf relationship?

Thanks
Jay

---

