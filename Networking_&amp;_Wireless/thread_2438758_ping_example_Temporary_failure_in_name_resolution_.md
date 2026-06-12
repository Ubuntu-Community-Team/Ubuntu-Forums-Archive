---
title: "ping: example: Temporary failure in name resolution ,Ubuntu Server 18.04.4 LTS"
date: 2020-03-17
forum: Networking &amp; Wireless
---

### Post by erikbraun1242 on 2020-03-17
I have a custom DNS server that i did setup in the Ubuntu Server 18.04.4 LTS.It can access the web(found that out trying to install something).Every other pc can use the custom hostnames i have setup in Pi-hole(which i use as DNS and DHCP),also my doamin is .local.

Thanks in advance,
Erik

---

### Post by pcfan1234 on 2020-03-22
How did you configure it?
Show the content of 
```

/etc/resolv.conf
systemd-resolve --status |grep Server

```

---

### Post by alsala on 2020-03-24
What's the use case to have a DNS server running in the Ubuntu box and the pi-hole one in the same network?
Unless there's a reason the easiest way forward would be to use only the pi-hole and disable dns server in your ubuntu.

---

