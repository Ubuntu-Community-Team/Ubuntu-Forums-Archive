---
title: "How to access Proftpd server"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by tkei on 2011-03-04
Greetings,

I hope this is the correct forum for this question. It would seem to me to be a relatively basic question but still one that I cannot find the answer for. 

So I recently installed ubuntu 10.10 on a desktop (the desktop edition) and I installed proftpd on it and from the looks of it everything seems to be running.

But I am unaware of where or how to connect to the ftp server from other computers. I'm assuming there would be an IP address with a port combination to enter in a web browser of another computer but I am not sure where to find this address to give enter in to access the ftp server.

If anyone has any information about this I would greatly appreciate it.

Thanks,

-Tkei

---

### Post by Frogs Hair on 2011-03-04
I have not used Proftpd but search turned up many links , here are a few. Welcome to the forums. 
[https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)
[http://forums.proftpd.org/smf/index.php?topic=5229.0](http://forums.proftpd.org/smf/index.php?topic=5229.0)
[www.debianadmin.com/proftpd-server-installation-and-configuration.html](www.debianadmin.com/proftpd-server-installation-and-configuration.html)

---

### Post by alphacrucis2 on 2011-03-05
> **tkei said:**
> Greetings,

I hope this is the correct forum for this question. It would seem to me to be a relatively basic question but still one that I cannot find the answer for. 

So I recently installed ubuntu 10.10 on a desktop (the desktop edition) and I installed proftpd on it and from the looks of it everything seems to be running.

But I am unaware of where or how to connect to the ftp server from other computers. I'm assuming there would be an IP address with a port combination to enter in a web browser of another computer but I am not sure where to find this address to give enter in to access the ftp server.

If anyone has any information about this I would greatly appreciate it.

Thanks,

-Tkei

The address is of course the ip address of your PC that Proftpd is running on. You can find that out by:

```
ifconfig
```

If you want machines out on the internet to connect to it then your internet router will have to cooperate by using port forwarding. ie the devices out on the internet open an ftp session to the public address of your internet router and the router has to be configured to forward these ftp connections to the private ip address of your PC. If you read the manual for your router, it should explain how to do this.

To find out the public address of your router you can use 

[http://www.whatismyip.com/]("http://www.whatismyip.com/")

Some other things.

1. The public address of your router may change from time to time. You can get around that by using a service such as [http://www.dyndns.com/](http://www.dyndns.com/)

2. The private ip address of your PC may change if it is being set by the DHCP server running on your router. You can either set the PC up with a static address outside of the routers configured DHCP range but still within the subnet being used, or most DHCP servers can be configured to always supply the same ip address to your PC based on its' hardware MAC address. Again your router manual should explain how to do this.

---

