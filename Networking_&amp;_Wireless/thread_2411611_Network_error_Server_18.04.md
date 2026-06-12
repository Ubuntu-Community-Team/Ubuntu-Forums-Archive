---
title: "Network error Server 18.04"
date: 2019-02-01
forum: Networking &amp; Wireless
---

### Post by patdundee on 2019-02-01
Hi guys
I installed and set up Ubuntu Server 18.04 last week and the network worked just fine.
I have just done all secuirty updates and the network has gone down. I get the following error when i try network apply or network --debug apply

Line 2 column 13 mapping values are not allowed in this context

Here is my setup

```

network:
 renderer: networkd
    ethernets:
        ens08:
            dhcp4: no
            dhcp6: no
            addresses: [xxx.xxx.xxx.xxx/27]
            gateway4: xxx.xxx.xxx.xxx
            nameservers:
                addresses: [xxx.xxx.xxx.xxx,xxx.xxx.xxx.xxx]
    version: 2

```

This all worked before the updates so not sure why i am now getting this error. 
Any assistance greatly appreciated
Cheers

---

### Post by chili555 on 2019-02-02
Please compare your file to the example:```
cat /usr/share/doc/netplan.io/examples/static.yaml 
```netplan is very picky about spacing, indentation, etc. Please refine your file and let us know if you can now connect.

---

### Post by patdundee on 2019-02-02
Hi Chili555

Many thanks for that. That layout is somewhat different to the working layout i was using before. I copied the static yaml from the examples to the netplan folder and then edited it. 
All works fine now.

Cheers :P
P

---

