---
title: "Two NIC, two internet connections, one default route."
date: 2022-12-22
forum: Networking &amp; Wireless
---

### Post by guillaumesoucy on 2022-12-22
Hello,  

  
 
  This is my netplan configuration file on Ubuntu 22.04 LTS:
  

 ```


   GNU nano 6.2                                                                                              /etc/netplan/01-netcfg.yaml                                                                                                        

  # This file describes the network interfaces available on your system
  # For more information, see netplan(5).
  network:
    ethernets:
      ens18:
        addresses:
        - 192.168.2.104/24
        nameservers:
          addresses:
          - 192.168.2.1
          search: []
        routes:
        - to: 192.168.2.104
          via: 192.168.2.1
  
 
      ens19:
        addresses:
        - 192.168.104.104/24
        nameservers:
          addresses:
          - 184.149.24.65
          search: []
        routes:
        - to: default
          via: 192.168.104.1
  
 
    version: 2

```  
 
    I do have two network cards on this Ubuntu system and two internet connections and would like to find a way to have ens19 192.168.104.104 as default and ens18 192.168.2.104 also being able to reach the internet if I bind something to this NIC such as wget as example:  
  

 ```


 wget --bind-address=192.168.2.104 ...


```  

 Right now, I'm unable to do so, traffic can pass through 192.168.104.104 but not through 192.168.2.104

  
 
  I did some researches on the internet before coming here but unfortunately I wasn't able to find anything that solve my problem.  
  
 
  Thank-you,  
  
 
  Guillaume

---

### Post by SeijiSensei on 2022-12-23
I'd start by making sure you can forward packets across interfaces. By default, that is turned off in Ubuntu as a security precaution.

Edit the file /etc/sysctl.conf as root with nano ("sudo nano /etc/sysctl.conf") and look for the line
```
#net.ipv4.ip_forward=1
```
If it has the hash mark at the beginning of the line, then forwarding is disabled. Delete the hash mark, save the file, then run
```
sudo sysctl -p
```
to reread the file. Any better?

---

### Post by guillaumesoucy on 2022-12-23
Hello, 

I just uncomment the line 

```
net.ipv4.ip_forward=1
```

and ran 

```
sudo sysctl -p
```

but the traffic isn't able to pass through ens18 when I bind it.

To be safe I did a reboot, it unfortunately changes nothing for now. 

I red about Policy-based Routing but I'm not so sure how to implement it. I'm not a beginner but Policy-based Routing is not something that I'm very familiarized with. 

Thanks, 

Guillaume

---

