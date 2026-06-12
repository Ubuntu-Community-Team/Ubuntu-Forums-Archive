---
title: "Wireless adaptor suddenly not working."
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by kim3 on 2013-10-04
All of a sudden, yesterday the ubuntu and lubuntu wireless connections to my router died. Not died completely. They see the connection, try to connect, use the right password, then ask me to authenticate and input the password again. Using an ethernet cable the connection works instantly.

I have tried with my phone as a mobile hotspot also. As with my PC, my notebook ubuntu/lubuntu sees the network, I used the right password but it never connects, just keeps asking me for the password again.

I have tried deleting the connections, restarting, and of course, the wirless networks are found...but the same problem occurs...

can anyone help me please???

---

### Post by praseodym on 2013-10-04
Is Lubuntu and Ubuntu on the same machine? Please show these terminal outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

