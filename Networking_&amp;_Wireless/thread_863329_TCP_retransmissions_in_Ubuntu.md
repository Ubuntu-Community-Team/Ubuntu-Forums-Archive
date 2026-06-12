---
title: "TCP retransmissions in Ubuntu"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by mjimeno on 2008-07-18
Hello,
I'm kind of new in Ubuntu. Even so, I jumped into recompiling the kernel to make TCP do something I want it to do. I've managed it well, =). The problem is the following:
Test bed: one machine on Windows, one with Ubuntu 7.10, kernel 2.6.14.22, (I guess, or 22.14). Client app running on Windows, server app running on the Ubuntu. Machine with Client is disconnected on purpose (no socket shutdown).
Problem: When TCP can't deliver a packet, it will start retransmitting. I read and found the constant that sets the maximum number of retransmissions, which is 15. After that, TCP "should" give up and close the connection. I changed that number to be large, (for research purposes) but, it doesn't work, because:
Ubuntu doesn't wait until 15 retransmissions. After like 6 or 7 retransmissions, it starts sending ARP packets asking for the missing PC. After 9 rounds of 3 ARP packets, it closes the connection and the socket returns "no route to host". Meanning, ARP triggered the connection shutdown. Is there something else I'm missing in Ubuntu?
I tried the same with Unix, and it actually retransmits until the maximum (13 in Unix) and then gives up, with no ARP packets. 
Any suggestions, please???
Thanks a lot!!!
Regards, Miguel

---

### Post by johnl on 2008-07-21
Not sure about your specific problem, but I would try changing the value like so instead of recompiling the kernel:

(as root):
```

echo 45 > /proc/sys/net/ipv4/tcp_retries2

```

---

### Post by mjimeno on 2008-07-21
hello johnl, thanks for your response. 
* Regarding my original question, even though I know better now what's happening, I still don't get where in the code is happening and why. I understand that TCP starts retransmitting, but there is a timer for ARPs to be sent. So, if after x seconds there is no respond for the retransmissions, the system starts sending ARPs and retransmissions stop. I don't see this in Unix. And, from my vague TCP knowledge, the connection should be closed when the maximum # of retx is reached, not when the link layer decides is enough. Anyhow, suggestions are welcome.
* I didn't know I could change tcp_retries with a linux command. I've found that I was able to change TCP write and read buffers with changing a file, but didn't know about this one. Do you or anybody else know where can I find a list of variables that I can modify just like you showed to me?
Thanks, M

---

### Post by signifer123 on 2008-08-26
Edit:Sorry I forgot to check the date of the original posting.

> **mjimeno said:**
> 

* I didn't know I could change tcp_retries with a linux command. I've found that I was able to change TCP write and read buffers with changing a file, but didn't know about this one. Do you or anybody else know where can I find a list of variables that I can modify just like you showed to me?
Thanks, M

Just call `ls` on /proc it has a ton of variables you can read(some you can write). there is also the `sysctl` command.

so for ipv4 variable list use:(blue text is another directory)
```
ls /proc/sys/net/ipv4
**or you can use **
sysctl net.ipv4
```

view the setting for keepalive time:
```
cat /proc/sys/net/ipv4/tcp_keepalive_time
**or**
sysctl net.ipv4.tcp_keepalive_time

```

set the setting for keepalive time(already shown, but not with sysctl)
```

echo "7200" > /proc/sys/net/ipv4/tcp_keepalive_time
**or**
sysctl -w net.ipv4.tcp_keepalive_time=7200

```

running `man proc` tells you more about the /proc filesystem.

And a page with explainations for the network variables:
[http://ipsysctl-tutorial.frozentux.net/chunkyhtml/tcpvariables.html](http://ipsysctl-tutorial.frozentux.net/chunkyhtml/tcpvariables.html)

As for the closing of the pipe, maybe have a throw at "tcp_keepalive_probes".

---

