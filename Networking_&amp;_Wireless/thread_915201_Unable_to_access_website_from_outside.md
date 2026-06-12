---
title: "Unable to access website from outside"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by davepal on 2008-09-09
I am trying to steam my music so I don't have to carry everything wherever I go.

This is my current setup : 

```

PC 1 ( 192.68.1.103 ) --
       Ubuntu 8.4          \
       host : karras        \
                             ----  router ----------router ------ internet modem 
                            /
PC 2 ( 192.68.1.101 )  --  /     192.168.1.1     192.168.15.1
        Windows XP           Wan 192.168.15.2

```

I have Ubuntu 8.04, apache2 and jinzora2 running on PC 1, hostname karras. I have Webhop set up in dyndns :

    * Webhop - davepal.homelinux.com - redirect to karras.homelinux.com:8080
    * Host - karras.homelinux.com - with Wan IP of my first router 192.168.15.1

Just because it's not working, I have opened up a lot of ports just to make sure. I have forwarded port 80,443, 8080 tcp, 6600 tcp and udp for jinzora from 192.168.15.1 to 192.168.15.2.

I have forwarded port 80, 8080, 6600 from router 192.168.15.2 ( second router ) to 192.168.1.103 ( my linux box )

In my apache ports.conf i am listening to both 80 and 8080

I can access the website internally, from PC 2, my windows box, by adding "192.168.1.103 karras karras.homelinux.com" in my hosts file. or by "http://karras" or "http://karras.homelinux.com:8080"

 If I try to emulate accessing from outside by removing that entry in hosts, I get connection failed. I am still able to ping both davepal.homelinux.com and karras.homelinux.com.


Any help would be greatly appreciated.

---

### Post by davepal on 2008-09-10
bump

---

### Post by superprash2003 on 2008-09-10
do you have any firewall running?? try this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) .. the complication could be where your two routers are placed.. a better setup would be, having your internet modem to dial the connection with dhcp etc.. and using the other two routers as pure hubs...

---

