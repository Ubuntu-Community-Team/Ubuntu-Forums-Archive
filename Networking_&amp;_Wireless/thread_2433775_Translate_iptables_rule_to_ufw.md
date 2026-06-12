---
title: "Translate iptables rule to ufw"
date: 2019-12-25
forum: Networking &amp; Wireless
---

### Post by ken35 on 2019-12-25
have a computer with two NICs. One is connected to my DSL modem and the  second to my LAN. Using the NetworkManager applet I set the second NIC  to "Shared to other computers" on the IPV4 tab. Presto a simple but  effective gateway/router etc.

I have a printer which seems to have the capability/tendency to "phone  home." That I do not wish to allow.  The printer has a static IP address  set so it SHOULD be simple to block it at the firewall from accessing  the Internet. I can add a rule with the iptables command which  accomplishes this task and still allows the printer to be accessed on  the LAN.```
iptables -I FORWARD -s 10.42.0.13 -j DROP
``` this  works as desired and I have also tested it with a computer. The blocked  computer cannot access the Internet yet it still can connect to other  computes on the LAN with ssh and it can be connected TO with ssh.

The question is... how do I accomplish this using ufw? I have poked around the documentation and gufw. I am not finding a path to success.

TIA,

Ken

---

### Post by TheFu on 2019-12-25
sudo ufw deny from <ip address>
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by ken35 on 2019-12-26
Thanks TheFu,

Unfortunately that does not work. The computer at 10.42.0.13 can still access the Internet with ping or a web browser. It can also access the firewall computer with ssh.  It LOOKS like it should be doing something```
root@t25-magic:~# ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                 
Anywhere                   DENY        10.42.0.13               
22/tcp (v6)                ALLOW       Anywhere (v6)
```

Ken

---

