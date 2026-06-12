---
title: "Allow a range of ports in ufw"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Dangerousdave26 on 2008-08-11
Is it possible to allow a range of ports in ufw

The server guide for 8.04 shows the allow command as 

sudo ufw allow xxxx

I would like to allow ports 2302 to 2400 with out entering each one individually.

---

### Post by jimv on 2008-08-11
```
ufw allow|deny [proto <protocol>] [from <address> [port <port>]] [to <address> [port <port>]]
```

[https://wiki.ubuntu.com/UbuntuFirewall#Command-line%20Interface](https://wiki.ubuntu.com/UbuntuFirewall#Command-line%20Interface)

---

### Post by guywithcable on 2009-07-20
> **Dangerousdave26 said:**
> Is it possible to allow a range of ports in ufw

The server guide for 8.04 shows the allow command as 

sudo ufw allow xxxx

I would like to allow ports 2302 to 2400 with out entering each one individually.

```
ufw allow proto tcp to any port 2302:2400
```

---

