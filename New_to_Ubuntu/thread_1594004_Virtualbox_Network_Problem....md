---
title: "Virtualbox Network Problem..."
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-10-11
I have Ubuntu 10.04 as my host OS and Winxp as my Guest OS using virtualbox.

I want the host and guest to be connected with a virtual network.

I Enabled a network attached to Host-Only adapter. Gave Host Ip as 192.168.2.1 and guest Ip as 192.168.2.2

Tried pinging to each other but ping fails...

I am trying to do this to be able to print to my printer using internet printng on [http://Host:631/printers/hp7000](http://Host:631/printers/hp7000)

Thanks for help in advance.

---

### Post by CharlesA on 2010-10-11
You'd need to use bridged networking for that to work.

---

### Post by Guruprasad on 2010-10-11
Thanks

But where should I enter the host IP 192.168.2.1 in case of bridged adapter?

---

### Post by CharlesA on 2010-10-11
You don't need to. You only need to put the guest on the same subnet as the host.

---

### Post by Guruprasad on 2010-10-11
Sorry.. Now I am totally confused.

Let me expalin clearly...

I have an internet connection for my host which uses DHCP this network is named eth0

I enabled first network adapter for my guest and attached to NAT. this gives me internet on my Guest.

Now I want my guest to print to my printer on host using internet printing at [http://host:631/printers/hp7000](http://host:631/printers/hp7000). For this I started a second network for my guest attached to bridged adapter. Gave Ip for my guest as 192.168.2.1

---

### Post by CharlesA on 2010-10-11
So you don't have a router?

I think the default ip address for the vboxhost networking model is 192.168.56.1.

So if you select "host-only" change the guest's IP to 192.168.56.2 and see if you can ping the host from the guest.

---

### Post by Guruprasad on 2010-10-12
I do not have router.

I changed the vboxhost ip to 192.168.56.1

I selected "host-only", changed the guest ip to 192.168.56.2

Tried pingning from host to guest. But it didnt work.

---

### Post by CharlesA on 2010-10-12
Try setting the guest to use DHCP.

I just tested it on one of my machines and the guest grabbed an ip of 192.168.56.101.

---

### Post by Guruprasad on 2010-10-12
With DHCP the guest gets the IP 192.168.56.101

I kept the host as 192.168.56.1. Still I can not ping eachother.

Do I need to modify subnet mask?

---

### Post by Guruprasad on 2010-10-12
Worked....

I had installed a Firestarter firewall long back.

By stopping the firewall it worked.

Thank you very much CharlesA...

---

