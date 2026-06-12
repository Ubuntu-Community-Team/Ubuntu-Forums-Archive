---
title: "[SOLVED] Can't ssh remotely, only locally"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by fizikz on 2008-07-23
I have 2 laptops and I want to ssh from A into B. B is (almost) always at home. When I'm at home, ssh works no problem. But when I'm away, ssh just times out. I'm using port 25 instead of the default 22, because someone else at home is using 22. While outside, I can ssh into 22, but 25 times out. Again, when I'm at home, everything works fine. What am I missing?

---

### Post by scorp123 on 2008-07-23
You did configure port-forwarding and network address translation on your Internet router/firewall, yes?

---

### Post by superprash2003 on 2008-07-23
thats right.. you need to open port 25 on your router.. but some ISP's may block port 25

---

### Post by fizikz on 2008-07-23
Yes I did forward port 25 on the router. I'm not sure about network address translation though. If the ISP is blocking port 25, would I still be able to use it to ssh when I'm local to the router? Currently when both machines are connected to the same router, ssh works. I don't have another internet connection at home, so I can't test if that is the common element. I suppose I could try changing the port I'm using... But I still don't see why it works  when I'm home, and not from elsewhere.

---

### Post by sp0nge on 2008-07-23
I have a similar issue. I am able to ssh locally, and have forwarded a higher port for use. When I came to work, I tried to use putty from a windows machine to ssh into the server at home by entering (my public IP) XX.XX.XXX.XXX:1234(the port I forwarded) as the host but the connection times out.

---

### Post by fizikz on 2008-07-24
Yes, it sounds like you have the same problem. If anyone has been through this, some info would be appreciated.

---

### Post by superprash2003 on 2008-07-24
even if isp blocks 25 it could be accessible locally.. try some other port..

---

### Post by fizikz on 2008-07-24
I've tried several other ports, but each time I get "connection refused". At least it's not timing out. I have changed the port information in sshd_config and in the router's port forwarding tables. Is there something else I need to configure?

---

### Post by flamethrower on 2008-07-24
do u have ssh configured to accept logins from anywhere?
have u nmapped ur home address from work?

i would do that to determine if the connection is refused on network level (tcp rst/icmp port unreachable) or by the ssh daemon.

---

### Post by fizikz on 2008-07-24
I believe it's configured to accept connections from anywhere. I didn't specify the incoming IPs if that's what you mean. But other than that, I'm not sure how to test what you're suggesting... Could you elaborate?

---

### Post by sp0nge on 2008-07-24
ssh listens to port 22 by default. If you open this port on your router you should be able to connect remotely as I am. I will be investigating this in terms of changing the port, but I have been unsuccessful to this point- at least I can connect remotely now.

---

### Post by flamethrower on 2008-07-24
> **fizikz said:**
> I believe it's configured to accept connections from anywhere. I didn't specify the incoming IPs if that's what you mean.

nah, i just meant to accept connections from anywhere, so thats fine.

> But other than that, I'm not sure how to test what you're suggesting... Could you elaborate?

well, you said ssh complains about the connection being "refused", when the connection should have been accepted.
it could be that you have iptables configured to filter incoming requests, it could be that you set up your router wrong.
it could also be that your isp is filtering some ports, but i would rather assume that you have some firewall in place at work - have you tried connecting from a friend's place?

why dont you use iptables to set up a pattern of filtered, closed and (fake-)open* ports. then go to work (or to a friend) and port scan your home address from there, and see if the pattern matches.

*
filtered: drop packets
closed: reject packets with tcp-rst
fake-open: "reject" tcp-syns with tcp-syn-ack packets, this will make nmap think the port is open

---

### Post by fizikz on 2008-07-24
I'll have to look into iptables...

Perhaps I should also mention that the "connection refused" message also comes when I try to connect locally.

---

### Post by flamethrower on 2008-07-24
> **fizikz said:**
> I'll have to look into iptables...

Perhaps I should also mention that the "connection refused" message also comes when I try to connect locally.

what? i thought you said it works locally.

check if the nic is properly configured (subnet mask and all), and flush your iptable rules (iptables -f, no need go into depth for that).

then try to connect

---

### Post by fizikz on 2008-07-24
It was working locally on port 25. When I changed it to higher port numbers (I tried 6898, 36898 ), that's when I got the connection errors, locally and remotely. I'll try your suggestions when I get home.

EDIT: The changes I made when going from port 25 to the others involved updating the port number specified in sshd_config, and the port forwarding tables on the router.

---

### Post by fizikz on 2008-07-25
I tried "iptables -F" but that didn't seem to change anything. I still get the connection refused error. Also, using "ifconfig" I don't see anything wrong or unusual. I don't know why choosing a different port is causing a different response from the server.

---

### Post by fizikz on 2008-07-26
I can't use port 22 because someone else at home is already using that port. I believe it works fine on 22 because I can reach his password prompt remotely without problems. But I still haven't gotten any other port working yet...

---

### Post by fizikz on 2008-08-24
I believe this problem is solved now. It turns out my firewall (moblock) was not configured to open the port I was using for ssh. I didn't think the firewall was a problem since ssh-ing from my home network was working, but that's probably because the local IPs are whitelisted. To test my ssh setup, I ssh-ed from a home laptop into a remote computer, and from the remote computer ssh-ed back into my main home laptop. The good news is, it works. Thanks for the help.

---

