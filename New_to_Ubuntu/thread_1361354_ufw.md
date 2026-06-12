---
title: "ufw"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-21
Hello friends

If Firestarter is active do i still have to enable ufw?Thanks for the lecture.

---

### Post by tom.swartz07 on 2009-12-21
> **manny43 said:**
> Hello friends

If Firestarter is active do i still have to enable ufw?Thanks for the lecture.

as long as firestarter says that the firewall is up, I.E. Firestarter says its okay, then youre all set.

you could always check and make sure- open the terminal and type
```
sudo ufw status
```

---

### Post by ramjet_1953 on 2009-12-21
Both Firestarter and UFW are just interfaces, they are not firewalls.

They interface to [COLOR="Red"]iptables[/COLOR] which is the Linux firewall.

Regards,
Roger :)

---

### Post by bodhi.zazen on 2009-12-21
> **manny43 said:**
> Hello friends

If Firestarter is active do i still have to enable ufw?Thanks for the lecture.

Firestarter and ufw conflict. Use one or the other, not both.

---

### Post by manny43 on 2009-12-21
Then how do i know firewall is on?

---

### Post by manny43 on 2009-12-21
Then Ubuntu has its own firewall but i just cant see it.

---

### Post by bodhi.zazen on 2009-12-22
you can see your firewall rules with:

```
sudo iptables -L -v
```

If you use ufw :

```
ufw status
```

You can test your firewall from a second box on your LAN with any number of tools, netstat

---

