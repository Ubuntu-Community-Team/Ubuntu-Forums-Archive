---
title: "Unblocking Ports In SSH"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by Beaver6813 on 2006-11-25
Hey There,

I am extremely new to Ubuntu and have only really got it to run a few perl files on for a friend, basically its a fresh install and i am trying to run this perl file under screen.

screen -A -m -d -S logproxy ./logproxy

Is the command i was told to use on it, however the script is using ports 9180 9181.

I only have SSH access to the machine and i have read about firestarter, however they say to navigate to the blah tab... but i can't really do that :(

Is there anyway to unblock those two ports on Ubuntu?

Thanks :)

Beav

---

### Post by Beaver6813 on 2006-11-25
Can anyone help with this? :( I want to carry on working with my app :)

---

### Post by spd106 on 2006-11-25
Hi, you can try to edit iptables directly by doing
 **sudo iptables -I INPUT --protocol tcp --dport 9180 -j ACCEPT**
and the same for 9181.
Check it over with **sudo iptables -L**.


NB This should allow connections from anywhere, so long as they can authenticate with sshd that is.

---

### Post by Beaver6813 on 2006-11-26
Hey,

Okay ive done that for udp as well just to be sure that i've done it right,

```
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9181
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9180
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9181
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9180
```

Although the script still gives the response Connection Refused [http://www.dsservers.net/BeaveRcon/srclog/](http://www.dsservers.net/BeaveRcon/srclog/)
Although when the server is shutdown it says Timed Out... so that leads me to believe that the script is hitting the server but something is stopping it in ubuntu... Any other ideas? :D

---

### Post by Beaver6813 on 2006-11-26
Any ideas? :(

---

### Post by Beaver6813 on 2006-11-27
Gah i guess i'll have to go back to using Gentoo :( Damn built in firewall...

---

### Post by koenn on 2006-11-27
you can remove all firewall rules by running
```
iptables --flush
```

obviously this is not recommended, but it can help with toubleshooting. 

The real problem is probably that your iptables allow connectections TO ports  9180 9181, but still blocks responses coming back FROM those ports. 

You can add those by using --sprt (source port) or --related and --established (allows connections related to or packages part of an established connection).

---

### Post by Beaver6813 on 2006-11-27
Hey,

Hmm i've tried iptables --sprt 9181, but it returns that --sprt is not a valid command.

Ive tried flush, didn't work so then i added the ports above again, still didnt work, ive made sure that my script is running [http://fremnet.net/article/218/source-log-proxy](http://fremnet.net/article/218/source-log-proxy) is the script. But [http://www.dsservers.net/BeaveRcon/srclog/](http://www.dsservers.net/BeaveRcon/srclog/) still says connection refused. 

Heh, im running outta ideas now :P

---

### Post by jimcooncat on 2006-11-27
Instead of opening more ports, why not tunnel them through SSH? You can do this with command line options, but I find it simpler to use a .ssh/config file. Here, I'm using a machine far away through SSH (on a non-standard port 8822), and forwarding it's webcam (port 9192) and VNC (5801) over it. No need to mess with the firewall, once I've forwarded the SSH port over it I can tunnel any port afterwards.

Host *
  Cipher blowfish
  SetupTimeOut 60
  ConnectTimeout 120
  ForwardAgent no

Host faraway
  HostName machine.faraway.com
  Compression yes
  Port 8822
  LocalForward 9192 localhost:9192
  LocalForward 5801 localhost:5801
  User jim

---

