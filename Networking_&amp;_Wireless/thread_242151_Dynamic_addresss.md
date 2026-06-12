---
title: "Dynamic addresss"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by aizen on 2006-08-23
Can anyone help me with changing to a client on a dynamic windows server? I'm 
in a network that needs the subnet address to be changed, my node is running ubuntu and it's the first time I ever used a linux based os so I am very new to it. Any help is greatly appreciated, thanks.

---

### Post by N6546R on 2006-08-23
If I understand correctly, you want your Ubuntu machine to det its IP address from a DHCP server.

From the Applications menu choose System Settings, then Network Settings. Click on the Administrator Mode button on the lower right portion of the screen and enter your password. 

Select your network interface from the list and click Configure Interface. Choose Automatic and DHCP, and click Ok.

Next time you boot the machine will pick up the new network information.

Perry

---

