---
title: "ssh blocked on every port? HELP!"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by torin on 2007-12-21
its the strangest thing, ssh connections on my apartment buildings network will not connect on any port the remote server is set to. I can ping the host and connect to it via http but ssh just times out no matter what server or port I try, however if I use the internet connection at my office everything works fine, so Im at a loss to explain it. is it possible that my buildings gateway is blocking all ssh protocol on all ports?  and if so how can I work around this, as im on holiday till after the first of the year and I have no access to my remote locations from home.

Regards

---

### Post by heindsight on 2007-12-21
It sounds to me as if the remote host(s?) that you're trying to ssh into are allowing ssh logins from your work network, but not from your home network.

---

### Post by trobbins on 2007-12-21
Did your SSH server ever work?  I had difficulties setting up the ssh server on Gutsy and Edgy.  It would install and appear to work if I established a loopback connection, but it would only listen for IPV6 traffic.

Use : ```
netstat -a | grep ssh
```

My PC returns this:

trobbins@fasterone:~$ netstat -a | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN  

If you see a "tcp6" this means that your computer isn't listening for IPV4 connections.  If this is the case then you need to modify this config file:

 /etc/ssh/sshd_config   

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0  ##<--------UNCOMMENT THIS LINE TO ENABLE IPV4

Restart SSH with :

```
 sudo /etc/init.d/ssh restart

```

---

### Post by mellowd on 2007-12-21
> **torin said:**
> its the strangest thing, ssh connections on my apartment buildings network will not connect on any port the remote server is set to. I can ping the host and connect to it via http but ssh just times out no matter what server or port I try, however if I use the internet connection at my office everything works fine, so Im at a loss to explain it. is it possible that my buildings gateway is blocking all ssh protocol on all ports?  and if so how can I work around this, as im on holiday till after the first of the year and I have no access to my remote locations from home.

Regards

Are you able to telnet to port 22? You won't connect fully but it will tell you if it is not able to reach it.

---

### Post by torin on 2007-12-21
I am trying to access an ssh server that is remote to both locations, I can access every ssh server I try from my office but none from my buildings internet connection and one of these I have control over and have given it many ports restarting sshd with no issues outside of my building

---

### Post by torin on 2007-12-21
> **mellowd said:**
> Are you able to telnet to port 22? You won't connect fully but it will tell you if it is not able to reach it.

even telnet on 22 times out from my building

---

### Post by mellowd on 2007-12-21
Then it seems like they are blocking it. Can you not SSH on another port? This would need to be configured on the server as well.

---

### Post by torin on 2007-12-21
> **mellowd said:**
> Then it seems like they are blocking it. Can you not SSH on another port? This would need to be configured on the server as well.

I have tried that and for whatever reason it dosent seem to work, I have gone as far as setting the remote server to accept ssh over port 80 and I know that isnt blocked because im posting here right now, Im at a loss to explain it. I can hit the server with nmap and see all the open ports but when I try to ssh it just times out and dies :confused:

---

### Post by torin on 2007-12-22
well I have even gone as far as to install windows on an extra HD with a win32 version of open ssh just to confirm that it is indeed a protocol/network issue and not me loosing my mind, but it seems that for what ever reason anything ssh related on my buildings network is blocked and I have no idea how to explain it or work my way around it, so much for being on call through the holidays I guess. if anyone has any insight Im open for suggestions. TIA

Regards

---

### Post by mellowd on 2007-12-23
> **torin said:**
> well I have even gone as far as to install windows on an extra HD with a win32 version of open ssh just to confirm that it is indeed a protocol/network issue and not me loosing my mind, but it seems that for what ever reason anything ssh related on my buildings network is blocked and I have no idea how to explain it or work my way around it, so much for being on call through the holidays I guess. if anyone has any insight Im open for suggestions. TIA

Regards

The best might be simply to ask them to unblock it? It's a very useful port to have access to, and if you use it for work it's 100% essential

---

