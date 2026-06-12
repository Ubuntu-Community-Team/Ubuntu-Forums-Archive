---
title: "server bridge ip address"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by rosegal on 2009-12-10
i have been following the step to configure Openvpn server in my laptop,but when i started my openvpn server,it failed...

* Starting virtual private network daemon(s)...                              
   *   Autostarting VPN 'server'                                           [fail] 
root@xxxx-laptop:/home/xxxx# openvpn /etc/openvpn/server.conf
Options error: --server-bridge IP addresses 121.xxx.xxx.xx and 121.xxx.xxx.xx are not in the same 255.255.255.255 subnet

how can i make it in the same subnet?i am using mobile broadband for my net connection and my ip address always changes...my iface is ppp0...pls help....

---

### Post by Ocxic on 2009-12-10
checkout [http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork) and [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/) for more info

The 0's in the subnet designate the host. 

if network like 192.168.2.0 has a subnet mask of 255.255.255.0

that means the network can have any number of host between 192.168.2.(1-255); so 192.168.2.5 and 192.168.2.7 would be separate hosts/computers on the same  network

if network like 192.168.0.0 has a subnet mask of 255.255.0.0

that means the network can have any number of host between 192.168.(1-255).(1-255); so 192.186.4.6 ad 192.186.8.5 would be separate hosts on the same network.

---

### Post by Geoff918 on 2009-12-10
Well, to be sure, you'll be setting up your VPN with a separate subnet always. Otherwise, you may run into issues, and the system won't know whether to address the "truly local" network or the "virtually local" network.

What is your main IP range? Then use a different private set-up. E.g. if you are on 192.168.xxx.xxx you would maybe try another private range such as 10.8.xxx.xxx

This guide is AWESOME! I did get a working VPN, and I struggled for hours before I followed this guide. It worked perfectly. Other guides totally failed me. Now I do understand all of the setup and it's quite easy for me. But, it was beyond frustrating when I was first trying to establish a VPN. Unfortunately, the Ubuntu documentation only makes mention of OpenVPN and says that "it's outside of the scope of the document to discuss it".

[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

Check it out, and no, you may not be trying to watch Hulu--but it works anyway.

P.S. You will need access to both the server side and the client side machines--pretty much either physically or through SSH or some such thing.

---

