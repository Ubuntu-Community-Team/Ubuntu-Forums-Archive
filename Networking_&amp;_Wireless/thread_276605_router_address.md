---
title: "router address"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by kievking on 2006-10-13
I have an extremely generic router with no documentation. How do I get the router address so I can configure it. I think I only need to change the WAN address so it works with Comcast. I tried to access the router by typing 192.168.1.254 in firefox, but no luck. I also tried 192.168.1.0, etc.

---

### Post by wieman01 on 2006-10-13
A few more options (most common once):

1. 192.168.0.1
2. 192.168.1.1
3. 192.168.1.2

---

### Post by kievking on 2006-10-13
Thanks. Tried those without any luck. Does the address appear in IPv6?

---

### Post by spd106 on 2006-10-13
A few more to try

192.168.2.1
192.168.10.1
10.0.0.1

Maybe try a link-local
169.254.1.0 - 169.254.254.255

If it's running dhcp then it should be on the same network as your clients. Then there's always a broadcast ping, [b]ping -b 255.255.255.255
[/b], just be careful you don't cause any storms.

---

### Post by kievking on 2006-10-13
Thanks, but still no luck. When I tried ping -b, I received a warning about using that command, but it didn't show a router address and the terminal just hung for 2 minutes. If I turn off the entire system and reboot, the comcast cable modem detects the router, works for about 3 minutes and then the modem and router shut down. I read that the mac address of the router must be changed in order for the router to work properly with the comcast modem. The 
experienced tech at the local computer shop said to exchange the router for a new one ??? . I think the model number is "Netcell INET Share 104" according to the label on the back of the router.

---

### Post by wieman01 on 2006-10-13
The thing with the MAC address is true. Let's worry about that later on. Your problem is that you don't know your router's IP address so that you cannot configure it, correct?

Assuming that you have DHCP enabled type this command and post the output:
> route

---

### Post by kievking on 2006-10-14
OK..my router address is 192.168.1.254. I was able to connect to the configuration page, but I was unable to change the mac address.


I attached a screen shot. I clicked "ADD" and it didn't bring up the
option to change the mac address. I'm also not sure about the other settings.
Thanks

---

### Post by wieman01 on 2006-10-14
You can change the router's MAC address by using the "CLONE" function. Do you have something like that?

---

### Post by kievking on 2006-10-16
Thanks for your help. I'm temporarily disconnecting one computer from the modem and then connecting the other one to the modem. When I get motivated again I'll try to solve the problem with the router.

---

