---
title: "SSH Server Problems"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by Garibaldi3489 on 2007-10-18
Hello,

I am running the latest version of Ultimate Ubuntu 1.4, which is basically Feisty with some restricted add-ons. I would like to be able to ssh into this machine, so I installed openssh-server with Synaptic. I then ran /etc/init.d/ssh restart and several other commands to try and get ssh up and running. I then tried
# ssh localhost
from this machine and I was able to log in fine. However, trying to ssh into it from any other machine on the network returns an error similar to this:
ssh: connect to host ytterbium port 22: No route to host


Any ideas why this is so troublesome?

---

### Post by tkharris on 2007-10-18
Try using the full IP address, you likely don't have an /etc/hosts file confiured with:

```

some.ip.address.here ytterbium

```

---

### Post by Garibaldi3489 on 2007-10-18
Thanks, I gave that a shot from two different machines and both returned:
> 
ssh: connect to host xxx.xxx.xxx.xxx port 22: Network is unreachable


---

### Post by tkharris on 2007-10-18
Are you sure the ethernet cable is plugged in?

It's on the same subnet?

No firewalls preventing this?

---

### Post by Garibaldi3489 on 2007-10-18
> **tkharris said:**
> Are you sure the ethernet cable is plugged in?

It's on the same subnet?

No firewalls preventing this?

Yep I have internet access on the machine in question and I can also ssh from that machine to the other machines that I've been trying to ssh into it from. This all works fine. It is indeed on the same subnet and it is even in the /etc/hosts on the server. There are no firewalls between these machines. This is what makes it so mystifying to me! Could there be some other program or something blocking or capturing port 22?

---

### Post by tkharris on 2007-10-18
Since everything else is working, those computers probably don't see the new one.  I would recommend using sendarp ( [http://www.abiogenesis.com/jrs/sendarp/](http://www.abiogenesis.com/jrs/sendarp/) ) and seeing if that straights out your problem.

---

### Post by louie55 on 2007-10-18
Have you double checked that the IP address is correct??

When I try to SSH to a non-existing IP address (on the same subnet) on my machine, I get
```
ssh 192.168.0.214
ssh: connect to host 192.168.0.214 port 22: No route to host
```

 If I try to ssh using a name that doesn't exist in my /etc/hosts file, I get:

```
ssh george
ssh: connect to host george port 22: Connection refused
```

As you can see, I do not get "No Route To Host" as you did when typing a name. This suggests that in your situation it was getting an IP from the name, but the IP didn't exist. Thus giving you a "No Route To Host" message as it did with me when I used a non-existing IP.

You can do a port scan on the machine to test for open ports.

```
nmap -sT x.x.x.x
```

Replace the x's with your server IP.

If you don't have nmap, you can do

```
sudo apt-get install nmap
```

It is a very useful networking tool.

Louie

---

### Post by tkharris on 2007-10-18
What version of ssh are you using?

```

$ ssh -V
OpenSSH_4.3p2 Debian-9, OpenSSL 0.9.8c 05 Sep 2006

```

```

$ ssh doesnotexist
ssh: doesnotexist: Name or service not known

```

When I ssh into a non-existent name, it can't look it up in DNS or /etc/hosts, thus it gives a DNS error.

Connection refused means that the server sent an RST packet, which it can only do if it's up and has a TCP/IP stack.  Network is unreachable happens when the interface is messed up.  If it's a firewall issue where it's dropping packets, but the computer is found, it would be a timeout.

---

### Post by louie55 on 2007-10-18
> What version of ssh are you using?

Not sure if the question is for me or the topic creator, but I am using:

```
ssh -V
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
```

Here's what I get:
```
ssh doesnotexist
ssh: connect to host doesnotexist port 22: Connection refused
```

Louie

---

### Post by Garibaldi3489 on 2007-10-19
Thank you for all your help! I can now SSH into the computer! I found out where my problem was - when I looked at the output for ifconfig on the machine, I accidentally read off the bcast instead of the IP address! Thanks for helping me find that silly mistake!

---

