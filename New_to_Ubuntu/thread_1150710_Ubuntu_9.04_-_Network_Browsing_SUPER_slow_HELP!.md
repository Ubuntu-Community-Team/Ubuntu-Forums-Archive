---
title: "Ubuntu 9.04 - Network Browsing SUPER slow HELP!"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Ice Dragon on 2009-05-06
Hello everyone, 

Installed Ubuntu 9.04 on about 6 computers now and im loving it, everything including the wireless works on all computers.

The problem im having, is one that is shared on all computers. When I click Places -> Network, it shows me my networked windows computers, when i double click to open the shares on one, every step of the way it tells me "Opening 'ComputerName'" and takes a good 45 seconds. Then i open a folder within that network location, again Opening for 45 seconds.

That is highly frustrating as my windows computers do network browsing instantly within a second.

Is there something wrong with the way I have Ubuntu 9.04 setup?

Please advise.

---

### Post by cariboo on 2009-05-06
With only six computers on the network you can alias the computer names to ip addresses in /etc/hosts eg:

```
192.168.1.200     computer1
192.168.1.201     computer2
192.168.1.202     computer3
etc.
```

---

### Post by Ice Dragon on 2009-05-09
> **cariboo907 said:**
> With only six computers on the network you can alias the computer names to ip addresses in /etc/hosts eg:

```
192.168.1.200     computer1
192.168.1.201     computer2
192.168.1.202     computer3
etc.
```


Why does this need to be done in order to have normal speed performance? On the windows computers networking works instantly without me having to add anything to the host file. Why is Ubuntu not setup with a similar ease of functionality?

---

