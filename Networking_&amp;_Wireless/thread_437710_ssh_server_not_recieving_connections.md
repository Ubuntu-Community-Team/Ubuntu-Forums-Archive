---
title: "ssh server not recieving connections?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-05-09
I'm trying to run the standard sshd server on my computer, but I can't connect into it from my laptop (on the same network). I had it running fine in Dapper, but after I did a (clean reinstall) upgrade to Feisty it doesn't work simply after starting the server. Is there some default setting in Feisty that's different?

I dropped a packet sniffer on both the client and server and I see the SYN packets leaving the client and being reaching the server, only to be replied to with ICMP or RST,ACK packets. And I know I'm trying to connect on the correct port.

---

### Post by haricharan on 2007-05-09
You can try 'ssh' ing on to ur server from itself by addressing as localhost. Also if you could post what error do you receive it wud be helpful...

---

### Post by .rdg on 2007-05-09
B-Con did you check if your sshd is running (especially after the system boot)? I know I had problems with sshd starting automatically. To check you can issue the following in the terminal:

netstat -lnt | grep :22

I'm assuming you didn't change the port the ssh server is listening on (if so change the above 22 to the port you actually use).

If the ssh is running try connecting locally:

ssh localhost or
ssh 127.0.0.1

If you are able to connect to yourself locally again try to connect to your PC but from other location. If you can't you could check if you have any firewalling going on (terminal):

sudo iptables -L

Please post your observations,
.rdg

---

### Post by B-Con on 2007-05-18
Hm, interesting, my ssh server isn't even starting.
```
b-con@*******:~$ sudo /etc/init.d/ssh start
Password:
 * Starting OpenBSD Secure Shell server...                               [fail] 

```

Why might it fail (apparantly it's never worked)? Are there any log files I can look at?

---

### Post by B-Con on 2007-05-19
Hm, simply removing and reinstalling the openssh-server package fixed the problem. The installation I was working with before was pretty new itself. Weird.

---

