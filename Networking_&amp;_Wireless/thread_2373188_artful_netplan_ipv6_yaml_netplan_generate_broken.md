---
title: "artful netplan ipv6 yaml netplan generate broken"
date: 2017-10-03
forum: Networking &amp; Wireless
---

### Post by slykens on 2017-10-03
Hello -

I have set up an artful VM to start testing with today and must admit to being frustrated by the ifupdown->netplan transition.

In my instance I have static IPv4 and IPv6 addresses to be assigned to a particular interface. The only documentation I can find on IPv6 in relation to netplan is in the manpage for netplan. There it states:

```
 
addresses (sequence of scalars)     
         
Add static addresses to the interface in addition to the ones received through DHCP or RA.  Each sequence entry is in CIDR  notation,  i.   e.
of the form addr/prefixlen.  addr is an IPv4 or IPv6 address as recognized by inet_pton(3) and prefixlen the number of bits of the subnet.

Example: addresses: [192.168.14.2/24, 2001:1::1/64]
```

Following this advice I have set my IPv4 and IPv6 static addresses following the convention specified.

When I try to generate the backend config using "netplan --debug generate" the following error is returned:

```
Invalid YAML at //etc/netplan/01-netcfg.yaml line 7 column 40: found unexpected ':'
```

Clearly, netplan is telling me the : in the IPv6 address is unexpected even though the manpage clearly states this is how it is to be configured. Further, netplan appears to count lines and columns starting at 0 which doesn't make sense, either.

Any ideas?

---

### Post by kees-r on 2017-11-29
I had the same issue. Apparently the correct syntax is:

```

addresses: 
  - 192.168.14.2/24
  - 192.168.14.3/24
  - 2001:1::1/64
  - 2001:1::2/64
```

---

### Post by powersj on 2017-11-29
In a YAML the colon ':' is a special character. Using the mechanism above or putting quotes around the value would also help. I would also suggest using a YAML syntax validator (e.g. [http://www.yamllint.com/](http://www.yamllint.com/)) to check your configuration as well.

Good:
```

addresses: 
  - 2001:1::1/64

```

Should also work:
```

addresses: ["2001:1::1/64"]

```

Bad, do not use this:
```

test: [2001:1::1/64]

```

---

### Post by powersj on 2017-11-29
I filed the following bug about this: [https://bugs.launchpad.net/netplan/+bug/1735317](https://bugs.launchpad.net/netplan/+bug/1735317)

---

