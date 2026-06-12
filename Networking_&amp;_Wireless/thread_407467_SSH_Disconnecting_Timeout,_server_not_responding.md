---
title: "SSH Disconnecting: Timeout, server not responding"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by charrin on 2007-04-12
Hello everybody

I am having problems when I connect any external server to open a session with it. I have tried ssh (OpenSSH), Putty (with ssh too), sftp and tsclient with different servers and the problem is always the same: I can connect without problem, but after few minutes working the program hangs and I have to kill it.

Its not a problem of keeping alive because I am active all the time the connection is up. And I am pretty sure the problem rely on Linux because I have Windows 2000 in the same machine and I can use Putty along hours without problems

Somebody has an idea about what is happening?

By the way, the OS is Ubuntu 6.06 Dapper

Help Please!!! I really need to connect these servers to do my daily work and I don't want to boot Windows

---

### Post by garrido on 2007-04-12
Try flushing your firewall rules and see what happens: 

```
sudo iptables -F
```

If it starts working as you want, you know where the problem is ;)

---

### Post by charrin on 2007-04-16
Finally I just found the problem :D :D . In my company we have two gateways, one of them configured to connect with one of our company's clients, whose servers I was trying to reach by SSH, and the other configured for the rest of addresses.

The problem was that my default gateway is the general one, so when I tried to get the ssh connection, my default gateway redirects me to the other router but, to work, I need to get it directly, because it is configured to let me connect our client's server. I discovered this information with:

  traceroute SSH_SERVER_IP

So, the solution was to add a line to the routing table with the command:

route add -net 192.0.0.0 netmask 255.0.0.0 gw GATEWAY_I_NEED

that means that for any IP that starts with 192. I want that the gateway to be used be GATEWAY_I_NEED

You can put this line in your user's .bashrc file or in the init folder for all the users

---

### Post by thelinuxguy on 2007-04-17
> **charrin said:**
> The problem was that my default gateway is the general one, so when I tried to get the ssh connection, my default gateway redirects me to the other router but, to work, I need to get it directly, because it is configured to let me connect our client's server.

Could you explain it a bit more? I didn't understand why your connection kept dropping after sometime when you were using the default gateway.

---

