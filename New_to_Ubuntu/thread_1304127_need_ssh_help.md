---
title: "need ssh help"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mvalviar on 2009-10-29
I'm trying to connect to a remote machine using ```
$ssh myusername@myremotemachine
```. I'm always getting connection timed out. Help me please. Thanks.

---

### Post by teward on 2009-10-29
> **mvalviar said:**
> I'm trying to connect to a remote machine using ```
$ssh myusername@myremotemachine
```. I'm always getting connection timed out. Help me please. Thanks.

Just a thought, but are you connecting to the right port on the computer (if the computer is behind a firewall)?

---

### Post by Aemaeth on 2009-10-29
can you ping the machine? If not TrekCaptain is probially right to assume that you are behind a firewall or router. If you are behind a router and feel up to the task you can configure port triggering (if your router supports it) and it will send all incoming ssh requests (default port 22) to that machine...

---

### Post by teward on 2009-10-29
There are exceptions to my above statement, of course, which are not listed here at this time.

---

### Post by mvalviar on 2009-10-30
I can ping the remote machine. I also tried ssh <ip> -l <user> and got the same result. I've read that this may be caused by a firewall or the settings of iptables. I really don't understand much about firewalls or tcp/ip. Please help me.

---

### Post by nothingspecial on 2009-10-30
If you use the -v flag it will tell you what`s happening. You can increase the verbosity to a maximum of 3 vs so

```
ssh -vvv user@ipaddress
```

That may throw some light on the situation. 

You have got openssh-client installed - just checking

---

### Post by mvalviar on 2009-10-30
```
mvalviar@mumee:~/src/php$ ssh -vvv user@host
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to host [xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx port 22: Connection timed out
ssh: connect to host host port 22: Connection timed out
```

---

### Post by JohnLM_the_Ghost on 2009-10-30
> **mvalviar said:**
> ```
mvalviar@mumee:~/src/php$ ssh -vvv user@host
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to host [xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx port 22: Connection timed out
ssh: connect to host host port 22: Connection timed out
```

Well as said before, remote machine apperars to be behind NAT and/or firewall.
Is the remote machine on the same local subnet or is it over connected internet?
If you don't know you could give us it's IP address (we actually need first or first two numbers from adress).
192.x.x.x and 127.x.x.x are local adresses, and most other are remote (internet) ones.

So in case of firewall, you will need to allow connections to port 22
And in case of NAT you will need to configure forwarding of port 22 to that particular machine.

btw In case of NAT pinging doesn't do much good, cause any subnet computer can reply to it, including the NAT router itself.

---

### Post by mvalviar on 2009-10-30
I'm dumb. I got it. I got the wrong IP address.

---

