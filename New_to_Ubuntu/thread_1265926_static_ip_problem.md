---
title: "static ip problem"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by dholcomb on 2009-09-14
[FONT=Verdana][SIZE=1]I am trying to set up an ubuntu machine to host a website (just as a learning experience) and I am having trouble getting it set up with a static ip on the local network. After some googling, I tried changing the /etc/network/interfaces file to this:

[/SIZE][/FONT][FONT=Verdana][SIZE=1]auto eth0
iface eth0 inet dhcp
[/SIZE][/FONT] [FONT=Verdana][SIZE=1]address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.99[/SIZE][/FONT] 

[FONT=Verdana][SIZE=1]After I did this, netowrk manager appears unable to find eth0. If I restart networking, it tells me that it cannot bring up eth0. Firefox no longer works, but I can still ssh to the computer over the network. I think that it maybe cannot find the DNS or something, but I dont know how to fix that. My router is set to get the DNS dynamically fron the ISP, so I cannot put in an IP for it in interfaces. Anybody know what is wrong?[/SIZE][/FONT]

---

### Post by talsemgeest on 2009-09-14
> **dholcomb said:**
> [FONT=Verdana][SIZE=1]I am trying to set up an ubuntu machine to host a website (just as a learning experience) and I am having trouble getting it set up with a static ip on the local network. After some googling, I tried changing the /etc/network/interfaces file to this:

[/SIZE][/FONT][FONT=Verdana][SIZE=1]auto eth0
iface eth0 inet dhcp
[/SIZE][/FONT] [FONT=Verdana][SIZE=1]address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.99[/SIZE][/FONT] 

[FONT=Verdana][SIZE=1]After I did this, netowrk manager appears unable to find eth0. If I restart networking, it tells me that it cannot bring up eth0. Firefox no longer works, but I can still ssh to the computer over the network. I think that it maybe cannot find the DNS or something, but I dont know how to fix that. My router is set to get the DNS dynamically fron the ISP, so I cannot put in an IP for it in interfaces. Anybody know what is wrong?[/SIZE][/FONT]
Assuming the addresses are correct, the only thing you need to change is ```
iface eth0 inet dhcp
``` to ```
iface eth0 inet static
```

---

### Post by mike555 on 2009-09-14
also it helps sometimes to shutdown for a couple minutes so the router can reset (instead of restarting)

---

### Post by The Cog on 2009-09-14
The dns server addresses go in /etc/resolv.conf. Like this example:
nameserver 192.168.1.99

---

