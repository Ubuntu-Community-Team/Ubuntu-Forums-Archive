---
title: "SLIP interface doesn't send datagrams to upper layers"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by pauloborges on 2013-10-25
[FONT=arial][COLOR=#333333]I'm testing an IPv6 stack implementation for embedded systems. My embedded plaform is connected to an Ubuntu 13.04 machine through RS232 over USB. To test the stack, I'm trying to ping the platform using its link-local address, everything over a SLIP link.
[/COLOR]
[COLOR=#333333]The embedded platform link-local address is fe80::aafb:3dff:fe7f:ede.
[/COLOR]
[COLOR=#333333]To create the SLIP interface I did:
[/COLOR]
```
$ slattach -s 115200 -p slip /dev/ttyACM0
```

[COLOR=#333333]Then, I set the interface's MTU and the link-local address (static one):
[/COLOR]
```
$ ifconfig sl0 mtu 1280
$ ifconfig sl0 add FE80::1/64
$ ifconfig sl0 up
```

[COLOR=#333333]Everything is ok (apparently):
[/COLOR]
```
$ ifconfig sl0
sl0       Link encap:Serial Line IP  
      inet6 addr: fe80::1/64 Scope:Link
      UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
      RX packets:110 errors:0 dropped:0 overruns:0 frame:0
      TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:10 
      RX bytes:4608 (4.6 KB)  TX bytes:1760 (1.7 KB)
```

[COLOR=#333333]To get the sl0 interface dump:
[/COLOR]
```
$ tcpdump -l -i sl0 -XX
tcpdump: WARNING: sl0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on sl0, link-type RAW (Raw IP), capture size 65535 bytes
```

[COLOR=#333333]Then I used ping6:
[/COLOR]
```
$ ping6 -L -I sl0 -c 1 fe80::aafb:3dff:fe7f:ede
PING fe80::aafb:3dff:fe7f:ede(fe80::aafb:3dff:fe7f:ede) from fe80::1 sl0: 56 data bytes

--- fe80::aafb:3dff:fe7f:ede ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```[/FONT][FONT=arial]

[COLOR=#333333]The output from tcpdump is:
[/COLOR]
```
11:35:37.773403 IP6 fe80::1 > fe80::aafb:3dff:fe7f:ede: ICMP6, echo request, seq 1, length 64
    0x0000:  6000 0000 0040 3a40 fe80 0000 0000 0000  `....@:@........
    0x0010:  0000 0000 0000 0001 fe80 0000 0000 0000  ................
    0x0020:  aafb 3dff fe7f 0ede 8000 8187 182d 0001  ..=..........-..
    0x0030:  b981 6a52 0000 0000 04cd 0b00 0000 0000  ..jR............
    0x0040:  1011 1213 1415 1617 1819 1a1b 1c1d 1e1f  ................
    0x0050:  2021 2223 2425 2627 2829 2a2b 2c2d 2e2f  .!"#$%&'()*+,-./
    0x0060:  3031 3233 3435 3637                      01234567
11:35:37.798177 IP6 fe80::aafb:3dff:fe7f:ede > fe80::1: ICMP6, echo reply, seq 1, length 64
    0x0000:  6000 0000 0040 3a40 fe80 0000 0000 0000  `....@:@........
    0x0010:  aafb 3dff fe7f 0ede fe80 0000 0000 0000  ..=.............
    0x0020:  0000 0000 0000 0001 8100 8087 182d 0001  .............-..
    0x0030:  b981 6a52 0000 0000 04cd 0b00 0000 0000  ..jR............
    0x0040:  1011 1213 1415 1617 1819 1a1b 1c1d 1e1f  ................
    0x0050:  2021 2223 2425 2627 2829 2a2b 2c2d 2e2f  .!"#$%&'()*+,-./
    0x0060:  3031 3233 3435 3637                      01234567
```

[COLOR=#333333]Which means that the embedded platform correctly sends ECHO REPLY and the sl0 interface received it. But for some reason, sl0 didn't send it to the application. I got similar results when I ping the all-nodes multicast address ff02::1.
[/COLOR]
[COLOR=#333333]My Ubuntu host can ping another linux machine using its local-link address through eth0 interface. So, the problem seems to be in the sl0 interface.
[/COLOR]
[COLOR=#333333]How can I fix this?[/COLOR][/FONT]

---

