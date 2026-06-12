---
title: "wireless check"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-02
How do I check if I'm the only one on my wireless connection again?

---

### Post by duanedesign on 2010-01-02
On my router i can log into the web interface and see the MAC addresses of computers connected to the network. You can find your computers MAC address using the command

```
ifconfig | grep HWaddr
```

---

### Post by Captain_tux on 2010-01-02
Check your router's wireless settings...

---

### Post by dzon65 on 2010-01-02
> **duanedesign said:**
> On my router i can log into the web interface and see the MAC addresses of computers connected to the network. You can find your computers MAC address using the command

```
ifconfig | grep HWaddr
```

Damn,I forgot.Somehow the text is hardly readable (tried several settings) in the terminal.
Thanks for the replies though.

---

