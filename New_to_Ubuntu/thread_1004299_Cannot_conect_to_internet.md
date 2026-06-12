---
title: "Cannot conect to internet"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-12-07
I cannot connect to Internet:
dmesg: [http://pastebin.ubuntu.com/81824/](http://pastebin.ubuntu.com/81824/)
ifconfig: [http://pastebin.ubuntu.com/81825/](http://pastebin.ubuntu.com/81825/)

---

### Post by chuckyp on 2008-12-07
Looks like you connected to the router and getting an ip of 192.168.1.2.  Perhaps try pinging the router. Also some more information would help. Has this ever worked? What are you trying to use to connect i'm assuming its the gigabit card in dmesg? Whats your network set up like DHCP?

Also maybe its a just a dns problem try:
```

$ ping 4.2.2.1

```

See if you get any replies.

---

### Post by jamil_1 on 2008-12-07
I can ping the router. It used to work before an improper restart due to power failure. I realtek ethernet card. Internet is working fine in windowsXP. I can ping IPs but not domains so may be DNS config problem.

---

