---
title: "Problems with iptables in ubuntu 12.04 LTS Server"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by chunny74 on 2013-11-06
I have to add the following line to iptables.

```
iptables -A jk2_ddos -m u32 ! --u32 "0x1c=0xffffffff" -j ACCEPT
```

I get this error message:

iptables v1.4.12: u32: option "--u32" cannot be inverted.

How can I fix this. I'am a total noob, please help.

Thanks,
Oliver

---

### Post by SeijiSensei on 2013-11-08
What exactly are you trying to do?  Perhaps there's a simpler way to write this rule.

---

