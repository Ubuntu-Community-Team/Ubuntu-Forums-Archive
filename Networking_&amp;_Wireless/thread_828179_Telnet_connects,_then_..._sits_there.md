---
title: "Telnet connects, then ... sits there"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by awacs on 2008-06-13
Ok, I'm stumped. New install of Feisty, trying to get telnet working (need it in addition to ssh). 

I:
installed telnetd, 
installed xinetd, 
setup telnetd as a service in xinetd.conf through tcp wrappers, enabled telnet (from local machines) in tcp wrappers

when I connect:
# telnet localhost, I get:
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

and that's it. No banner, no response to keystrokes. netstat tells me that i'm connected:
tcp       12      0 127.0.0.1:23            127.0.0.1:46388         ESTABLISHED

and so does lsof:

xinetd   6352    root    7u  IPv4  109773       TCP 
*:telnet (LISTEN)
telnet  18207    root    3u  IPv4  402134       TCP localhost:46388->localhost:telnet (ESTABLISHED)
tcpd    18208 telnetd    0u  IPv4  402135       TCP localhost:telnet->localhost:46388 (ESTABLISHED)

and the telnet client responds to ^] and lets me disconnect.

Oh, and daemon.log reports:
Jun 13 13:23:04 geulah tcpd[18138]: connect from 
localhost (127.0.0.1)
Jun 13 13:23:35 geulah last message repeated 5637 times

No kidding. It looks like it keeps connecting again and again - why?

Anyone know what's going on?

---

### Post by awacs on 2008-06-18
bump, he said hopefully?

---

