---
title: "Connection To Internet"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-01-26
Hi,

good day. currently I have one rounter that is permenently to connect to internet, then I using the RJ45 network connection to connect to internet. but after i configure the network setting at /etc/network/interfaces, then i can ping our rounter. but i try to ping [www.google.com](www.google.com), it will return "ping:unknown host google.com.my". 

At the following is network setting at :

figure 1 : /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eht0 inet static

     address 192.168.1.218
     netmask 255.255.255.0
     network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.1

======================================

figure 2 : route -n

Destination     Gateway       Genmask          Flags     Metric     Ref     Use     Iface
192.168.1.0    0.0.0.0          255.255.255.0    U         0            0        0        etc0
0.0.0.0           192.168.1.1   0.0.0.0              UG       0            0        0        etc0

---

### Post by manokaran on 2007-01-26
You will have to add the address of a nameserver to your /etc/resolv.conf file.

regds,
mano

---

### Post by voltage on 2007-01-26
> **manokaran said:**
> You will have to add the address of a nameserver to your /etc/resolv.conf file.

regds,
mano

Hi, 

Thank for your reply. may I know how do i setting of the /etc/resolv.conf ? Do you have any sample ?

There for, may I know how to add routing manually, then the setting still remain after restart the Ubuntu.

Thanks

---

### Post by manokaran on 2007-01-26
Sorry I was vague :-)

I do not know the nameserver ip address of your ISP. However, you can use 4.2.2.2 . Howver, please be advised that it is insecure to use untrusted dns ip like the above. Get the nameserver ip of your ISP asap.

OK.Having got the ip address open /etc/resolv.conf using vi or gedit. You'll have to sudo for this:

sudo gedit /etc/resolv.conf

You might find some entries already existing there - probably like 192.168.1.1 - your routers IP!! Anyway, add the following to the top:

nameserver 4.2.2.2

if you have got your ISP's ip add then substitute that for 4.2.2.2

Nothing more to be done. No restarting required. 

Hope this helps.

regds,
mano

---

### Post by voltage on 2007-01-26
Thanks For All ... I get the link done ..Good Day

---

