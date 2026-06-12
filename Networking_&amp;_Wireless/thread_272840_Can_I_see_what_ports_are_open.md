---
title: "Can I see what ports are open?"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by Jordan Meeter on 2006-10-07
Hey,

Is there something I can enter into the command line to tell me which ports are open?

Thanks,
Jordan

---

### Post by davesgonebananas on 2006-10-07
To see open TCP/IP ports type

```
netstat -ta
```

To see which program has the port open type

```
netstat -tap
```

To see just server (listening) ports type

```
netstat -tlp
```

---

