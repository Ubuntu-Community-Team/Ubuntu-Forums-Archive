---
title: "isc-dhcpd-server help with on commit"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by dakoellis on 2013-12-10
Hi Guys,

I have been trying to configure my dhcp server to run a script whenever a client connects, and after searching the internet, I can't seem to figure out why it isn't working.  I have to guess it's something simple that I haven't done, or am unable to do.  Basically, I have a simple subnet declaration, and inside that I have my on commit statement.  The addresses are being handed out, and I can see that happening in /var/log/messages, but the on commit part is not running, and I don't know why.  Any ideas?

TIA

```
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.5 192.168.1.100;
on commit {
execute("touch /tmp/test");
}
}
```

edit: just wanted to mention that I have restarted the dhcpd server, and see no error messages anywhere.  The file /tmp/test is not being created.  I originally tried the script I actually want to run, but tried this just to see if it was a problem with my script but it doesn't even create the file.

---

