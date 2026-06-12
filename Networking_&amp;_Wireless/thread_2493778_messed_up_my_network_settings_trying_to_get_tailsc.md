---
title: "messed up my network settings trying to get tailscale running"
date: 2023-12-24
forum: Networking &amp; Wireless
---

### Post by patwashere on 2023-12-24
Hi  Guys, was messing around last night trying to get tailscale to work  with my ubuntu desktop server.   It stopped responding to pings etc  after I updated an ip rule.  I am hoping someone could help me back that  change out or know how to fix it.
  Right now the box is up and running, but will not respond to pings on  either of it's network cards ip addresses.   I can sign onto the box  and ping other devices. Also some docker containers still seem to work.    I have frigate installed and get notifications via homeassistant  (running on a vm).   I have shutdown tailscale to try and eliminate that  from the scope.


  the change I believe caused the problem is:

  ```
ip rule add to 192.168.2.0/24 priority 25000 lookup main


```  
I am very new to linux networking and not clear on how to back that out. 

  
My net work:

  ```

pat@Plex:~$ ip -c r | column -t
default           via  192.168.2.1      dev    enp4s0  proto   static  metric  100
default           via  192.168.30.6     dev    enp2s0  proto   static  metric  20101
169.254.0.0/16    dev  enp4s0           scope  link    metric  1000
172.17.0.0/16     dev  docker0          proto  kernel  scope   link    src     172.17.0.1
172.18.0.0/16     dev  br-3bec9488216d  proto  kernel  scope   link    src     172.18.0.1     linkdown
172.19.0.0/16     dev  br-185d729d4c47  proto  kernel  scope   link    src     172.19.0.1     linkdown
172.20.0.0/16     dev  br-ca30175ba3ed  proto  kernel  scope   link    src     172.20.0.1     linkdown
172.22.0.0/16     dev  br-80607738ed16  proto  kernel  scope   link    src     172.22.0.1
172.27.0.0/16     dev  br-58167c42be0e  proto  kernel  scope   link    src     172.27.0.1
172.30.32.0/23    dev  hassio           proto  kernel  scope   link    src     172.30.32.1    linkdown
192.168.2.0/24    dev  enp4s0           proto  kernel  scope   link    src     192.168.2.6    metric
100 192.168.30.0/24   dev  enp2s0           proto  kernel  scope   link    src     192.168.30.6   metric
101 192.168.160.0/20  dev  br-5ba6e85d9513  proto  kernel  scope   link    src     192.168.160.1
192.168.176.0/20  dev  br-33f0397a1f8b  proto  kernel  scope   link    src     192.168.176.1            


```  
the rules. 

  ```

at@Plex:~$ ip rule show
  0:  from all lookup local
  50: from all lookup main suppress_prefixlength 1
  70: from all fwmark 0x3214 lookup piavpnFwdrt
  100:    from all fwmark 0x3212 lookup piavpnOnlyrt
  101:    from all fwmark 0x3211 lookup piavpnrt
  102:    from 192.168.2.6 lookup piavpnrt
  5210:   from all fwmark 0x80000/0xff0000 lookup main
  5230:   from all fwmark 0x80000/0xff0000 lookup default
  5250:   from all fwmark 0x80000/0xff0000 unreachable
  5270:   from all lookup 52
  32766:  from all lookup main
  32767:  from all lookup default

```

---

### Post by patwashere on 2023-12-24
fixed.  turns out I had modified the tailscale access controls and that messed things up on my local network.  I could not even ping my firewall/router.   removing those changes fixed it for me.  I have my network back!

---

