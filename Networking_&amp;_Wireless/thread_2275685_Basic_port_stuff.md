---
title: "Basic port stuff"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by huff2 on 2015-04-27
Hey guys,

I'm new and trying to learn about ports. When I used the ufw allow command for say, port 1715, it seems to work. The return message says, rule added. However I used nmap localhost and it said only port 631 was open. Am I missing something? I'm learning so please help me out guys.

---

### Post by ian-weisser on 2015-04-27
An 'open port' means that a process is bound to that port and listening/sending/receiving upon that port.
Allowing/disallowing traffic upon that port does not 'open' or 'close' the port. Same port, totally different action.

Example:
I allow traffic (ufw) on port 1715, AND start an application that sends/receives data upon the port. The port is OPEN.

Example:
I allow traffic (ufw) on port 1715, BUT don't start the application. The port is CLOSED.

Example:
I disallow traffic (ufw) on port 1715, AND start an application that sends/receives data upon the port. The port is BLOCKED. The application cannot connect.

When I wanted to learn about sockets and ports, I stopped using UFW and other tools that hide important concepts, and began using iptables directly.

---

### Post by huff2 on 2015-04-27
How do I open and close a port?

---

### Post by bab1 on 2015-04-27
> **huff2 said:**
> How do I open and close a port?

It's not like a faucet that you turn off or on.  It is a 16 bit number in a network packet header that is part of a dupal (IP Address/port number).  The server is configured to look for packets with the appropriate port number listed in the packet header.  If it sees one of those it accepts it.  The firewall can also filter those same packets and deny traffic based on that port number.  See [here]("http://en.wikipedia.org/wiki/Port_number") and [here]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers").

[COLOR="#0000FF"]Rdit: To answer your question directly; you can filter the packets at the fire wall and deny net flow or you can turn off the server scanning for packets with that port number in the packet header.[/COLOR]

---

### Post by huff2 on 2015-04-27
thanks!

---

