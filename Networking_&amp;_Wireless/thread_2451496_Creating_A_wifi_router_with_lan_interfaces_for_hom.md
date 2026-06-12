---
title: "Creating A wifi router with lan interfaces for home - routing problem"
date: 2020-10-05
forum: Networking &amp; Wireless
---

### Post by gibsonjcor2 on 2020-10-05
Hi,

I was wondering if someone would be able to help me. I am currently trying to switch out my old router with a computer running ubuntu LTS 20.04. I need both a wireless access point, lan connections, wan connections and the computer itself to be able to browse the internet. I have been able to get either a wifi access point to work with the computer still being able to browse the internet, or the lan connections to work but the computer is not able to browse or have the wireless access point working. I imagine it has to do with how I am setting up the routing table and netplan but I have been working on this pretty steadily for about a month now and I am not able to grasp the correct setup. Any help that could be provided would be greatly appreciated. 

Thank you. 

John.

---

### Post by SeijiSensei on 2020-10-05
Have you enabled IPv4 forwarding in /etc/sysctl.conf? Ubuntu, like most modern distributions, won't forward traffic across network interfaces by default as a security precaution.  Use "sudo nano /etc/sysctl.conf" and remove the hash mark ("#") from the line that reads
```
net.ipv4.ip_forward=1
```
Then save the file and reboot. Any better?

You shouldn't need to do anything special for routing.

You might also need a "masquerading" iptables rule. [https://www.lifewire.com/ubuntu-ip-masquerading-2205843](https://www.lifewire.com/ubuntu-ip-masquerading-2205843)

---

