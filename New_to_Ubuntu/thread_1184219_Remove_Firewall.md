---
title: "Remove Firewall"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Frank_F on 2009-06-10
Hello

Wondering how I can permanently disable or remove firewall. iptables -F is not permenant. Is there a config file I can disable or init.d program I can remove

Thanks

---

### Post by jbrown96 on 2009-06-10
Ubuntu's main firewall is called ufw. Check the status with ```
sudo ufw status
``` If it is loaded you can disable it with ```
sufo ufw disable
```

---

### Post by Frank_F on 2009-06-11
thanks that worked

---

