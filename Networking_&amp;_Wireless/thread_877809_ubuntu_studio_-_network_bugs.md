---
title: "ubuntu studio - network bugs?"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by vk4ebp on 2008-08-02
I installed Ubuntu Studio 8.04.1, and configured my wireless interface with a static IP as the default network connection. 
Now whenever I attempt to configure my wired eth0 using network manager, I get a message "The Interface does not Exist, check that it is correctly typed and that it is correctly supported"
Previously, I installed it with the wired connection as the default, and after the installation was complete I was unable to configure the wireless!
Additionally, I configured my broad PCMCIA card to work as a modem. This dials out and connects, but no iternet traffic occurs until I enter:
sudo route add default pppo
I tried same for the eth0 interface, but no traffic occurs even though I can acquire an IP from my router after entering ifup eth0
Has anyone had a similar problem, and or has a solution?

---

