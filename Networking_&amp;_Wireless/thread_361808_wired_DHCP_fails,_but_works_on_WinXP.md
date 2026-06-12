---
title: "wired DHCP fails, but works on WinXP"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Illusion65 on 2007-02-14
I have a Toshiba laptop (5 years old) that will not acquire a DHCP address from our ISP via our cable modem.  It works in WinXP, but not in Ubuntu Edgy.  It is connected via CAT5 to a switch, then to the cable modem.  DHCP works on both OS's when connected via crossover cable to a WinXP computer running ICS (Internet connection sharing, so it is serving DHCP on it wired port).

We have 5 computers in total, and they can all receive IP addresses from the cable modem company without any special config.  Another, newer laptop works when running Ubuntu Feisty (also when it was running Edgy and WinXP), but this older Toshiba does not work with the ISP's DHCP server.

Does anyone understand DHCP well enough to have any idea what the differences might be between WinXP and Linux?  I suspect it's protocol related.  The problem laptop is using an Intel 8255X ethernet adapter.

Thanks,
Doug

---

### Post by bnuytten on 2007-02-15
Can you post the output of this command here. Open two terminals, first start tcpdump in one terminal. In the other terminal bring the interface down and up.
```

tcpdump -vvni eth0 udp port 67 or port 68
ifdown eth0
ifup eth0
```

If tcpdump does not output anything, check the device's name (eth0?). You may force DHCP by using
```
dhclient eth0
```

---

