---
title: "sorry but sick of searching now"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by prodigal on 2007-09-07
Apache2 and SSH are working PERFECTLY inside my LAN but from the WAN they just can't get there.

I should explain before anyone comes back with the obvious stuff of port forwarding etc I'm an I.T. engineer for quite a large support company so I actually do know what I'm doing with networking. I know a fair bit about Linux but haven't used it for ages. I'm now trying to get back into it because I miss it so much. Unfortunately as much as I can get both Apache and SSH working on the LAN as soon as I try to access them from the WAN they just don't respond.

The ports are all forwarded correctly, the server has a static ip address and is listening on the appropriate ports. I need a Linux guru and I need one asap before I start crying lol.

Thanks in advance for any help you can give me. Someone PLEASE help me lol.

---

### Post by noob12 on 2007-09-07
Is it one host providing both these services?  Can we see the output of
```

netstat -tnl 

sudo iptables -nL

```
on the host(s).

When you say you can't connect, are you actually running the browser from a point outside the local private net?  If not, can you try that.

---

### Post by prodigal on 2007-09-08
Hiya, thanks for the response. Output of 

```
netstat -tnl 

sudo iptables -nL
```

is 

```

tcp          0            0  192.168.0.121:805                0.0.0.0:*                  LISTEN
tcp          0            0  127.0.0.1:3306                     0.0.0.0:*                  LISTEN
tcp          0            0  192.168.0.121:22                  0.0.0.0:*                  LISTEN

```

and 

```

Chain INPUT (policy ACCEPT)
target      prot opt source                destination

Chain FORWARD (policy ACCEPT)
target      prot opt source                destination

Chain OUTPUT (policy ACCEPT)
target      prot opt source                destination

```

iptables is still open as standard, I haven't locked the server down yet.

This server is built into my work LAN. I'm at home at the moment. I RDP to from my XP machine at home to my XP machine at work then SSH from that to the server no problem, can also SSH from my Kubuntu Laptop which is also on the work LAN same applies for the website. If I browse to [http://192.168.0.121:805](http://192.168.0.121:805) from either XP or Kubuntu laptop at work I get the index.html. If I try to browse to our external IP on port 805 or SSH to the external IP to port 22 I get nothing.

Port forwarding is setup on our firewall at work to send those ports to 192.168.0.121 and our router has all ports forwarded to the firewall. Any other port forwarding I setup on the firewall to any other machine on our work LAN works perfectly but the Ubuntu server seems to just be rejecting everything.

I'm so lost :confused:

---

### Post by prodigal on 2007-09-08
well I fixed it. As expected was something stupidly simple. Because I had it working all day on the LAN I never even thought to test if it could get outside the LAN itself or not. Turns out when I assigned a static IP to it the machine lost it's gateway that it had obtained from DHCP. I didn't assign it a new one, therefore it worked fine on the LAN but couldn't operate on the WAN in or OUT.

Thanks for trying to help noob12

---

### Post by noob12 on 2007-09-08
[COLOR="Red"]UPDATE:  I just missed your last post, so I didn't see you had fixed it.  You can of course ignore this post now.  Interestingly, I think the **route -n** would have revealed the issue.
[/COLOR]
So far that all looks ok, so more diagnostics are needed.  Following are a number of questions and suggestions to proceed with this.

I suspect either the connection is not reaching the host at all or that your return traffic is not being routed back properly.  

Does the host have multiple network interfaces (any interfaces other than loopback and the one that is 192.168.0.121)?

Can you please post the output of **ifconfig -a** and **route -n** on the host.  You say you can RDP into a Windows Host on the work LAN.  It may be useful to compare the output of **ipconfig /all** and **route print** from that host, if you can post that too.

Also, can you describe what exactly happens when you try to connect to your sshd from an external location?   What is the specific message or behavior that you get?    

Here is how you can verify that you are getting traffic to the sshd host from the port forwarding you've setup. Start a terminal window and leave it running with the following tcpdump command to trace traffic to and from port 22 on that interface.   You should first determine the interface associated with 129.168.0.121 using ifconfig.  It is probably eth0.  If yours is not eth0, replace the eth0 below with the appropriate interface name:
```

sudo tcpdump -i eth0 host 192.168.0.121 and port 22

```
This will trace incoming TCP packets to port 22.   Note that if you do connect, you'll get a lot of output here.  What will be interesting is seeing what you get when you try to connect from outside.  If you get nothing while connecting from outside.  Traffic is not reaching the host from the port forwarding.  If you get something, it probably indicates a problem routing the traffic back.  (Note that if you connect from inside the work lan, you'll get a lot of output here, so during this test, it will be helpful if you can avoid internal connections).

If you know the internal IP address or address range used by your firewall device, you can further restrict the tcpdump so that you avoid tracing any traffic originating internally and you'll just see whether you are getting things via port-fowarding.

---

### Post by prodigal on 2007-09-08
Thanks again for the help noob12, if I hadn't already fixed it I think you're right the route -n would have shown what the problem was. 

I actually went into the office and was talking to one of my colleagues, another I.T. engineer, his knowledge of Linux is about equal to mine, he used to use it all the time in previous jobs and in his spare time but has been working for the company we are with now for 7 years and hasn't had much call to use it in that time, we work mostly with windows at work because thats what our clients use.

Anyway we were both really puzzled by it until I decided to try what I call "The Windows Fix" That is reboot the thing and it usually just magically works again, obviously this didn't work but what did happen was the server came back up with a different IP address to the one it should have had, This made me realise that I obviously didn't configure the eth0 interface properly when I assigned it a static IP. My fault entirely lol Gave it the same static IP address again (The quick way so still need to fix it permanently) and then gave it a default gateway manually and bingo, everything worked.

Thanks again dude.

---

