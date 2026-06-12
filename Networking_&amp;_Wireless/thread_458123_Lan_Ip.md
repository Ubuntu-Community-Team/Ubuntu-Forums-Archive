---
title: "Lan Ip"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Mjo890 on 2007-05-29
Quick question, how can I find out my LAN ipaddress?

(192.168.0.10X)

Thanks in advanced.

---

### Post by EndPerform on 2007-05-29
Open up a terminal and type:

```
ifconfig
```

Which will show you your network devices and associated information.  You're looking for the line marked inet addr, and there's your ip address.

---

### Post by Mjo890 on 2007-05-29
> bash: ipconfig: command not found

Hmmm..?

---

### Post by Synflux on 2007-05-29
I**f**config is the command you need, Ipconfig is the Windows version.
Hope that helps :)

Dave

---

### Post by EndPerform on 2007-05-30
yeah, ifconfig is what I had for him to type :)

---

### Post by Synflux on 2007-05-30
> **EndPerform said:**
> yeah, ifconfig is what I had for him to type :)

Yeah I know, I saw you had it right, I just put it in bold for mjo890, didn't mean to take the credit for it :)

---

### Post by EndPerform on 2007-05-30
> **Synflux said:**
> Yeah I know, I saw you had it right, I just put it in bold for mjo890, didn't mean to take the credit for it :)

It's all good :)  Kinda makes me wish they'd alias ipconfig as ifconfig though, I know at first I had done that a couple of times.

---

