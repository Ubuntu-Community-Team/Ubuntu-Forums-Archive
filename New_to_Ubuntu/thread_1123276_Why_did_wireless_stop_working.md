---
title: "Why did wireless stop working?"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-04-12
My wireless connection wouldn't connect on my Dell Mini9. I kept trying and it wouldn't connect. Finally I restarted and it worked. 

Why wouldn't it connect? Is there anything I can do to fix it when it doesn't connect?

---

### Post by davidgurvich on 2009-04-12
I would guess that there was some update with the reboot clearing the old version from memory.  You can always control an interface from the command line:```
ifconfig INTERFACE_NAME down
modprobe -r INTERFACE_MODULE
modprobe INTERFACE_MODULE
ifconfig INTERFACE_NAME up
```

---

