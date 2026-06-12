---
title: "Is Netplan a stupid implementation or is the documentation bad?"
date: 2018-11-23
forum: Networking &amp; Wireless
---

### Post by sidstuart on 2018-11-23
I've set up my first Ubuntu 18.04 server and am currently working to configure services on it. We like to assign VIP's to services, so they can be easily moved around. We also like to use Ansible to maintain the configuration of the services. 

After reading through the documentation for Netplan and it's configuration files, I can't figure out a simple way to add/delete a VIP configuration on an interface. In 16.04 we could drop a file into /etc/networking/interfaces.d. In Netplan, it looks like one has to use the Ansible lineinfile module to add/delete a line in a YAML list. That does not look like a robust approach at all. 

Has Netplan taken a step back from simple configuration management or is there a way to maintain multiple addresses on an interface in multiple configuration files? Perhaps I'm missing something and there is a better approach? I certainly cannot find one suggested in the documentation.

Sid

---

### Post by TheFu on 2018-11-24
You can go back to the old ifup/down tools until netplan matures.
sudo apt install ifupdown
delete any .yaml file in /etc/netplan 
setup stuff the old way.

---

### Post by Doug S on 2018-11-24
> **TheFu said:**
> You can go back to the old ifup/down tools until netplan matures.
sudo apt install ifupdown
delete any .yaml file in /etc/netplan 
setup stuff the old way.+1. I am still on 16.04 on my servers, but I think I'll do it this way when I migrate to 18.04.

---

