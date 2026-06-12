---
title: "Allow incoming connection from a Subnet (ufw)"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2014-09-09
Hi,

I want to open a port to this specific subnet 172.16.0.0/24.

I read the [community doc. ]("https://help.ubuntu.com/community/UFW")

This is the command to allow incoming connections from a subnet

> **Allow by Subnet**

 You may use a net mask : 
sudo ufw allow from 192.168.1.0/24

But seems like the above ^^ command will open all ports to that subnet. I want to open only  a single port.

I tried this but didn't work
 
```
sudo ufw allow from 172.16.0.0/24 any <port>
ERROR: Wrong number of arguments
```

What is right command ?

---

### Post by steeldriver on 2014-09-09
That would be

```

sudo ufw allow from 172.16.0.0/24 **to** any **port** <port>

```

I think

---

### Post by linuxyogi on 2014-09-09
Worked ! Thanks.

---

