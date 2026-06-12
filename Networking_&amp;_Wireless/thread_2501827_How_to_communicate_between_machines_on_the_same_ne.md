---
title: "How to communicate between machines on the same network?"
date: 2024-10-22
forum: Networking &amp; Wireless
---

### Post by betawolff on 2024-10-22
I have a machine A running apache server and I want to access the server from another machine B connected to the same router. The machine A has a public ip of 192.168.204.59 while the machine B has a public ip of 192.168.1.2 indicating that they're on different subnets. The machine A is connected to my phone and is accessing internet via usb tethering. The phone is on the same wifi as the machine B. When I run **ip a** in machine A, the network interface doesn't have any IP address and it's status is down.

---

### Post by ian-weisser on 2024-10-22
192.168.*.* addresses are, by definition, private. Not public. You cannot access them from the internet. You can only access them from the local side of your router.

Login to your router and put both devices on the same subnet.

If your phone is acting as a router (USB tethering), then B might still be unable to connect to A, as there might still be a router between them.

---

### Post by betawolff on 2024-10-22
Thanks for explaining!

---

