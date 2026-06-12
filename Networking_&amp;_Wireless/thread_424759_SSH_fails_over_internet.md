---
title: "SSH fails over internet"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by snarkycat77 on 2007-04-27
Hi all,

I'm having trouble getting SSH to work. Right now I have two computers - a desktop with Feisty on it and a laptop with Edgy. I installed openssh-server onto the desktop. Then I went ahead and made the public and private keys and put the public key onto the desktop. Now I can SSH from the laptop onto the desktop when I'm at home and both machines are sitting behind the router. But if I go to a coffee shop and try to "ssh 125.143.27.88", or whatever my current wan IP is, I get the message "ssh: connect to host 125.143.27.88 port 22: Connection timed out."

I have set up a static IP in /etc/network/interfaces. I tried disabling ipv6. I've updated my router's firmware and have opened port 22. Nothing is working for me and I'm at a loss as to how to troubleshoot this. Any help would be appreciated. :) 

FWIW - the router is a Linksys BEFSR41

---

### Post by .rdg on 2007-04-27
Are your PCs also set up with public IPs? Most likely they have private IPs (since they're behind a router) - something like:

192.168.x.x
172.16.x.x - 172.31.x.x
10.x.x.x

If so - you'll need to set up port forwarding on your router, so it forwards network traffic for port 22 to your desktop PC.

If uncertain what are your PC IP addresses in terminal run:

sudo ifconfig.

Regards,
.rdg

---

### Post by snarkycat77 on 2007-04-27
Sorry for not being clear on this. Yes, I am forwarding port 22. Again, it works when I'm at home behind the router but I can't connect when I'm away from home. And yes, I do go to one of the sites that tells you what your WAN IP is, which I use when I try to ssh into my machine when I'm away from home.

I did try bypassing the router today, by connecting the desktop up directly to my modem. Same result. Away from home, I get the same "Connection timed out" error.

Any ideas on how to troubleshoot this?

---

### Post by .rdg on 2007-04-28
If you're able to directly connect to Internet - you should start testing it this way first. So at least you know your sshd is setup correctly.

First of all try the following (in the terminal):

netstat -lnt | grep ":22"

This way you'll know if anything is listening on port 22 (deafult for sshd - from your messages it seems you haven't changed it). Then ask a friend to connect to your server (if the prompt shows fine - you're fine; I assume your sshd is setup to accept passwords).

If he's able to connect - your sshd is set up fine. If not - you probably firewalled it. The next step would be to check your forwarding settings and firewall on the router.

Also note - some routers are able to use DDNS (dynamic DNS) services - so you wouldn't have to bother knowing your IP - just the hostname (which would always be static while your IP could change).

Regards,
.rdg

---

