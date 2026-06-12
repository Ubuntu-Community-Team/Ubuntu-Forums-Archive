---
title: "sshd stopped working after 2007-10-0x updates"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-10-07
Been using a laptop as ssh server for many months.  I never touch this laptop apart from to turn it on (auto shutdown).  The other day, there were 16 updates one day then 19 updates a few days later...since then I cannot access my ssh server.

I can access it locally with 'ssh localhost', but even from the ssh server itself, I cannot do 'ssh 192.168.1.110'...I get a timeout and message "connection closed by 192.168.1.110'.

I can ping the IP from both the server and the client laptop I have.

Apart from doing updates, nothing has changed!  Any ideas what the problem could be?

---

### Post by kevdog on 2007-10-07
Make sure you open a port up in your firewall (port 22) to allow incoming connections?? You should be able to do ssh localhost from the server computer itself however

---

### Post by finite9 on 2007-10-07
I dont have a software firewall installed on either the server or the client.  In my gateway router, I have a firewall, with port 22 open to the fixed IP of the server, but this should not be needed on my LAN, as the firewall is only between WAN and LAN, not within the LAN.

I do not think it has anything to do with network or client PC, as I cannot even do ssh 192.168.1.110 from the ssh server itself!!

Maybe it is not directly ssh related...maybe it is something wrong with my network interface config, but like I said, I have not changed anything!  So I need help in trying to figure out what could be wrong, or why it would suddenly stop working.

---

### Post by kevdog on 2007-10-07
Can you ssh localhost from the server itself???  You might have a DNS issue.  I thought -- although I could be wrong - that by default all incoming ports on any Ubuntu machine were closed by default, so that either through a gui firewall (firestarter or guarddog) or by manipulating the IP tables directly at the command line, you needed to open up port 22 on the server for incoming connections.

---

### Post by noob12 on 2007-10-07
Can you post the output of these to tell us which interfaces the server is listening on and if you have any firewall rules.  Maybe we'll see something.

```

netstat -tnl

sudo iptables -nL

```

---

