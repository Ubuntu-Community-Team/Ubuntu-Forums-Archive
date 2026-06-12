---
title: "VPN work only with the terminal active?"
date: 2020-06-30
forum: Networking &amp; Wireless
---

### Post by tackskull on 2020-06-30
Hi there,

I just bought a 2  years license of Surfshark VPN. To run this VPN it requires to run commands on the terminal, and once I did it the terminal say my new IP address. In the case I turn off my computer, in the moment *I turn it on again, the VPN is still working or should I run the command again? * Same, If I turn off the terminal, the VPN is still on?

Thanks everybody

---

### Post by The Cog on 2020-06-30
I am pretty sure that if you restart the PC then the VPN will no longer be running, and you will have to run the command again to restart the VPN. The two commands 
```
ip address
ip route
```(in a different command window) will show you your current IP addresses, and where your default route (to the internet) is pointing to. It would be worth your using those two commands both before and after starting the VPN so you can see what the dirrenence is. I expect that starting the VPN will create a new interface and that your default route will be using that interface.

As to whether the VPN stops when you close the terminal, probably not, but I'm not sure. Use those two commands again to see if things change back when you close the terminal you ran the VPN command in.

---

