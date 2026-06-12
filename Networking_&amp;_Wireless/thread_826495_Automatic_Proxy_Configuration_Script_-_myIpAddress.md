---
title: "Automatic Proxy Configuration Script - myIpAddress"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by JFire on 2008-06-11
Hey all,

I would like to set up an automatic proxy configuration script which uses eth0 IP address to determine which proxy settings browsers should use.

The automatic configuration script is written in JavaScript.

[HTML]function FindProxyForURL(url, host) {
	if (myIpAddress() == "10.20.38.22") 
		{return "PROXY proxy.somewhere:8080";}
        else
          return "DIRECT";
}
[/HTML]
The problem is that the inbuilt **myIpAddress()** function will always return the ip address of the local loopback adapter (i.e. 127.0.0.1) instead of eth0, which is quite useless.

Does anyone know of anyway to query/capture the eth0 adapters ip address using JavaScript?

Or if anyone has any other ideas of how I can automate changing proxy settings based on IP, I would be very happy to hear it.

Thank you.

---

### Post by mrclisdue on 2009-03-22
Apologies for "grave digging" but I feel it may be useful if someone else has pulled out all hair trying to find a solution.

In hosts file (/etc/hosts) remove any reference to 127.0.0.1 and machine hostname.

Add an entry with machine ip address and hostname.

eg:
```

127.0.0.1 localhost.localdomain
127.0.0.1 laptop <----- remove this
10.20.38.22 laptop <---- add this
```

I'm off to purchase a toupee.

cheers,

---

### Post by JFire on 2009-03-23
Thanks very much! :-)

---

### Post by dvo on 2011-03-02
mrclisdue, thanks a lot!!!

This solved also to me a long-standing nasty problem, 
which has been repeatedly reported as Mozilla bug, e.g.
[https://bugzilla.mozilla.org/show_bug.cgi?id=347307](https://bugzilla.mozilla.org/show_bug.cgi?id=347307)

---

### Post by deezer on 2012-05-17
> **mrclisdue said:**
> Apologies for "grave digging" but I feel it may be useful if someone else has pulled out all hair trying to find a solution.

In hosts file (/etc/hosts) remove any reference to 127.0.0.1 and machine hostname.

Add an entry with machine ip address and hostname.

eg:
```

127.0.0.1 localhost.localdomain
127.0.0.1 laptop <----- remove this
10.20.38.22 laptop <---- add this
```



What if your IP address changes with DHCP?  Are you suggesting that this file needs to be changed every time the IP address changes to get the host?

---

### Post by mvaniersel on 2012-09-17
Yeah, adding a hardcoded IP address isn't much of a solution at all. The point of calling myIpAddress in the PAC file so that you can configure the proxy based on what your current IP address is. If you already knew what the IP address was, you wouldn't need to call that function :)

The real solution is to remove the offending line from your /etc/hosts, but don't replace it with anything else. It's not needed!

---

