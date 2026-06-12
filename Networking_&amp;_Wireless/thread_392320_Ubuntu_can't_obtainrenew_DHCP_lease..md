---
title: "Ubuntu can't obtain/renew DHCP lease."
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Senesence on 2007-03-24
I'm on Dapper
Cable modem
Optimum Online is my ISP

The lease given by my provider lasts 3 days, after which it has to be renewed, or I can't go online.

Now windows doesn't have any trouble with this. When the lease expires, windows xp automatically renews it, and I'm never bothered.

Ubuntu on the other hand is unable to do so. It doesn't seem to have any automatic features that would renew the lease when needed, however even manual methods don't seem to work, because using dhclient does absolutelly nothing either. This means that every 3 days, I am forced to go back to windows just to get a new lease, after which I can only use ubuntu to surf the web for another 3 days.

How do I get ubuntu to automatically and successfully renew my lease?

TIA

---

### Post by Senesence on 2007-03-24
O, and can anyone tell me how to view the lease obtained/expires dates on Ubuntu?

On windows, they can be found at the end of the ipconfig /all output. I can't seem to find any options for that with ifconfig on ubuntu.

---

### Post by lloyd_b on 2007-03-24
> **Senesence said:**
> O, and can anyone tell me how to view the lease obtained/expires dates on Ubuntu?

On windows, they can be found at the end of the ipconfig /all output. I can't seem to find any options for that with ifconfig on ubuntu.

Take a look at the file "/var/lib/dhcp3/dhclient.leases".

Lloyd B.

---

