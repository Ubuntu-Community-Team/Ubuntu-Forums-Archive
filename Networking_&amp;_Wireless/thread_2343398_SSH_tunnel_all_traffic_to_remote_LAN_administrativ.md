---
title: "SSH tunnel all traffic to remote LAN: administratively prohibited"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by Curtis.Everingham on 2016-11-15
Hello, and thanks in advance for any help.

I'm following the help.ubuntu guide here: [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

My scenario is almost identical to the one depicted in that article. I have SSH access and a sudo user on both machines, both are running 16.04, and are up to date using apt-get. I need to get Machine B's traffic all tunneled into Network A.

As instructed in the guide, here is the command I'm issuing on Machine B:
```
sudo ssh -NTf -w 0:0 myusername@networkA's.routable.IP.address
```

On doing that, I get prompted for sudo locally, and then I get prompted for SSH login to [email]myusername@networkA's.routable.IP.addres[/email]s. I then get the following error:
```
channel 0: open failed: administratively prohibited: open failed
```

I've been searching around, trying to resolve the issue myself. Here is what I've tried, which has not made any difference:

The following lines are present in /etc/ssh/sshd_config (leaving out the rest of the stuff, for brevity. It's all set to default except what I've included):
```

PermitRootLogin yes
PermitTunnel yes
AllowTCPForwarding yes
PermitOpen any
TCPKeepAlive yes
MaxSessions 256


```

Checked IPtables on Machine A: After adding an "allow all" rule to each, here is the output of command sudo iptables -L:
```
Chain INPUT (policy ACCEPT)
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
```

I haven't found anything online yet which makes any difference. What am I missing that is causing this connection to be denied?

Thanks again for any help

---

### Post by TheFu on 2016-11-16
Turn up the debugging from ssh with -vvv option.
And just to be clear, I did NOT validate the ssh command you are using.

---

