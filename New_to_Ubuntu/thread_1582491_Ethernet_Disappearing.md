---
title: "Ethernet Disappearing"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-09-26
So I have a laptop, and I have access to wifi 24/7 basically, but as wifi is wifi and linux is linux, it's pretty unreliable at keeping a steady pace. So streaming video and massive downloads tend to go wonky. So I have an ethernet setup at home for handling this. When I first turn the laptop on, plug ethernet it, it works like a charm. However, I think this is usually caused when I close the lid (suspend the session) ethernet stops working. ifconfig doesn't even recognize that I /have/ ethernet (it only shows local and wireless). Reboot and ethernet comes back.

How can I prevent this?

---

### Post by Iowan on 2010-09-27
One option is to change the action when the lid is closed. (I'll need to fire up my laptop to find where the option is located...)

---

### Post by Delkster on 2010-09-27
> **Iowan said:**
> One option is to change the action when the lid is closed. (I'll need to fire up my laptop to find where the option is located...)

It should be in System > Preferences > Power Management.

However, if using suspend is actually desirable, it might be a good idea to try and figure out if we can get your ethernet driver to survive over suspend/resume rather than make the laptop not suspend. Zeppelin, could you open a terminal (Applications > Accessories > Terminal) and run the following command in the terminal?

```
lspci
```

The command lists your PCI devices. One of the output lines should mention your ethernet controller. Copy and past the output of the command here.

---

### Post by Zeppelin! on 2010-09-30
Suspend is desirable, I have miserable battery life. Hibernate breaks about 50/50 and is painfully slow either way, so is useless.

lspci output:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

