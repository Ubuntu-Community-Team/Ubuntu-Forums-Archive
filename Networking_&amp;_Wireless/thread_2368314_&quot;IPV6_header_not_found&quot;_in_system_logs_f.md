---
title: "&quot;IPV6 header not found&quot; in system logs for ICMP6 Router Advertisements"
date: 2017-08-09
forum: Networking &amp; Wireless
---

### Post by apoz on 2017-08-09
Hi all,

I'm running a server with Ubuntu 16.04 (kernel 4.4.0-62-generic) with some virtual machines handling IPv6 traffic.

Apparently, every time a VM sends a ICMP6 router advertisement, I get a log in syslog of "IPV6 header not found".

I inspected the packets in the physical interface and they seem OK to me:

```

11:42:34.666022 02:XX:XX:XX:XX:XX > 33:33:00:00:00:01, ethertype 802.1Q (0x8100), length 158: vlan 203, p 0, ethertype 802.1Q, vlan 169, p 0, ethertype IPv6, fe80::XXXX:XXXX:XXXX > ff02::1: ICMP6, router advertisement, length 96
`....`:...........@...!w....................@...............@.!w..........@.... ........*..    ..!w................*..    ..!w.............    '.
11:42:35.683194 02:XX:XX:XX:XX:XX > 33:33:00:00:00:01, ethertype 802.1Q (0x8100), length 158: vlan 203, p 0, ethertype 802.1Q, vlan 144, p 0, ethertype IPv6, fe80::XXXX:XXXX:XXXX > ff02::1: ICMP6, router advertisement, length 96
`....`:...........@...!^...................U@...............@.!^..........@.... ........*..    ..!^................*..    ..!^.............    '.

```

```

sysadmin@olnmpep02318n001:~$ sudo tail -f /var/log/syslog
Aug  9 12:01:04 hostname kernel: [1638581.817138] IPv6 header not found
Aug  9 12:01:04 hostname kernel: [1638582.040507] IPv6 header not found
Aug  9 12:01:07 hostname kernel: [1638584.590434] IPv6 header not found
Aug  9 12:01:10 hostname kernel: [1638587.772732] IPv6 header not found

```

I am not sure if it's related to the problem, but the traffic gets Q-in-Q'ed on the way out of the server (one tag is included by the OVS the VM is attached to, and the other tag is included by a veth of VLAN type).


[B]Anyone has faced this problem before? Any hint pointing out where I could investigate further?

[/B]Things I already did:
[LIST]
[*]All the sysctl net.ipv6.conf.*.forwarding parameter is 0 and net.ipv6.conf.*.accept_ra is 0 also, so Router advertisements should not be accepted (just forwarded).
[/LIST]

I tried to check the code printing that log, and it seems the offset is wrong or the version is not 6, but I checked the packets in Wireshark and they look fine to me...

```

    if (*offset) {
        struct ipv6hdr _ip6, *ip6;

        ip6 = skb_header_pointer(skb, *offset, sizeof(_ip6), &_ip6);
        if (!ip6 || (ip6->version != 6)) {
            printk(KERN_ERR "IPv6 header not found\n");
            return -EBADMSG;
        }
        start = *offset + sizeof(struct ipv6hdr);
        nexthdr = ip6->nexthdr;
    }
```


Thank you very much in advance!

Regards,
apoz

---

