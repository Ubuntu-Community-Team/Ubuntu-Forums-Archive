---
title: "Fits with SSH"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by treii28 on 2015-02-26
I'm having nightmares with various systems connecting via ssh. The systems are behind a router and each has a block of ports forwarded to each. e.g. the machine on 192.168.x.22 has 22000-22999 and so on. It works, and is verified from one system to all by one of them. But I keep running into strangenesses that I can't explain.

Work machine = linux ubuntu on comcast business
home = 4 machines (one win7 running sshd on cygwin, one rpi, one bpi and one ubuntu behind a router with port forwarding)
other: godaddy account

I can ssh from home to home from any machine to any machine over either ethernet or wifi. (all machines have both configured)
I can ssh from work to home using this port configuration to all but the banana pi. (trying gives about a 30s wait before it times out with 'connection refused')
I cannot seem to ssh to any system from godaddy. trying gives an instant failure with connection refused.

The win7 is running windows firewall and avast, but ssh is open to it and I can connect to it fine from work or home. Only one of the pis has any kind of elaborate firewall rules in place and I verified the godaddy is not specified in any of the exclusions.

So why would ssh work from one host just fine and fail from another? Keys have been transferred between all the respective machines and I have tried nuking the known_hosts, restarting sshd, etc with no changes in behavior.

SW

---

### Post by TheFu on 2015-02-26
ssh -vvvv userid@server
on the server side, watch the sshd logs.
Clearly, watch the router logs too.

My setup is simple.
* port 22 used inside a LAN for all ssh access. No need to move ports.
* Random high ports used from outside the LAN for selected system ssh access - "port translation"
* all systems have static IPs
* Not all systems allow ssh access from outside the LAN - it just isn't necessary. Use a "jump box" to get inside the LAN, then hop over to other systems. For example, I'd never allow remote, internet, connections to a Windows box.
* Don't allow passwords. Clearly this is necessary until the keys all work.
* Don't allow remote root ... er ... ever.

---

