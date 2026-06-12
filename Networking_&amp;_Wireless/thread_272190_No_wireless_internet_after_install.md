---
title: "No wireless internet after install"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by kevindubrow on 2006-10-05
Hi, during using the live CD I could access the internet, but after an install I can no longer do so. I am using a Dell TrueMobile 1180. The device is powered on and being recognised by the computer. I tried doing the Ubuntu Device Database program, but it freezes up when it gets to the networking part. This may be just as simple as making the connection, but I can not find the proper way to do it in any of the programs. Any ideas would be great. Thanks.

---

### Post by kevindubrow on 2006-10-05
Ok, I'm not sure if this gives any ideas, but I have gone to the network setrtings, configured my ip address and such under the  properties of Ethernet Connection (static ip address) and still have no internet. Thanks in advance for any help.

---

### Post by kevindubrow on 2006-10-05
Ok something new:

I typed in "/etc/indit.d/networking" and got this message.

if down: failed to open statefile /var/run/network/ifstate: Permission denied

if up: failed to open statefile /var/run/network/ifstate: Permission denied
                                     [failed]



I believe this has something to do with newtorking, I saw this code on the forums.

---

