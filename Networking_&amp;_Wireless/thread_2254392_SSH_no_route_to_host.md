---
title: "SSH no route to host"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by Thomas_R. on 2014-11-26
Hello,

I am currently working on a project that's main objective is to create a cluster computer with a 8 or so computers. I have created static IP's and tried using this link so that they would connect: [http://www.sudo-juice.com/how-to-set-a-static-ip-in-ubuntu-the-proper-way/#disable-nm](http://www.sudo-juice.com/how-to-set-a-static-ip-in-ubuntu-the-proper-way/#disable-nm) ... except for the DNS-name server I used my Gateway address. Now the problem is whenever I use ssh to login from the main computer into one of the nodes, the terminal gives me back an error. For example I will type into the terminal on the master: "ssh node1" and then it'll say "ssh: connect to host node1 port 22: No route to host". Is there any way I can resolve this? If you need any more information then please ask. 

I have also disconnected the cluster from the internet because the IP's keep changing, that is why I created static IP's.

Thank,
    Thomas

---

### Post by SeijiSensei on 2014-11-27
Usually that means you don't have name service correctly configured.  Either you don't have an entry for node1.example.com, or you don't have example.com specified as search entry.  If the IPs are configured statically, then you should designate the DNS nameservers in /etc/network/interfaces as described here:  [https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/14.04/serverguide/network-configuration.html#name-resolution)

If you don't have a DNS server for your domain, you'll need to add entries to /etc/hosts instead.

Try using the server's IP address instead of its hostname like "ssh 10.10.10.10".  If that works, then it's definitely a problem with name resolution.

---

