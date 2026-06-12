---
title: "Port Not listening ..."
date: 2009-09-19
forum: New to Ubuntu
---

### Post by mamut0o1 on 2009-09-19
Hello everyone; I need to have port 5060 open; so I created an entry using: sudo iptables -A INPUT -p udp -m udp --dport 5060 -j ACCEPT

When I check to see my active connections I get the following:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:512             0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:5038          0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -
tcp6       0      0 :::512                  :::*                    LISTEN      -
tcp6       0      0 ::1:631                 :::*                    LISTEN      -
udp        0      0 0.0.0.0:2727            0.0.0.0:*                           -
udp        0      0 0.0.0.0:4520            0.0.0.0:*                           -
udp        0      0 0.0.0.0:47658           0.0.0.0:*                           -
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           -
udp        0      0 0.0.0.0:4569            0.0.0.0:*                           -
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -

I'm wondering why port 5060 is not on status "LISTEN". Does this means that port 5060 is not active?
I have open my ports from the router so could anyone please explain how can I troubleshoot this issue.

thanks!

---

### Post by mapes12 on 2009-09-19
Try this:

[www.lmgtfy.com/?q=port forwarding](www.lmgtfy.com/?q=port forwarding)

---

### Post by lovinglinux on 2009-09-19
Opening the port in the firewall or router has nothing to do with listening ports.

To get a "LISTEN" report on that port you need to have an application (server) listening to that port, otherwise the port is virtually closed, even if you open it in the firewall and the router. Any incoming connection requests on that port will pass through the router and the firewall, but will be refused when reaching the port, because there isn't any application listen to it.

On the other side, if you don't open all those other ports with listening servers in the firewall and the router, they will also be refused, even with an application listening to them.

I guess you used netstat -plntu to get that report right?

I'm not sure why the port 5060 is the report, but doesn't have a listening server. Perhaps because it's udp. I'm not an expert on this, so you might need other opinions. Anyway, which application should be listening to that port?

---

### Post by mamut0o1 on 2009-09-19
> **mapes12 said:**
> Try this:

[www.lmgtfy.com/?q=port forwarding](www.lmgtfy.com/?q=port forwarding)

Thanks for the link but as I mentioned above I have the ports already open from the router.

---

### Post by mamut0o1 on 2009-09-19
> **lovinglinux said:**
> Opening the port in the firewall or router has nothing to do with listening ports.

To get a "LISTEN" report on that port you need to have an application (server) listening to that port, otherwise the port is virtually closed, even if you open it in the firewall and the router. Any incoming connection requests on that port will pass through the router and the firewall, but will be refused when reaching the port, because there isn't any application listen to it.

On the other side, if you don't open all those other ports with listening servers in the firewall and the router, they will also be refused, even with an application listening to them.

I guess you used netstat -plntu to get that report right?

I'm not sure why the port 5060 is the report, but doesn't have a listening server. Perhaps because it's udp. I'm not an expert on this, so you might need other opinions. Anyway, which application should be listening to that port?

No I did netstat -tulpn; but when I do netstat -plntu I get the server that is suppose to be listening at that port which is asterisk. Take a look:
 udp        0      0 0.0.0.0:5060            0.0.0.0:*                           2233/asterisk

any ideas?
thanks again!

---

### Post by lovinglinux on 2009-09-19
> **mamut0o1 said:**
> No I did netstat -tulpn; but when I do netstat -plntu I get the server that is suppose to be listening at that port which is asterisk. Take a look:
 udp        0      0 0.0.0.0:5060            0.0.0.0:*                           2233/asterisk

any ideas?
thanks again!

I guess -tulpn shoud give the same results as -plntu :) Check **man netstat **for more info.

---

### Post by mamut0o1 on 2009-09-19
> **lovinglinux said:**
> I guess -tulpn shoud give the same results as -plntu :) Check **man netstat **for more info.

yes it does but the only difference is that it does not list the server Listening on that port. That's the only difference I noticed. But I still have the same issue; I will check my configuration files. If you think of something else or anyone else please let me know.


thank you all.

---

### Post by MauroTyler on 2010-12-06
Sometimes the answer is so obvious that it gets overlooked, and I can't blaim anyone, I'm a victim of that sooo many times..

Once again.. check the following lines from your post:

tcp        0      0 0.0.0.0:512             0.0.0.0:*               LISTEN      -
udp        0      0 0.0.0.0:5060            0.0.0.0:*                           -

What's the difference between those 2 lines, besides the port number?

The problem is that 5060 port is UDP, not TCP... nothing will ever bind to that port, because UDP ports do not listen. 
UDP port = "mailbox"
TCP port = "telephone"

That's why you're not seeing the "LISTEN" word.

Cheers!

---

