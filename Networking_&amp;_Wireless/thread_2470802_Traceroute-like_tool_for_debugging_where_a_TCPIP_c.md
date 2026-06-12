---
title: "Traceroute-like tool for debugging where a TCP/IP connection is droped or rejected ?"
date: 2022-01-12
forum: Networking &amp; Wireless
---

### Post by gigi1335 on 2022-01-12
Hi everybody,

Do you know a traceroute-like tool for debugging where a TCP/IP connection is droped or rejected ?

Thanks in advance for your help.

Gilles

---

### Post by The Cog on 2022-01-12
You are probably looking for **tracepath** .

---

### Post by him610 on 2022-01-12
You could also try *mtr* from command line.
```

mtr nmsu.edu

```

---

### Post by gigi1335 on 2022-01-13
Thanks a lot for your answers ! I discovered that tracepath doesn't send TCP packets like traceroute (installed by apt install traceroute) or mtr

Cheers

---

