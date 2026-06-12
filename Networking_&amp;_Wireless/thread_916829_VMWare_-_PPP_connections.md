---
title: "VMWare - PPP connections"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by j0natz on 2008-09-11
Hi, 

I'm using Ubuntu 8.0.4.1 on a Dell Latitude D420.

Everything works fine but VMWare :)

What I want to do is the following:

To use a Windows (for work) on my Laptop I've setup it on VMWare Server.

It works great with eth0 and wlan0. 

If I try to add ppp0 as a additional device so VMWare can use my 3G connection VMWare doesn't start anymore.

Can somebody help me with this please?

Best regards

Jonas

---

### Post by j0natz on 2008-09-12
Nobody ever had this before? 

Or is my problem not really clear?

---

### Post by NoReflex on 2008-09-12
How did you setup the connection for the virtual machine? I always used shared networking with virtual machines and it worked no matter how I connected to the internet (eth, wlan, ppp (3G)).
That being said I really recommend VirtualBox (I use it with Ubuntu(host) and XP(guest)) and I'm very happy with it.

Best wishes,
NoReflex

---

### Post by dmizer on 2008-09-12
Have you reconfigured vmware to include your ppp device for NAT or host-only? A "bridged" connection probably won't work for your ppp connection.

---

