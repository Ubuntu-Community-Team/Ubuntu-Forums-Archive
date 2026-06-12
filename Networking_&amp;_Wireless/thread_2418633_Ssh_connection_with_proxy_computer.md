---
title: "Ssh connection with proxy computer"
date: 2019-05-09
forum: Networking &amp; Wireless
---

### Post by jsjpandey on 2019-05-09
My main system is connected locally through lan with other computer where I place backup files, while my laptop and main are having connection with each other through wifi hotspot. I have various files to copy to and fro from one system to other (as and when needed) which is on backup computer. To reach to backup computer I have ssh to main computer and then to backup computer and then to the file I want which consumes lot of time. I want to directly reach to the backup computer from my laptop. I have attached the file to explain my scenario. Thank You

---

### Post by TheFu on 2019-05-09
I would redraw the diagram with the B listed as the network router with a WiFi-AP connected.
Wifi performance will always suffer when there are multiple hops because just those 2 devices will effectively cut the best possible throughput 50%. Add in the real-world aspects and wifi might only provide 5-10% of the bandwidth listed on the AP box.

Routing will be very important for an efficient setup and so does knowing where the internet connection is.  That is missing from the diagram.  Subnets for each connection would be helpful too.

---

### Post by jsjpandey on 2019-05-10
Computer A and Computer B is having internet connection from Tenda router which is connected with ISP wire while Computer C is in shared connection with computer B.

---

### Post by The Cog on 2019-05-10
I would use TCP forwarding to do this. Assuming computer B is 2.2.2.2 and C is 3.3.3.3:
On computer A, ssh to computer B but with forwarding on port A-12345 to C-22
ssh -L 127.0.0.1:12345:3.3.3.3:22 myname@2.2.2.2
then on computer A you can ssh to computer-C-username@127.0.0.1:12345 and you get passed through to computer C. You can use sftp in your file manager - enter this in the location:
sftp://computer-c-username@127.0..0.1:12345/home/computer-c-username

---

### Post by jsjpandey on 2019-05-10
I even tried that but from Computer C I can ssh to Computer A directly without any port forwarding not in other way.

---

### Post by TheFu on 2019-05-10
> **jsjpandey said:**
> I even tried that but from Computer C I can ssh to Computer A directly without any port forwarding not in other way.

So ... no routing tables will be provided?> 
Routing will be very important for an efficient setup and so does knowing where the internet connection is. That is missing from the diagram. Subnets for each connection would be helpful too.

---

### Post by The Cog on 2019-05-10
> **jsjpandey said:**
> I even tried that but from Computer C I can ssh to Computer A directly without any port forwarding not in other way.

In that case, routing must be correct, and I guess your issue is with firewall configuration, probably on computer C although it is conceivable that there may be odd forwarding rules on B. Or perhaps there is ome NAT going on somewhere.

---

### Post by jsjpandey on 2019-05-11
How to check firewall configuration and NAT configuration.

---

