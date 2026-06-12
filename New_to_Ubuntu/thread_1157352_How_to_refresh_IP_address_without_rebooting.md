---
title: "How to refresh IP address without rebooting"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by ags40 on 2009-05-12
How should I refresh my IP address without having to reboot? How can I get a pop-up saying that it was interrupted. Thanks to everybody.

---

### Post by XCan on 2009-05-12
Perhaps what you're looking for is:
ifdown eth0
ifup eth0

---

### Post by OffAxis on 2009-05-12
or a 
```

sudo /etc/init.d/networking restart
```

---

### Post by ags40 on 2009-05-12
Thank you very much!

---

