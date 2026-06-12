---
title: "How to permanently save my iptables configurations"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by legendary on 2007-03-27
Hello,

I'm having trouble saving my iptables configuration permanently so that it will be retain even after reboot. Does anybody can help me find the configuration files of iptables so that i may edit it directly?

I'm just a newbie in Ubuntu and I will need all the help I can get.

---

### Post by hde on 2007-03-27
> **legendary said:**
> 
I'm having trouble saving my iptables configuration permanently so that it will be retain even after reboot. Does anybody can help me find the configuration files of iptables so that i may edit it directly?


How did you configure your iptables? As far as I know there are many frontends to configure iptables. System wide configuration files are stored in /etc often in a directory with the name of the program.

If you have a iptables script, which can just be a bash script, with the firewall rules you want, you can start it automatically by adding an "up" line in /etc/network/interfaces

like this:

auto eth0
iface eth0 inet dhcp
up   /path/to/your/script.sh

it will then run your script everytime the network interface comes up

(this may not work with network-manager)

---

