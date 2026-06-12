---
title: "Ubuntu Ultimate 1.2 networking problem"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by rhart211 on 2007-03-07
I have installed Ubuntu Ultimate 1.2 and I am having a problem with getting the network to work. I have given the computer a static address. I can see that eth0 has this IP address with 'ifconfig eth0', however, I cannot ping the gateway. Another computer using the same cable and the same network port can ping the gateway, and browse the internet. I thought the problem was network manager, so I removed it and rebooted. I thought the problem was firestarted, so I removed it and rebooted. So I don't know what else the problem could be? Any suggestions.
Thanks

---

### Post by lloyd_b on 2007-03-07
Could you post some additional info?  Specifically:
1. The contents of the file "/etc/network/interfaces"
2. The output from running the "ifconfig" command.
3. The output from running the "route" command.
4. The contents of the file "/etc/resolv.conf"
5. The type of ethernet card (if known)

Some other questions:
1. When you try pinging the gateway, are you pinging it by IP address, or by name?  If the latter, try pinging it by IP address and see what happens.

2.  Can you ping this machine from another machine?

Lloyd B.

---

### Post by rhart211 on 2007-03-07
I got it fixed. It was the port I was using. I used another port and now it works fine.
Thank you.

---

