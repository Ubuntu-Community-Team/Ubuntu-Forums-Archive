---
title: "How do you know if you are NOT using IPV6?"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-08-21
I have read some threads about how disabling ipv6 would take care of some of the network problems, such as connection slowing down for no reason, etc

How does one find out if ipv6 is in use?
Thank you!

---

### Post by linuxwizard on 2007-08-21
in terminal > ip a | grep inet6 

If there's no output, IPv6 is disabled. 

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by tak1150 on 2007-08-21
Thanks for your reply and link.

```
    inet6 ::1/128 scope host 
    inet6 fe80::20f:1fff:fe28:2863/64 scope link 

```

This is the output. Does this mean I should not disable ipv6?
Or if I'm using ipv6 correctly already, should I disable ipv4?
Thanks!

---

### Post by linuxwizard on 2007-08-21
tak1150> How does one find out if ipv6 is in use?

That command I gave shows ipv6 is in use.

---

### Post by tak1150 on 2007-08-22
Yes, you've totally answered my question. Thank you.

I did not say and only implied that I wanted to know if I have ipv6 is in use so that I can assess whether or not I can disable it for the purpose of improving my network and overall hardware usage (esp. CPU).

I suppose I'm drifting off to another topic perhaps, but anybody know the answer?
Thank you!

---

### Post by linuxwizard on 2007-08-22
You could disable IPV6 and try it see if it works for you. I have done it in Dapper Ubuntu/Kubuntu & Edgy Ubuntu/Kubuntu I could not see any difference. I didn't change it in Feisty Ubuntu/Kubuntu. I have seen others talk about how it helped with connection issues and others no change.

---

