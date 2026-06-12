---
title: "iptables info"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Tnoty on 2010-07-23
I want to block access to the 'domain' (53) port using iptables.  Where do I go for information regarding setting up or configuring ip tables.  Thanks

---

### Post by sandyd on 2010-07-23
> **Tnoty said:**
> I want to block access to the 'domain' (53) port using iptables.  Where do I go for information regarding setting up or configuring ip tables.  Thanks
```

iptables -A INPUT -p tcp -i <internal NIC> -s <your IP> --dport 53 -j REJECT

```you also might wanna try firestarter/gufw

---

### Post by Tnoty on 2010-07-23
Trying now thanks much.

---

### Post by sandyd on 2010-07-23
> **Tnoty said:**
> Trying now thanks much.
and if that screws your network up,
```

iptables --flush
```

---

### Post by Ocxic on 2010-07-23
Use this:

iptables -A INPUT -p tcp -i <internal NIC> -s <your IP> --dport 53 -j DROP

using DROP instead of REJECT is a better way of doing it, i believe, as it does dot reply to any incoming packets and will look as if your computer isn't even connected(think stealth mode)

---

### Post by sandyd on 2010-07-23
> **Ocxic said:**
> Use this:

iptables -A INPUT -p tcp -i <internal NIC> -s <your IP> --dport 53 -j DROP

using DROP instead of REJECT is a better way of doing it, i believe, as it does dot reply to any incoming packets and will look as if your computer isn't even connected(think stealth mode)
**shrugs** as a server administrator doesn't matter to me. Theyll see that my computer exists through different ports....

---

### Post by sandyd on 2010-07-23
And I really do hope that didn't cause the OP to lose his/her internet...
since its 1h since he/she tried it.

---

### Post by CharlesA on 2010-07-23
DNS is UDP port 53, not TCP port 53. I don't really know why you'd want to block DNS requests anyhow.

---

