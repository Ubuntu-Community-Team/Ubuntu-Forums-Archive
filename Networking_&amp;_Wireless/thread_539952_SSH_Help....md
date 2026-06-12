---
title: "SSH Help..."
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by aten on 2007-08-31
MacBook:~ Twesh$ ssh admin@127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused
MacBook:~ Twesh$ ssh admin@192.168.0.100
ssh: connect to host 192.168.0.100 port 22: Operation timed out
MacBook:~ Twesh$ ssh admin@192.168.0.102
ssh: connect to host 192.168.0.102 port 22: Connection refused


ubuntu says:
inet addr:127.0.0.1 Mask:255.0.0.0

but Ubuntu is running on my windows box under vmware, but it is set as a "NAT:Used to share the hosts IP Address " my windows box ip address is 192.168.0.102

---

### Post by scxtt on 2007-08-31
you'd have to bring up an interface on the Ubuntu VM ... you can't connect via ssh to the Ubuntu loopback (lo) device ... i use bridged networking for my VMs - so i can assign them IPs right off my router ...

---

### Post by zyth on 2007-08-31
Do you have openssh-server installed?

> 
sudo apt-get install openssh-server


---

### Post by aten on 2007-08-31
> **zyth said:**
> Do you have openssh-server installed?
yup

---

### Post by aten on 2007-08-31
> **scxtt said:**
> you'd have to bring up an interface on the Ubuntu VM ... you can't connect via ssh to the Ubuntu loopback (lo) device ... i use bridged networking for my VMs - so i can assign them IPs right off my router ...

I now have it set as Bridged but i dont see any thing on my routers dhcp list except for the computer it self...

---

### Post by scxtt on 2007-08-31
what's the output of:

cat /etc/network/interfaces

on the ubuntu VM?

---

### Post by aten on 2007-08-31
when i try to ping something it says network unreachable... im going to do a fresh install thanks for the help!

---

