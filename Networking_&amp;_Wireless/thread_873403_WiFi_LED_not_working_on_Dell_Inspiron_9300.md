---
title: "WiFi LED not working on Dell Inspiron 9300"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by psimeson on 2008-07-29
Hi, I am new to Ubuntu and just installed Ubuntu 8.04 on my Dell Inspiron laptop. Everything is working smoothly, however the WiFi LED does not turn on even though wireless network card is working. How can I fix this? thankyou.

---

### Post by dileepdinesh on 2008-09-27
try this command 
>>touch /etc/modprobe.d/ipw2200 && echo options ipw2200 led=1 > /etc/modprobe.d/ipw2200


this command will a line options ipw2200 led=1 on the above file
it  should work fine now

---

### Post by psimeson on 2008-10-22
thanks it works now. however when i turn off the wireless suing Fn+F2 keys it still stays on until shutdown. But if i turn it again LED goes off and come back again. thanks again

---

