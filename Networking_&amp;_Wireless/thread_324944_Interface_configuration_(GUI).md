---
title: "Interface configuration (GUI)"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by IamAcoconut on 2006-12-24
Hello, dear fellow-users!
Coconut has another question.

How does he configure his network settings. Coconut's computer has a static IP, it's part of a home network, behind home gateway. Yet the gateway get's it's IP and DNS addresses from the ISP via DHCP, So what should be done if the DNS addresses are provided by DHCP, yet (inner) IP is static. 

The DNS servers don't really change, so I entered their addresses when configuring my network. (Yet I would like to know a better solution) 
Despite enering all neccesary parameters the connection was down (though I could ping my gateway) until I did the same thing (except for the DNS addresses) from the console.
```
sudo ifconfig eth0 10.1.0.2
sudo route add default gw 10.1.0.1
sudo ifconfig eth0 up
```

Now it works, but since Ubuntu's described as linux for human beings I think there's a way to do this via GUI - that's what it's for, isn't it?
Another thing I'm seeking is a better solution for described situation.

Thanks in advance :-)

---

### Post by TMMM on 2006-12-24
Configure your gateway and dns the same number whichever your gateway lan ip is.

If you click on something along the lines of "system/administrative/network..." then you will see where to configure your adapter.

---

### Post by IamAcoconut on 2006-12-24
> then you will see where to configure your adapter.I know, that's how I've done it first time. Yet the gateway neither the gateway nor the IP I entered showed up after running ifconfig and route from console. Until the second time, when I typed the parameters  from console.

---

### Post by IamAcoconut on 2006-12-25
Well, anyway, now it's fine. Thanks for the help, TMMM :-)

---

