---
title: "address leases in DHCP"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by waYYne on 2010-05-23
Hi All,  
how would one browse/ view the address lease of all the ip's? :-?

---

### Post by quadproc on 2010-05-23
> **waYYne said:**
> Hi All,  
how would one browse/ view the address lease of all the ip's? :-?
I am not sure of what you are looking for, but you might find ifconfig useful.  That command will tell you about the system that you are on.

If you are looking for information regarding other systems on a LAN, for example, then you would need to query your switch.  Most of them can be accessed at IP address 192.168.0.1 or something similar to that.

quadproc

---

### Post by iponeverything on 2010-05-23
```
cat /var/lib/dhcp3/dhcpd.leases

```

If you install webmin, it has nice interface for dhcp.

---

### Post by waYYne on 2010-05-23
sorry for my vauge post and thanks for your responses.  So the webmin option is this so that i can  "look from my DHCP Server (Ubuntu running the DHCP3-Server) and view all the pc's currently leasing an IP from me?":redface:   

sorry if that wasnt clear!

---

### Post by sylvester_0 on 2010-05-23
iponeverything gave a good answer. Run that command in a terminal to see all of the current leases. you may also find something like

```
nmap -sP 192.168.1.0/24
```
to be useful.

---

### Post by waYYne on 2010-05-23
cheers guys i knew there must be away without installing stuff :D

---

