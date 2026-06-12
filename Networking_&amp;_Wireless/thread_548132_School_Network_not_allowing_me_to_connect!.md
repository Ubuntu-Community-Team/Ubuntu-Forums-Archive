---
title: "School Network not allowing me to connect!"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by linuxpwnsmsn on 2007-09-10
Hi, I've had this problem almost ever since I got here (it worked once, and I believe that was the first day I got here) and I've exhausted every source I could possibly find. Other linux users have been able to connect to the DHCP server, but I have yet to do so since the one time it worked.

My problem is that my system simply will not connect to the DHCP server. I am currently dual booting with Windows XP, enabling me to post onto here for help.

I would type in "sudo invoke-rc.d networking restart" and get the return of dhclient attempting to connect to 255.255.255.255 at port 67 at many different intervals, and it would eventually find nothing and begin to hibernate.

I *have* tried messing with the dhclient.conf file in /etc/dhcp3 but with the same results, and I have changed it back to the standard settings.


Here is what I get with windows:

Windows IP Configuration



        Host Name . . . . . . . . . . . . : apoc

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Hybrid

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : gmu.edu



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : gmu.edu

        Description . . . . . . . . . . . : ULi PCI Fast Ethernet Controller

        Physical Address. . . . . . . . . : 00-13-8F-7A-83-6F

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 42.23.113.22

        Subnet Mask . . . . . . . . . . . : 255.255.255.252

        Default Gateway . . . . . . . . . : 42.23.113.21

        DHCP Server . . . . . . . . . . . : 42.0.0.1

        DNS Servers . . . . . . . . . . . : 129.174.1.3

                                            129.174.97.3

        Primary WINS Server . . . . . . . : 42.0.0.1

        Lease Obtained. . . . . . . . . . : Monday, September 10, 2007 10:12:50 AM

        Lease Expires . . . . . . . . . . : Thursday, September 13, 2007 10:12:50 AM


I have tried manually configuring the network with no luck so far, and I'm thinking that if I can hook up with the dhcp server, I'll be set.

Help me, please?

---

### Post by jlintz on 2007-09-10
Does your school have some sort of internet registration system?  Many schools require you to go through a registration process before your internet is enabled

---

### Post by linuxpwnsmsn on 2007-09-10
you have to login before you can connect to the Internet, but I have not even began to be able to connect to the network. It assigns an ip on the dhcp server, and then it prompts for a login.

So... not really.

Windows and Kubuntu uses the same MAC address.

---

