---
title: "2 NIC's and virtual servers"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by lollypork on 2006-10-19
Hello everybody! :)

I have a server with two network interfaces, eth0 and eth1, running ubuntu server with just sshd and vmware server ports open. I want to be able to have eth0 connected to my home network and eth1 connected directly to my ISP so that the ssh and vmware ports are only open to the home network side, but the virtual servers I choose can use eth1 as a bridge. Do I need to configure this on a per-program basis or can I make it global? Maybe a firewall is the best solution? I have never worked with firewalls on linux before, is anything recommended?

I have basic linux usage and am not afraid of a configuration that might take long, if it brings me were I want to be.

Thanks for any response in advance! :)

---

### Post by lollypork on 2006-10-19
It seems something similar has been posted before: [http://ubuntuforums.org/showthread.php?t=272788](http://ubuntuforums.org/showthread.php?t=272788)

I assume now that the way to go is with firewall rules. Although I don't know how firewalls behave when I use the beforementioned bridged networking, where the virtual host NIC's get their IP adresses from eth1.

The reason I want to try this is because I want a virtual host with 4 network interfaces to get external IP's (that is, from my ISP), because my bandwith is capped per IP, and with this approach I can quadruple my bandwith! :D

---

