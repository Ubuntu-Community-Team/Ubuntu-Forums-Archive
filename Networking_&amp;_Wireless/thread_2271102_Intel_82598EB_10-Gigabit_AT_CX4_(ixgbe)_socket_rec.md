---
title: "Intel 82598EB 10-Gigabit AT CX4 (ixgbe) socket recv issue"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by justin.henderson on 2015-03-27
I was able to get the ixbge drivers working in 14.04 by following this thread [http://ubuntuforums.org/showthread.php?t=2253722](http://ubuntuforums.org/showthread.php?t=2253722)  The 82598EB has two interfaces and I am able to receive data on both of them (let's say eth4 and eth5). I can see the RX packets: count increment in ifconfig, and I can verify in wireshark that data is being received on both of these interfaces. However, if I try to open a socket on one of the interfaces and receive data, say on eth4, I never see a byte until I ifdown the other interface (eth5 in this case). Here is the simple Python code I am executing:

```

import argparse
import socket

if __name__ == "__main__":
    parser = make_parser()
    args = parser.parse_args()
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    s.bind((args.addr, args.port))
    s.setblocking(0)
    s.setsockopt(socket.SOL_SOCKET, socket.SO_RCVBUF, args.size)
    data, address = s.recvfrom(4096)    

```

If I execute my script, s.recvfrom never returns until I ifdown the other interface. Then I get data as I expect and the script behaves normally. Why does bringing down the other 10GbE interface cause the socket to be able to receive data, where is the data being held up otherwise?

---

### Post by justin.henderson on 2015-04-08
I still have not resolved this issue. Any thoughts on how to further debug this are welcome.

---

