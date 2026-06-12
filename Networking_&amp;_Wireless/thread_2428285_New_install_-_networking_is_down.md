---
title: "New install - networking is down"
date: 2019-10-02
forum: Networking &amp; Wireless
---

### Post by jim-anderson on 2019-10-02
I used kubuntu and ubuntu years ago, so I am only a bit familiar with ubuntu now. I have installed ubuntu 18.04.3 on a laptop and at first glance things look good except the ethernet networking is not working. I have not tried wifi yet.

I did a search and found this article [https://www.krizna.com/ubuntu/setup-network-ubuntu-18-04](https://www.krizna.com/ubuntu/setup-network-ubuntu-18-04). Before going on, my first question:

   **Should I be using netplan? Is that the recommended utility and methodology? If I am using netplan, I am in the mainstream of ubuntu users?**

Anyway, I tried to follow the directions in the article above. Things seemed to go ok, but when I ran netplan, I was not successful. I wrote a yaml file and ran it through netplan without errors. When I ran it through 'netplan --debug', it looks like I have errors, but I am not sure how to interpret or fix the errors. It looks like maybe my yaml file should not refer to 'ens32' which was used in the example at [www.krizna.com]("http://www.krizna.com"). Should I used 'enp6s0**' **which is reference in the debug file?

Jim A.


Following is my file named '01-network-manager-all.yaml':
[INDENT][B]# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    ens32:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.240/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4][/B]
[/INDENT]

And this is the output from running: netplan --debug apply

[B]  1 ** (generate:2147): DEBUG: 07:20:35.617: Processing input file /etc/netplan/01-network-manager-all.yaml..
  2 ** (generate:2147): DEBUG: 07:20:35.618: starting new processing pass
  3 ** (generate:2147): DEBUG: 07:20:35.619: ens32: setting default backend to 1
  4 ** (generate:2147): DEBUG: 07:20:35.619: Configuration is valid
  5 ** (generate:2147): DEBUG: 07:20:35.619: Generating output files..
  6 ** (generate:2147): DEBUG: 07:20:35.619: NetworkManager: definition ens32 is not for us (backend 1)
  7 DEBUG:netplan generated networkd configuration changed, restarting networkd
  8 DEBUG:no netplan generated NM configuration exists
  9 DEBUG:ens32 not found in {}
 10 DEBUG:Merged config:
 11 network:
 12   bonds: {}
 13   bridges: {}
 14   ethernets:
 15     ens32:
 16       addresses:
 17       - 192.168.0.240/24
 18       dhcp4: false
 19       dhcp6: false
 20       gateway4: 192.168.0.1
 21       nameservers:
 22         addresses:
 23         - 8.8.8.8
 24         - 8.8.4.4
 25   vlans: {}
 26   wifis: {}
 27 
 28 DEBUG:Skipping non-physical interface: lo
 29 DEBUG:Skipping non-physical interface: enp6s0
 30 DEBUG:Skipping non-physical interface: wlp7s0
 31 DEBUG:{}
 32 DEBUG:netplan triggering .link rules for lo
 33 DEBUG:netplan triggering .link rules for enp6s0
 34 DEBUG:netplan triggering .link rules for wlp7s0
 26   wifis: {}
 27 
 28 DEBUG:Skipping non-physical interface: lo[/B]

---

### Post by chili555 on 2019-10-02
> Should I be using netplan? Is that the recommended utility and methodology? Everyone in later Ubuntu versions is using netplan, but not in the way you are corrupting it. Your file suggests that Network Manager is running on your system. Everything you need to do, a static address, DNS nameservers, et al, can and should be done in Ntework Manager. 

[https://www.itzgeek.com/wp-content/uploads/2018/05/Configure-Static-IP-Address-in-Ubuntu-18.04-Manual-IP-Address-to-WiFi.png](https://www.itzgeek.com/wp-content/uploads/2018/05/Configure-Static-IP-Address-in-Ubuntu-18.04-Manual-IP-Address-to-WiFi.png)

Next, revert your yaml file to the default:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```Reboot and tell us how it's working:```
ip addr show
ping -c3 www.ubuntu.com
```

---

### Post by jim-anderson on 2019-10-03
@chili555

Thank you for the help.

After my original install and boot, there was no networking. I found a thread and sort of followed the instructions on setting up the yaml file. Obviously, that did not help.  Tonight I modified the yaml file as you suggested and a network connection was made, amazingly without rebooting. For the most part, I am good. I am going to close this thread as solved and open up one or two new threads with follow up questions.

Jim A.

---

