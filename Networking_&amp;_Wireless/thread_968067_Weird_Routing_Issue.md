---
title: "Weird Routing Issue"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by kenpotf on 2008-11-02
I hope someone can help me. I have two 8.04 laptops (one is full OS, and the other laptop is virtualized in Windows). Both work fine. I have the following router configuration:

Cisco 871W -- Wireless signal to another Cisco 1100 AP -- Cisco 871
192.168.1.1                           192.168.1.2       192.168.1.3

From both linux OSs, I can ping 192.168.1.1, and ping internet addresses (4.2.2.1). I can browse the internet with no problems in either laptop.

From the Windows system, I can ping 192.168.1.1, .2, and .3, with no problems. The Linux boxes will NOT ping the .2 or .3 addresses. Since routing is working in Windows, I doubt it's a Cisco issue. I another linux box that is behind an ASA, and it can ping it okay. I'm not sure what to look at since the Windows pings okay. Anything you guys can suggest will be greatly appreciated!

Oh, my default route is 192.168.1.1, and that can see all devices.

Thanks!
John

---

