---
title: "ssh possible, but no ougoing connection during ssh session"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by TINUSZ on 2014-03-26
Hello,

Ik hope i can explain myself.

I have setup a ubuntu server 12.04 with a webserver and ssh.
I have setup the server to use a static ip also setup my router to do port forwarding to this ip.

This is all working fine. I can connect to the server from outside my home network and the webserver is also available

But when i am connect via ssh i cannot connect to the outside world.
I can't ping google.com
I can't "sudo apt-get update"
however i can ping my home router.

I do not undstand why, i just connected to the machine from the internet and now the server can't find the internet.

thanx!

Martijn

---

### Post by steeldriver on 2014-03-26
Hello and welcome to the forums

Can the server ping external hosts by numeric IP e.g. 
```
ping -c4 8.8.8.8
```
(one of Google's public DNS servers)

---

### Post by TINUSZ on 2014-03-26
yes.

i tried "ping 82.94.234.46" (google) and it worked

---

### Post by steeldriver on 2014-03-26
So it sounds like you have not configured any DNS server(s) - usually, for a static connection defined in your /etc/network/interfaces file you would need to add a valid **dns-nameservers** entry something like

```

# The primary network interface
auto eth0
iface eth0 inet static
.
.
.
**dns-nameservers 208.67.222.222 208.67.220.220**

```

(replace **208.67.222.222 208.67.220.220** with your chosen server(s))

---

### Post by TINUSZ on 2014-03-26
you are my hero!
It is all working fine now

---

### Post by steeldriver on 2014-03-26
Happy to help - please use the 'Thread tools' to mark the thread '[Solved]'

---

