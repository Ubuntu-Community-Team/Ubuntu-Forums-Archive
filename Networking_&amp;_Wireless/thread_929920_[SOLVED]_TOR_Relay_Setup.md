---
title: "[SOLVED] TOR Relay Setup"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Yuki_Nagato on 2008-09-25
Am trying to setup a TOR Relay.

It keeps spitting back this error:

```
Sep 25 13:45:35.560 [warn] Your server (XXX.XXX.XXX.XXX:443) has not managed to confirm that its ORPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.
Sep 25 13:45:35.560 [warn] Your server (XXX.XXX.XXX.XXX:80) has not managed to confirm that its DirPort is reachable. Please check your firewalls, ports, address, /etc/hosts file, etc.

```

I run:

```
sudo nmap -sT -O localhost

```

and get back:

```
80/tcp   open  http

443/tcp  open  https

(This is edited)

```

Expected.  But, why cannot TOR get through here?

---

### Post by mrsteveman1 on 2008-09-25
Firewall somewhere? Lots of ISPs block port 80 too, and perhaps 443.

---

### Post by Yuki_Nagato on 2008-09-25
Alright.  Any ideas on what ports should be open for incoming connections?

I imagine the mail and SSH ports are also closed.

---

### Post by rocketero2008 on 2009-02-23
Same problem here, and after google-ing a lot I finally discover that my ISP (VerizonDSL) blocks INCOMING ports 80 and 443 by issuing the command:

# sudo nmap -sT -O localhost

which will show you all open ports in your system.

I also tried to forward por 80 and 443 to ports 9030 and 9001 respectively on my ISP's modem webpage configuration (set on private address 192.168.1.1) but that didn't work.

any suggestion would be appreciated.

---

