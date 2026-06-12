---
title: "Soft reset failed device not ready"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-28
During boot up right after grub tells me its loading i get an message Soft reset failed device not ready, something about sata, its hard to read because it doesnt stay there very long, is this anything to be worried about. i only have one sata drive and thats my main hdd

---

### Post by Iowan on 2009-10-28
My laptop does that, too... but I get two messages.
 Machine still works fine. 
(so far...)

---

### Post by cariboo on 2009-10-28
You can do a search of dmesg or /var/log/messages to see if anything stands out. Open a terminal and type:

```
dmesg | grep reset
```

and

```
cat /var/log/messages | grep reset
```

---

