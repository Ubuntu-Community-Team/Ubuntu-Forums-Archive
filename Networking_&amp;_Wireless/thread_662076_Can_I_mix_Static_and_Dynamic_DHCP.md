---
title: "Can I mix Static and Dynamic DHCP"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by StewD on 2008-01-08
Hi

I would like to set up my Ubuntu PC to have a static IP address, and could change my Belkin router to switch off the DHCP server.

However other devices connect to the router that must be dynamic as I am not able to set them up with static IP addresses (laptops from work, Nintendo Wii).

My theory to resolve this is to leave the DHCP server switched on, but  increase the "IP Pooling Starting Address" within the Belkin Router configuration from 

xxx.yyy.zzz.1

 to 

xxx.yyy.zzz.5

and then manually set up the Ubuntu machine with an address of xxx.yyy.zzz.2 

Does this make sense? Is it liable to work? Or cause me issues?

Thanks for any thoughts etc!

Stew

---

### Post by reckless2k2 on 2008-01-08
ok...i think you are saying that your server will have an IP not in the DHCP range and that will be fine. like this:

server = 192.168.2.50

DHCP router range is = 192.168.2.100 - 200

that will be fine. sometimes in the routers you can specify certain MAC addresses to get a static IP from the router. whatever.

---

### Post by StewD on 2008-01-08
Thanks, that is what I was trying to say!

Router has an address that the DHCP server can not issue out.

Thanks for the reassurance. Now I just need to spend time researching how to configure Ubuntu to have a static address!!

But thanks again.

Stew

---

### Post by andguent on 2008-01-08
Agreed. As long as the dhcp start and finish do not have any static IP addresses within that range you should be fine.

When changing the range that dhcp gives out, if anyone was using one of the addresses that just dissapeared from the pool, it might be worth giving them a restart. After restart they should get a different address, but you shouldn't really notice any other changes.

---

### Post by andguent on 2008-01-08
There is definitely a GUI option for setting things.

If you prefer the command line, check /etc/network/interfaces

Convert it from this:
auto eth0 inet dhcp

To:
auto eth0 inet static
       address 192.168.1.2
       netmask 255.255.255.0
       gateway 192.168.1.1


Don't forget to check your /etc/resolv.conf (or update DNS server in the GUI tool).

---

### Post by StewD on 2008-01-08
Wow! Thank you. 

I'll have a play tomorrow night and see how I get on.

Thanks again!

Stew

---

### Post by tagno25 on 2008-01-08
> **StewD said:**
> ... I am not able to set them up with static IP addresses (laptops from work, Nintendo Wii).
I understand not being able to set a static ip for the work laptop, but you can on the Wii.

---

