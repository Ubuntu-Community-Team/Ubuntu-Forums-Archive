---
title: "DNS &amp; DHCP server help"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2008-01-17
I am running a DNS server on my home network and it's working great, I wish to setup a DHCP server aswell, but I can;t get it going i get this error:

```

[B][FONT=Arial][SIZE=3]dhcpd self-test failed. Please fix the config file.
The error was: 
WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
/etc/dhcp3/dhcpd.conf line 126: expecting key name.
	key ;
        ^
Configuration file errors encountered -- exiting
 
```

[SIZE=2][FONT=Tahoma]I think i need a TSIG key or something to use DNS and DHCP at the
same time with the DHCP server updating the DNS server. how do I do this???
[/FONT][/SIZE][/SIZE][/FONT][/B]

---

### Post by Ocxic on 2008-01-17
bump

---

### Post by ICberg7 on 2008-01-19
did you install dhcpd using the package manager?
What does your etc/dhcpd.conf file look like?

---

