---
title: "static IP"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by DiJEH on 2006-09-15
Is there any easy way to set up a static IP? I'm not too confident in editing important files and most tutorials seem to suggest I must..

---

### Post by tagra123 on 2006-09-15
> **DiJEH said:**
> Is there any easy way to set up a static IP? I'm not too confident in editing important files and most tutorials seem to suggest I must..

From the Panel Menu: System > Administration > Networking 

Click on etho  and select static and enter your info.

---

### Post by DiJEH on 2006-09-15
I did that and then my router refused to let me access the internet. Doesn't seem to want to be nice :(

---

### Post by wieman01 on 2006-09-15
You have to change your router's settings as well of course. Currently it's set to DHCP, if you need static IPs then you'll have to change that on both ends.

---

### Post by tagra123 on 2006-09-15
> **DiJEH said:**
> I did that and then my router refused to let me access the internet. Doesn't seem to want to be nice :(

Fair enough:

Go to System > Administration > Networking  and click on the DNS Server.

Entering your router's address will usually work here but I find it quicker to enter my IP Providers DNS Servers addresses. 


You router should store these addresses somewhere depending on the model. It will be listed dns server. Just copy these and enter them into the above box.


Also make sure to set the static ip outside your router assigned range. Most, if not all routers allow you to limit the assigned ip range.

---

