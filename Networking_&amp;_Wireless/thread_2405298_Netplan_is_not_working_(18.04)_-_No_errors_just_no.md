---
title: "Netplan is not working (18.04) - No errors just no route/connection."
date: 2018-11-03
forum: Networking &amp; Wireless
---

### Post by uufor44400aa12 on 2018-11-03
I've been using Ubuntu since inception and have recently found out   about Ubuntu's switch to using netplan vs it's traditiona  /etc/network/interfaces method.  


  I'm attempting to get this to work but it simply isn't working.    Based on what I can tell, there is no default route, or possibly even a   bad netplan (though ./netplan apply runs correctly). Below is what I'm   doing:


  
[LIST]
[*]Clean/brand new 18.04.1 install on ESXi
[*]Interface is named ens160
[*]My IP Address 247.235.60.161
[*]My Gateway is 247.235.38.51
[*]My subnet mask is 255.255.255.255
[/LIST]


 /etc/netplan/01-netcfg.yaml:


  ```
network:
  version: 2
  renderer: networkd
  ethernets:
          ens160:
                  dhcp4: no
                  addresses: [247.235.60.161/32]
                  gateway4: 247.235.38.51
                  nameservers:
                          addresses: [8.8.8.8,8.8.4.4]

```

 When I run "netplan apply" it completes successfully.  If I do with the --debug switch, nothing jumps out (see here: [https://i.imgur.com/aViBohG.png](https://i.imgur.com/aViBohG.png)  ).   "ip link" shows this:  [https://i.imgur.com/Scs7Frv.png](https://i.imgur.com/Scs7Frv.png)


  If I ping 8.8.8.8 I get a "SIOCADDRT: Network is unreachable"


  If I do a "route" to view my routing table, it returns with nothing.  No routing table.  This definitely is an issue.


  If I do an "ifconfig -a" it displays my ens160 interface, correct IP,   netmask of 255.255.255.255, no broadcast address, the mac/ether address   is correct.


  With regards to the addressing/gw/sn, I can confirm that is correct   (I have other hosts running with same/similar on this network/ESXi  server). 


  Something is definitely wrong with netplan.  Any ideas?


  Thanks very much for your help!

---

### Post by chili555 on 2018-11-04
> addresses: [247.235.60.161[COLOR="#FF0000"]/32[/COLOR]]With this subnet mask, you won't be able to reach the gateway. I suggest that you change to:```

addresses: [247.235.60.161/18]


```Then do:```
sudo netplan generate
sudo netplan apply
```Reboot and check.

---

