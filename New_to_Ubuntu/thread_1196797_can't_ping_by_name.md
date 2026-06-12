---
title: "can't ping by name"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ant2ne on 2009-06-25
My squid server is running ubuntu8.04. It can not be resolved by name. We have a mostly windows network with a Windows2003 server as Active Directory and DNS. From the ubuntu box I can ping anything by name. But nothing can ping the ubuntu box by name. I can ping the ubuntu box by IP. Is there some configuration that I'm missing so this machine's IP will be automatically registered in our Win2003 DNS server?

```
administrator@AHSPX01:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
$auto eth0
$iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 10.60.254.14
netmask 255.255.255.0
gateway 10.60.254.1
broadcast 10.60.254.255
network 10.60.254.0
administrator@AHSPX01:~$
```

---

### Post by prshah on 2009-06-25
> **ant2ne said:**
> 
auto eth0
iface eth0 inet static
address 10.60.254.14
netmask 255.255.255.0


Given that you have set a Static IP address, it is very likely that the DNS server is not registering the name.

I suggest you add it manually to the "hosts" file in your DNS server, or on each client computer.

---

### Post by jimv on 2009-06-25
I had this issue with my home machines...it turned out that Avahi was the culprit.  Try removing Avahi and then reboot.

sudo apt-get remove avahi-daemon

---

### Post by ant2ne on 2009-06-25
> **jimv said:**
> I had this issue with my home machines...it turned out that Avahi was the culprit.  Try removing Avahi and then reboot.

sudo apt-get remove avahi-daemondid that, rebooted, still no luck.

---

### Post by Cheesemill on 2009-06-25
Sounds like you just need to add a DNS record for it on your Windows server.

---

### Post by ant2ne on 2009-06-25
Shouldn't DNS just add a record for that device. I'll admit that I'm not real savvy on the ins and outs of DNS, I've just set it up and it just worked.

---

### Post by wojox on 2009-06-25
Add a 015 DNS Domain Name to your server options with yourdomain.local as the data. This is the option that tells the non windows machines what domain name they should have.

---

### Post by Cheesemill on 2009-06-25
Nope, it doesn't happen automatically if the machine has a static IP.

Windows machines send a DNS update request to the server via the Microsoft DHCP client service.  For your Ubuntu server you're going to have to update the DNS records manually.

It's not hard, just log on the the DNS server and go to Administrative Tools > DNS
Drill down into your domain until you see the list of records and then just right click and select 'Add new A record'. Enter your servers name and IP details and click OK. If you check the 'Create associated PTR record' box then it will add a reverse lookup record automatically for you as well.

---

### Post by ant2ne on 2009-06-29
> **wojox said:**
> Add a 015 DNS Domain Name to your server options with yourdomain.local as the data. This is the option that tells the non windows machines what domain name they should have.
How do I do this?

> Windows machines send a DNS update request to the server via the Microsoft DHCP client service. For your Ubuntu server you're going to have to update the DNS records manually.DHCP server is a MAC, DNS server is a Windows, and the client is ubuntu. I assume that a Windows Machine with a static address would get its IP recorded with the Windows DNS.

---

