---
title: "how to enable ipv6"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by snake444 on 2007-07-07
Hi, my isp doesnt support ipv6 and i want to install ipv6 support so i can join to efnet with vhost
some people told me to register to btexact tunnel
can someone say to me what i need to do now?
im using the 7.04 ubuntu and im beginner in linux and dont say that i dont need ipv6 because i want it;)

---

### Post by linuxwizard on 2007-07-07
IPv6 is turned on by default

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

---

### Post by snake444 on 2007-07-07
but my isp doesnt support ipv6 so i get ipv4 adress when i connect to the internet and to efnet
so how do i use ipv6 trought tunnel brocker?

---

### Post by spd106 on 2007-07-07
You need to register with a tunnel broker and set up a 6 in 4 tunnel. BT exact will provide this service, so go sign up [https://tb.ipv6.btexact.com/start.html](https://tb.ipv6.btexact.com/start.html)

The help pages on that site are quite good and they will email you a script that should work with a little tweaking, though I didn't manage to get it working when I tried a few months back. Something to do with port forwarding on my router not working right. Since then I haven't had time to go through it again.

It's meant to be a testing ground, so service isn't guaranteed and I'm not sure how long BT exact is going to stay open for. If you are not in the UK then there may be a better tunnel broker closer to you.

---

### Post by snake444 on 2007-07-08
i downloaded the script and since i dont have any eth1 device i changed all eth1 words to eth0 in the script
now when i run the script i get:
snake@delta:~/Desktop$ sudo sh LinuxScript.sh
SIOCSIFADDR: File exists
IPv6 configuration failed!
what do i need to do?

---

