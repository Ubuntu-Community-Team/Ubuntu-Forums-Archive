---
title: "Browsers cannot access internet, but Pings work"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by ElSean on 2008-02-14
I'm running Ubuntu 7.4, I can ping from the terminal using both DNS and IP addresses.  But none of the web browsers can open sites (firefox, opera, etc).

I've disabled ipv6 completely.

I did a traffic capture with wireshark, when I attempt to access a site, I see the DNS query and the response.  Then there is no more traffic, the DNS resolution is valid though.

Does anyone have any suggestions?

Thanks!

---

### Post by nixscripter on 2008-02-21
The next question I would look at is, how far is the connection getting. This will be a bit technical.

Try running this in the terminal, and see if any traffic shows up when you try to access a website:

```
sudo tcpdump -i any 'tcp[tcpflags] & (tcp-syn) != 0 and tcp port 80'
``` 

The output will be messy, but lines should look like:

```
date-and-time IP computer-name.portnum > www.destination.com.www: S blah blah blah
```

That is a SYN packet going by, the first step in a TCP connection. If you don't see that, then your computer isn't transmitting the request, and that's the problem.

There should also be another SYN packet going the other way:

```
date-and-time IP www.destination.com.www > computer-name.portnum: S blah blah blah
```

If that doesn't happen, then the connection is being dropped somewhere along the line, and that's the problem.

If both happen, more tests.

---

