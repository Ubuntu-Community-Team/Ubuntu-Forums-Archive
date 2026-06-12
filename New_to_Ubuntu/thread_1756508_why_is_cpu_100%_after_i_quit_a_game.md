---
title: "why is cpu 100% after i quit a game ?"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by neil_1 on 2011-05-12
After i quit Urban terror ,i see that the laptop became slower and when i checked the system monitor , the cpu was 100%
why is this ?
any way to free it without restarting ?

---

### Post by TeoBigusGeekus on 2011-05-12
Run top (or, even better, htop) to see what's eating up your cpu.

---

### Post by neil_1 on 2011-05-12
> **TeoBigusGeekus said:**
> Run top (or, even better, htop) to see what's eating up your cpu.
hmm..
ioUrTded.i386 100% cpu :(
its the server for UrT ,how do i kill it ? it dosnt show up in system manager

---

### Post by kaldor on 2011-05-12
Use the kill command. Run "ps ax" to view the list of processes. The number on the far left row for UrT is what you want to find. So, if UrT shows as "1050", you will run:

```
kill -9 1050
```

---

### Post by TeoBigusGeekus on 2011-05-12
...or
```
killall -s 9 ioUrTded.i386
```

---

### Post by neil_1 on 2011-05-12
ok it worked , thanks guys :)

---

