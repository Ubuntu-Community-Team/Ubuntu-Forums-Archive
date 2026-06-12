---
title: "Should 127.0.0.1 only resolve to localhost, or my hostname as well?"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by mjgumbley on 2007-01-29
My /etc/hosts reads like:
> 
127.0.0.1 localhost.localdomain localhost myhostname
192.168.7.32 myhostname.mydomain.net myhostname


Is this correct? (I have a feeling that's the way the installer set it up)
Or should myhostname only be referenced against the 192.168.7.32 address, with localhost being reserved for the local loopback adapter?

If I remove the myhostname entry from 127.0.0.1, what might break?

[http://gentoo-wiki.com/Talk:TIP_Setup_Your_FQDN](http://gentoo-wiki.com/Talk:TIP_Setup_Your_FQDN)
says that the above is fine...


(I'm having issues with a Java RMI server program I'm writing that searches for the local host name during RMI registry lookups, and always finds it as 127.0.0.1... google for java.rmi.server.hostname - esp article at [http://java.sun.com/docs/books/tutorial/rmi/running.html](http://java.sun.com/docs/books/tutorial/rmi/running.html))

Having to set this Java property to make my code do the right thing makes me wonder whether my /etc/hosts is wrong.....

---

### Post by kosmic on 2007-01-29
127.0.0.1 is and should be ALWAYS your Localhost don't change this :)

127.0.0.1 is the standard [IP]("http://www.tech-faq.com/ip.shtml") address used for a loopback network connection.  
This means that if you try to connect to 127.0.0.1, you are immediately *looped back* to your own machine.
  If you telnet, ftp, etc...  to 127.0.0.1, you are connected to your own machine.
  In other words, 127.0.0.1 is **you**.
  For example, if your system was named "joker", and you attempted to telnet to 127.0.0.1, you would see:
  # telnet 127.0.0.1
Trying 127.0.0.1...
Connected to joker
Escape character is '^]'.

**Also Convincing newbies to connect to 127.0.0.1 is a frequent joke on the Internet. ;)**

  Another name for 127.0.0.1 is *localhost*.
  
To read more about localhost give a look here -> [http://tools.ietf.org/html/rfc3330](http://tools.ietf.org/html/rfc3330)

---

### Post by RandomJoe on 2007-01-30
On a Slackware system, this is part of what's in /etc/hosts:
```

# By the way, Arnt Gulbrandsen <agulbra@nvg.unit.no> says that 127.0.0.1
# should NEVER be named with the name of the machine.  It causes problems
# for some (stupid) programs, irc and reputedly talk. :^)

# For loopbacking.
127.0.0.1     localhost

# This next entry is technically wrong, but good enough to get TCP/IP apps
# to quit complaining that they can't verify the hostname on a loopback-only
# Linux box.
127.0.0.1     slackware.example.net slackware

```

If the system gets configured for DHCP, the second "technically wrong" line gets the domain name changed to whatever your hostname and domain is.  A fixed-IP system doesn't get that line - you get a proper line like the second one you list.

So no, you don't need the machine's hostname appended to the 'localhost' line, although normally it doesn't cause problems and is usually left there for DHCP systems so that programs don't stall and complain about not finding the machine's IP when looking up by hostname if the system doesn't get an IP.

---

