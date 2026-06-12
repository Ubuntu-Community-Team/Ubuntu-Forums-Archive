---
title: "ssh connection timeout"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2007-08-28
I have two laptops, and when I'm on my apartment's wireless network, I can use one to access the other one remotely with no problem using ssh.

When I'm on my school's wireless network, however, I get ssh timeouts involving port 22. I have no idea what to do, but I have a feeling it has to do with opening that port. In summary, I want to access the hard drive of my laptop at home from my laptop at school.

---

### Post by xjgnsdof on 2007-08-29
up

---

### Post by kevdog on 2007-08-29
If you have a router at home, you need to port forward port 22 to the IP address of the computer (located at home).  If this "server" is running ubuntu, then you need to open up port 22 for inbound connections since its closed by default.  The easiest way to do this is probably to install firestarter or guarddog since these provide GUIs allowing you to manipulate your firewall without too much effort.

Just a side note, I would probably just for security reasons run you ssh server on a different port other than 22, maybe 2222 for example.  You will get a lot of anonymous traffic trying to access your box on port 22.

---

### Post by xjgnsdof on 2007-08-29
Thanks. I'll get started on port forwarding. Does it even matter that people might try to access my server on port 22 if I have a password?

---

### Post by kevdog on 2007-08-29
Just a couple of recommendations (although I think generally you will find these supported by most of the people on this forum).

1. Run ssh on an alternative port other than 22.
2. I would generally recommend you do not use a password (unless last resort) to access your ssh server, but rather use public/private keys with the private key password protected.  This would require you to store the private key on a usb drive or your computer or on something that you would have to carry around with you, so its a little bit inconvenient.  

I used to run ssh on 22, however one day looked at the logs with some remote script that was trying to access my box about 1000 times (this even though I had removed the use of passwords on my ssh server).  

Personal recommendation.  I use the ssh tolero server version on ubuntu from here: [http://tech.tolero.org/blog/en/linux/ssh-password-brute-force-protection](http://tech.tolero.org/blog/en/linux/ssh-password-brute-force-protection)
You can read about how it tries to protect your system from brute-force attack.  I used the edgy repository even though Im using feisty.

---

### Post by xjgnsdof on 2007-09-08
So I have opened Firestarter and created policy that allows service "SSH" for port 22 for "everyone." On my other laptop, which is on a different wireless network than the server, I still can't SSH in. I get a message saying "no route to server." What's going on?

---

### Post by kevdog on 2007-09-09
Just make sure that the ssh server has either a static IP address assigned or its dynamically allocated IP address is not changing so that the router can appropriately forward connections correctly to the correct internal LAN

You can try to things to see where the connection breaks.

Do a tracert from the client to your IP address at HOME -- the WAN IP address.  Make sure you dont have any broken hops.

Also do a 
ssh -vvv  user@IP_address (or domain name)

That will give some debugging output!!

---

### Post by xjgnsdof on 2007-09-09
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.6 [192.168.1.6] port 22.
debug1: connect to address 192.168.1.6 port 22: No route to host
ssh: connect to host 192.168.1.6 port 22: No route to host


I have no idea what "broken hops" and "tracert" are.

---

### Post by kevdog on 2007-09-09
Can you ping the server from the client??

---

### Post by kevdog on 2007-09-09
It seems to me like a firewall problem, but can you do the following:

Open a command window on the server and type:
sudo tcpdump -i <interface name - ie eth0, wlan0, eth1, etc> port 22

Then on the client attempt to connect to the server
ssh user@IP

See if any packet reaches the server.  If nothing shoes up, you know at least something is blocking the connection.  

Anyway to deactivate the firewall (for testing) and just open all ports???

---

### Post by xjgnsdof on 2007-09-09
I've stopped the firewall. I typed in all that stuff you said, and I still get the same error message on my client when it is on a neighbor's network. I get no response on the server's terminal window. When the client is on my own network, it's fine.

---

### Post by kevdog on 2007-09-09
The problem is that its not even reaching the ssh deamon.

Can you telnet to the machine

telent ipaddress port 22

---

### Post by xjgnsdof on 2007-09-09
This is what I typed in: emones@emones-laptop:~$ telnet 192.168.1.6 port 22

This is what I got back:

Usage: telnet [-4] [-6] [-8] [-E] [-L] [-a] [-d] [-e char] [-l user]
        [-n tracefile] [ -b addr ] [-r] [host-name [port]]

Edit: I input "telnet -b 192.168.1.6" and then typed "open 192.168.1.6" and got the same error message.

---

### Post by xjgnsdof on 2007-09-09
uppers

---

### Post by kevdog on 2007-09-09
telnet 192.168.1.6 22

---

### Post by kevdog on 2007-09-09
Post the following on the server machine:

netstat -tnl

route -n

---

### Post by xjgnsdof on 2007-09-09
On the client, I got the same error message: "...No route to host."

As for the other commands, I received the following on the server:

```
emones@emones-homePC:~$ netstat -tnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:39886           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:2207          0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
emones@emones-homePC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by kevdog on 2007-09-09
Have you tried turning off ipv6??  I did this a while ago, but I cant remember how.   Search the forums for it

Just as a comparison, here is the results of my netstat -tnl for the ssh server
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN

Yours is tcp6.  Im assuming this may have to do with ipv6

---

### Post by xjgnsdof on 2007-09-09
Same result. I've disabled it through Mozilla, and when that didn't work, I blacklisted it in Ubuntu. This is really hurting my head now...

---

### Post by xjgnsdof on 2007-09-10
up

---

### Post by xjgnsdof on 2007-09-11
I'm at school, and instead of a "no route to host" error message, which I got when on my neighbor's wireless network, I got a "connection timeout" message, which I have always gotten when on my school's wireless network. I'm right back to square one after all the stuff I tried...

---

### Post by kevdog on 2007-09-11
Im out of ideas, although it seems to be more of a firewall issue to me, either on the client or server or both.  Im not very good at configuring IP tables manually.  Last suggestion would be to PM noob12.  He's pretty good at figuring problems out such as yours.

---

