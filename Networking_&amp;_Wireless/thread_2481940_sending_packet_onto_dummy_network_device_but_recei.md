---
title: "sending packet onto dummy network device but receiving echo"
date: 2022-12-14
forum: Networking &amp; Wireless
---

### Post by othernamen on 2022-12-14
Hello,

I create network device "ip link add mydevice type dummy" and send/receive traffic on this device using some python scripts.

But I receive my own sent packet on this device (python code below). If I bind to some other physical network card, there is no echo if I send a packet (I do not receive my own packet).

Is there other basic simple network device which would not do that? veth is not suitable for me as it creates a pair of network devices.

Many thanks!
I

[1] python code to receive message:
rs.bind(("mydevice", ETH_P_ALL))
buffer=rs.recvfrom(BUFFER_SIZE)[0].hex()

---

### Post by othernamen on 2022-12-14
Just to note, that there is no echo when doing a tcpdump, so must be maybe a way to get rid of this echo, but might post it in python programming forum then..

---

### Post by othernamen on 2022-12-16
This was the problem that I was creating a separate socket for receiving and transmitting onto the device. But when creating single socket. problem solved.

---

