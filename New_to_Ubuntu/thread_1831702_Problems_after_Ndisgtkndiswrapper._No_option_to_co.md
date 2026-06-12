---
title: "Problems after Ndisgtk/ndiswrapper. No option to connect to a network."
date: 2011-08-23
forum: New to Ubuntu
---

### Post by BlackbirdShaman on 2011-08-23
I used ndiswrapper (well, ndisgtk throught the software center) and used the right driver for my atheros ar5b97, but then I rebooted and now I can't get the option to connect to a wireless network. How can I fix this?\Acer Aspire 5552 laptop, Ubuntu 11.04. I looked around and I think it may not be recognizing my wireless card.

---

### Post by cariboo on 2011-08-24
You shouldn't need ndiswrapper, as there is a native driver fo your wireless chipset, that should be enabled by default. After removing ndiswrapper, reboot and once at the desktop, open a terminal and type:

```
sudo lshw -C network
```

The output of the above command will show you that the device has been detected, and what driver it uses.

If you have any other problems, paste the output of the above command in your next post.

---

### Post by BlackbirdShaman on 2011-08-24
I AM SO HAPPY! Please don't think less of me. Maybe I am an idiot when it comes to Ubuntu. I deleted ndiswrapper.conf and problem solved.

---

