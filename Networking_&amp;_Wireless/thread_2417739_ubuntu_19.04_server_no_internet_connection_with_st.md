---
title: "ubuntu 19.04 server no internet connection with static IP"
date: 2019-04-26
forum: Networking &amp; Wireless
---

### Post by tognaco on 2019-04-26
My recently installed Ubuntu 19.04 server works fine with dynamic IP, but I need an static IP for the server, and since I have changed it to static, my Internet connection no longer works. If I type in the terminal ping 192.168.1.1. it reaches it with no problem. The same happens when I type ping 8.8.8.8 , no problem at all. My /etc/netplan/50-cloud-init.yaml has the following configuration:

network:
version: 2
renderer: NetworkManager

I don't know what I can do to get it working. Any advice?

---

### Post by chili555 on 2019-04-26
Where did you set the static IP? Since you evidently have Network Manager installed and running in your server, that is the logical and best place to set your static IP. May we review the settings?

---

### Post by tognaco on 2019-04-27
I set it with the graphic interface. After posting here I found a post in linuxconfig where I learnt that it is better to do it manually. I opened in nano /etc/netplan/50-cloud-init.yaml and set it in the following way:

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
     dhcp4: no
     addresses: [192.168.1.224/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4]

Then, sudo netplan apply and that's all. Now it is working perfectly :)

---

