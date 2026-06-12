---
title: "IPv6 issue"
date: 2019-04-15
forum: Networking &amp; Wireless
---

### Post by risonwung on 2019-04-15
I am using Ubuntu 16.04 LTS . After installed Radvd to get Router advertisement work, i found that the ping can only reach to ipv6 link-local address(self own or others ).
When ping global ipv6 address  or even loopback address ::1 ,it returns “ping: unkown host xxxxxx” right away. 
BTW, ping to ipv4 address are all OK.
That is WHY? How to fix this?

Thanks very very much.

---

### Post by wildmanne39 on 2019-04-15
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by risonwung on 2019-04-15
I did same processes on two machines and got same reault.

---

### Post by SeijiSensei on 2019-04-16
Do you need to support IPv6?  I'll often disable it entirely by adding the lines

```
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1

```

to the bottom of /etc/sysctl.conf and rebooting.

---

### Post by chili555 on 2019-04-17
Are you quite confident that your router supports IPv6, as well as your internet appliance (cable modem, DSL modem, etc.) and your ISP? Do other devices on the same network get a real IPv6 address like this?```

5: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 5c:c5:d4:0e:64:a6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.xx/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 171816sec preferred_lft 171816sec
    [COLOR="#FF0000"]inet6 2600:1700:xxxx839:4547:4c4b:71f4:4d6c/64 [/COLOR]scope global temporary dynamic 
       valid_lft 603818sec preferred_lft 85364sec
    [COLOR="#FF0000"]inet6 2600:1700:xxxx839:ed1a:bd8d:e5a:17ef/64 [/COLOR]scope global dynamic mngtmpaddr noprefixroute 

```Or do they get fe80xxx place-holder addresses?

---

### Post by VMC on 2019-04-17
> **SeijiSensei said:**
> Do you need to support IPv6?  I'll often disable it entirely by adding the lines

```
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1

```

to the bottom of /etc/sysctl.conf and rebooting.
I use this to prefer ipv4 over ipv6:
```
sudo sed -i 's/#\(.*96  100.*\)/\1/' /etc/gai.conf
```

---

