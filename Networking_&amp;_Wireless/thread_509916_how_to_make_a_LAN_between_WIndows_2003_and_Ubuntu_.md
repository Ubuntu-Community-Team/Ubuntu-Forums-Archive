---
title: "how to make a LAN between WIndows 2003 and Ubuntu linux?"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by linkstack on 2007-07-26
My computer's OS is Ubuntu and it's local IP address is 192.168.0.1,another computer's OS is windows 2003 and it's IP address is 192.168.0.5,how to make a LAN between the two?

---

### Post by Koybe on 2007-07-26
Just plug them on the same hub/switch. It's done.

If you mean how do I share data in my LAN? Then you should turn a look to samba.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by linkstack on 2007-07-26
I don't have any hubs or switchs.
My computer has two NICs.one line is connected with modem,and another line is connected with another computer.
On my computer,I ping 192.168.0.5,it's no use,on another computer,I ping 192.168.0.1,it's no use either.

---

### Post by yota on 2007-07-26
If you directly connect two computers without an hub or a switch you have to use a "crossed" cable (a cable with some wires twisted).

---

