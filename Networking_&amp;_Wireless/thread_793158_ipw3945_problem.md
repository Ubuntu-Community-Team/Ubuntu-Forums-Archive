---
title: "ipw3945 problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by anarki007 on 2008-05-13
Hello, i need some help over here,
i got a wireless bug after upgrading to kubuntu 8.04, kernel 2.6.24-17-generic, I cant connect throw wireless or even see the wireless, i follow some threads in many forums and i got nothing
my wireless card driver is ipw3945 (using hp pavilion dv2775cc)
i reinstalled the driver and done alot of works at the last 2 days please some one help me.
Thanks

---

### Post by nixscripter on 2008-05-14
Have you tried upgrading to the iwl3945 driver? When my wireless card was having various annoying problems, I discovered that the ipw3945 driver is a little dated.

If the command ```
modprobe iwl3945
``` driver works (I think that driver is installed by default), then add it to /etc/modules, and blacklist the other one:

```

echo "ipw3945" >> /etc/modprobe.d/blacklist
echo "iwl3945" >> /etc/modules

```

Also, you will have to do those two things as root. You may also have to remove the **ipw3945** entry from /etc/modules.

Hope this helps.

---

