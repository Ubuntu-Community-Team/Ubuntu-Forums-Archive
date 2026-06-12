---
title: "help me"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by phanindra on 2010-03-24
i've installed ubuntu 9.10 newly.
after that i activated my nvdia graphic card driver so that i can use it after that it asked me to restart. so i did restart. when i restarted there is no video display rest of the system is working. how to make my system well.

---

### Post by NightwishFan on 2010-03-24
Hold in shift while booting a choose recovery mode. When in recovery mode choose drop to a root shell prompt and run this command.
```
jockey-text -d xorg:nvidia-185
```

Then when thats done type:
```
reboot
```

---

