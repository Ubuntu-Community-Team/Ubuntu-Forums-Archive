---
title: "Ubuntu 18.04 persistent/permanent ip route and ip rule"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by arya6000 on 2018-06-18
I have the the following ip route and ip rule commands

```
ip route add default via 172.16.11.254 table wlx74da388c32d0
ip rule add from 172.16.11.107 lookup wlx74da388c32d0
```

Ubuntu 18.04 does not use the /etc/network/interface file anymore, it is using netplan, so I can no longer use the interface method of persisting the ip route and ip rule using the interface file.

One of the ways I am considering is by creating a file and putting the commands in there, and then setup cron to run it at boot. Is there a more standard/better way of doing this?

---

### Post by TheFu on 2018-06-18
[https://netplan.io/examples#source-routing](https://netplan.io/examples#source-routing)  - did this not work?

---

### Post by arya6000 on 2018-06-18
> **TheFu said:**
> [https://netplan.io/examples#source-routing](https://netplan.io/examples#source-routing)  - did this not work?

The main connection to the server is done through Ethernet and that interface is listed in the netplan. However the connections that I am setting up ip route and ip rule are wifi connections that I connect to using the nmuti command, the wifi interface is not listed in the netplan file. 

I have not tried adding the ip route and ip rule inside the netplan file since it was for a different interface. I will try that to see if it works.

---

### Post by TheFu on 2018-06-18
Server with wifi?  How odd.  None of my servers have any wifi-anything.
You can manually add routes in a "post-up" method, but I think that was broken in the initial release of 18.04.  I haven't seen that it is or isn't fixed. [https://netplan.io/faq#use-pre-up-post-up-etc-hook-scripts](https://netplan.io/faq#use-pre-up-post-up-etc-hook-scripts) ...  there is a table that seems to say using routable.d stuff (part of networkd) is the new technique.

As long as you don't use network-manager, you should be able to add routing commands to the wifi-up stuff at boot.

And worst case, you can add route commands to rc.local, which is still a hack, but at this point, if it works, that's enough. ;(

Looking over all this stuff, I'm glad I haven't moved any servers to 18.04. Thanks for taking the pain as an early adopter. Much appreciated.

---

