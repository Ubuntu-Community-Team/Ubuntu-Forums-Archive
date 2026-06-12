---
title: "Open a port?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-07-09
I have a service that is trying to access several ports that are apparently closed.

How do i get Linux to open them?

---

### Post by jonobr on 2009-07-09
HEllo

AFAIK Usually you have an application or daemon listening and waiting and listening on certain port numbers or that will open the port when invoked.

So I suppose opening the port is only useful if you have application or service behind it that knows what to do with the traffic.

From your question Im thinking you application opening the ports, is trying to connect to something that is not provisioned or configured correctly, or just not accepting connections

Open to correction to all of this

---

### Post by jonobr on 2009-07-09
mmmm.....

I see a lot more detail in your post [HERE]("http://ubuntuforums.org/showthread.php?t=1195272")

With some tcp connections you can test connectivity by telnet to the port on that port number

eg telnet ipaddress 80

And it should show if a connection is made.
your netstat command should show you an established connection on that port number.
For your udp Im not sure, 
maybe a wireshark or tcpdump will show you packets being recieved and how they are treated by the ubuntu box.
Usually if a port will not open, you get a packet response typically saying 
application not avaible or port unreachable or something of that nature

---

