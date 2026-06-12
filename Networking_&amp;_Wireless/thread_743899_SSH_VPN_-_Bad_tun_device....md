---
title: "SSH VPN - Bad tun device..."
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by boondocks on 2008-04-03
Assuming that my WAN ip address is
"A.B.C.D"
and my firewall forwards port
"nnn"
to my Ubuntu server
192.168.4.6 port 22

I am always able to remotely ssh into this server by doing:
```
ssh    remoteMe@A.B.C.D     -p nnn
```
Works great all the time.


So now I want to setup a SSH VPN.
I am following the instructions on:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

I did the IP Forwarding with:
```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

[sudo] password for ME:
1
```

Then on my (remote client Ubuntu) laptop, I did:
```
 sudo   ssh  -w 0:A.B.C.D    -p nnn
[sudo] password for ...
Bad tun device '0:A.B.C.D'
```
What does "Bad tun device" mean?
How do I fix it?

---

### Post by boondocks on 2008-04-03
My mistake.
It should have been:
```
sudo  ssh   -w 0:0  A.B.C.D    -p nnn
NOT
sudo   ssh  -w 0:A.B.C.D    -p nnn
```

This works and takes me one step further.
I am able to ssh into server A.B.C.D and then I see
> channel 1: open failed: administratively prohibited: open failed

---

### Post by chrisdew on 2008-06-05
I had the same problem, but realised that I'd overlooked one of the steps...

Adding

 PermitRootLogin yes
 PermitTunnel yes

to /etc/ssh/sshd_config


Regards,

Chris.

---

