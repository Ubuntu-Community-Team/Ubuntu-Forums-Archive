---
title: "Network configuration"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by capempe on 2011-01-28
Dear all, i'm struggling with network card configuration. when i use dchp configuration, on my desktop machine using ubuntu 10.4, i can access the internet, but when i config it with a static ip address i can ping other computers on the LAN, but i can't browse the internet. Can someone help me ssolve this problem? Thanks in advance

---

### Post by [Snc] on 2011-01-28
With non DHCP settings, you also have to supply the Netmask, Gateway and DNS IPs

---

### Post by alphacrucis2 on 2011-01-28
> **capempe said:**
> Dear all, i'm struggling with network card configuration. when i use dchp configuration, on my desktop machine using ubuntu 10.4, i can access the internet, but when i config it with a static ip address i can ping other computers on the LAN, but i can't browse the internet. Can someone help me ssolve this problem? Thanks in advance

That would indicate that you haven't set the default gateway to point at your internet router. What does ```
route -n
``` say.

Eg. Here is route -n on my machine

```
 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0

```


The 0.0.0.0/0  route listed on the last line is the default route which has 10.1.1.1 as its' gateway. That is the address of my internet router. You can set the gateway by editing the connection in network manager.

---

### Post by dineshs on 2011-01-28
+1 to alphacrucis2
If you are using Network manager you should hit enter after assigning IP ,mask and gateway .Please see postcount 9 and 10  [here ]("http://ubuntuforums.org/showthread.php?t=1555373&highlight=gateway")

---

### Post by tdapower on 2011-01-28
This was a problem for me also, but I add my gateway ip address to DNS servers field. so then after I could able to access internet. good luck:guitar:

---

### Post by alphacrucis2 on 2011-01-28
> **tdapower said:**
> This was a problem for me also, but I add my gateway ip address to DNS servers field. so then after I could able to access internet. good luck:guitar:

I also set the DNS and gateway to point at my internet router as it operates as a DNS forwarder. If the OP's router doesn't operate as a DNS forwarder, it will be necessary to put in the addresses of one or more real DNS servers, usually your ISP's.

---

### Post by [Snc] on 2011-01-28
> **alphacrucis2 said:**
> I also set the DNS and gateway to point at my internet router as it operates as a DNS forwarder. If the OP's router doesn't operate as a DNS forwarder, it will be necessary to put in the addresses of one or more real DNS servers, usually your ISP's.

If you cannot get your ISPs DNS servers, you can use google's DNS service, the address is 
```
8.8.8.8
```
Works perfectly for me :)

---

