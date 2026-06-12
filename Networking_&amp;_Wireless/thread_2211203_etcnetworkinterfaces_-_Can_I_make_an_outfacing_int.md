---
title: "/etc/network/interfaces - Can I make an outfacing interface with a dynamic IP?"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by tuffshark on 2014-03-14
I want to run a Minecraft server (port 25565). But I am having trouble with Ubuntu's firewall... It doesn't mix well with my current settings! I have a setup for a dynamic IP address. I already use ddclient, which updates the external ip so that the data sent to the hostname is forwarded to the external IP, and the hostname updates depending on whatever external IP my router has provided. (This is a feature that my ISP offers in the router settings, so my router should do the mapping). But I need to set NAT rules in iptables for the incoming requests, so they aren't dropped - which is what is happening now to all the incoming packets.
 
So I need to define some FORWARD rules to iptables? But if I use my external IP it will update and I'll have to set the rule every time, so I looked around and what it seemed most people where doing was setting up an outgoing interface, so that the external IP can be resolved and better understood as a rule for iptables. Although, they all seemed to have static IP addresses if they used this method for their servers. Is there a way I can do this with a dynamic IP at all? Or is there any kind of workaround? I already have a static internal interface setup as eth0, which my router maps incoming requests to, and Wireshark picks up the requests, so they are reaching my server?.. So I figured iptables must be blocking them? Or is there something I am missing? Help!

---

### Post by papibe on 2014-03-14
Hi tuffshark.

A few thoughts:

You probably have a dynamic public IP provided for your ISP. 'ddclient' allows other users to reach your modem/router.

In order for your friends to reach your server you need to:
[LIST]
[*]set an static LAN IP to the server (mod /etc/network/interfaces), or easier, set a DHCP reservation on the router (leave the server as is), and
[*]forward the port the the server.
[/LIST]
If you are not running iptables, you won't need to update any rules on the server. If you are, please post the output of this command:
```
sudo iptables -L
```
Regards.

---

### Post by tuffshark on 2014-03-14
sudo iptables -L:
```
Chain INPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin

ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25565

ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED





Chain FORWARD (policy ACCEPT)

target     prot opt source               destination         




Chain OUTPUT (policy ACCEPT)

target     prot opt source               destination         

root@helloworld:~#
```

---

### Post by papibe on 2014-03-14
Thanks.

It looks like that's taken care of. You already have a rule to let people to the port 25565:
```
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:25565
```

The rule should look like this in your file of rules:
```
iptables -A INPUT -p tcp -m tcp --dport 25565 -j ACCEPT
```

Did you set the DHCP reservation on your router?

Regards.

---

### Post by tuffshark on 2014-03-14
Yes I did set a reservation for my ip :), and the rule looks just like that!

---

### Post by papibe on 2014-03-14
Restart the network on the server so that it grabs the new address (if necessary):
```
sudo service networking restart
```

Let us how it goes.
Regards.

---

### Post by tuffshark on 2014-03-14
After reset still nothing... The ports are still showing closed. I am using [this]("http://www.yougetsignal.com/tools/open-ports/") to test this.

---

### Post by papibe on 2014-03-14
Ok.

could you run this command on the server?
```
ifconfig
```
and then upload and screenshot of the forwarding rules on your router?

Regards.

---

### Post by tuffshark on 2014-03-14
ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:0e:7f:a9:10:54  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7fff:fea9:1054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3057949 (3.0 MB)  TX bytes:1151253 (1.1 MB)
          Interrupt:20 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


root@helloworld:~#

---

### Post by papibe on 2014-03-14
Thanks. How about the screenshot?

---

### Post by tuffshark on 2014-03-15
> **papibe said:**
> Thanks. How about the screenshot?
[IMG]http://s14.postimg.org/6ck4e07vl/Thingy.png[/IMG]

---

### Post by untrustytahr on 2014-03-15
tuffshark,
I think he/she meant a screenshot of your router's port forward settings, not your ubuntu machine's interface settings.  You have the ubuntu machine correctly listening on port 25565 but before any connections can reach it, it has to get through your router's firewall via port forwarding.  In other words,  on your router you need to forward port 25565 to 192.168.0.8.

(didn't mean to butt in papaibe, but saw tuffshark online and you weren't) :)

---

### Post by leftyleo on 2014-03-15
sudo service networking [COLOR=#417394]restart

This just hangs up my VM server and have to go back to last snapshot 
weird[/COLOR]

---

### Post by papibe on 2014-03-15
> **leftyleo said:**
> This just hangs up my VM server and have to go back to last snapshot 
weird
The fact that this is a VM is relevant. This changes things a little bit.

Could you explain how the VM is set?
Did you bridge the VM network interface?
Could you post the output from the same command from the host machine (text only)?
Do you have a firewall active on the host machine?

I see that you set up an static IP on the server itself instead of a reservation on the router. What are you using in your router's forwarding rules? hostname, MAC?

Looking forward to hearing from you again.
Regards.

---

### Post by tuffshark on 2014-03-16
These are my router's firewall rules. The incoming packets on port 25565 are sent to the LAN ip of my host machine/server (192.168.0.8)
[IMG]http://s21.postimg.org/94oz98qs7/qwerty.png[/IMG]

---

### Post by tuffshark on 2014-03-16
I have no VM software installed, I was simply ssh'ing the system from my LAN.

---

### Post by JKyleOKC on 2014-03-16
It'll help if you tell the forum what you told me via PM -- and mark the thread as SOLVED per the link in my signature below!

---

### Post by tuffshark on 2014-03-16
[COLOR=#000000]I am trying to create a Minecraft server with port 25565 for me and my friends to access. I used to run one on my mac, where I would change the config for my firewall to allow connections through different ports when my public IP changed; then tell my friends to change the IP they should connect to when necessary. But I got sick of this, and wanted to run the server from a remote computer to act as a server which could be controlled via ssh from my main computer. And so you could connect to it from a hostname rather than the actual IP address.[/COLOR]

[COLOR=#000000]Now, I have a computer running Ubuntu Desktop 12.04 and a set of rules to allow ports 25565 and 10000 (for webmin). It has a service set to run the executable for the server when it is commanded to and it works on LAN but not outside my network. It has a reserved private IP and I am using a Dynamic Update Client (ddclient) to update the public IP from the system every 300 seconds. This updates to DynDns.com, but I understand Linux has a client firewall and network manager, iptables.[/COLOR]

[COLOR=#000000]My ISP, Sky supports DNS from DynDns.com specifically. So that works fine, but it doesn't support fixed external IP addresses so I can't create a network card for an outfacing network because it will just change? I thought I might be able to create one that will search my DynDns.com profile to find my external IP and update it every x minutes. But I am unsure of how to do this to make it work properly. I need to map my Internal IP to my external from a postrouting rule. And this - I thought could only be achieved if I can make a set of iptables rules that uses an outfacing interface that uses my external dynamic IP.[/COLOR]

---

