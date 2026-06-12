---
title: "It is necessary to install ifenslave package on Ubuntu 18.04"
date: 2020-04-24
forum: Networking &amp; Wireless
---

### Post by abdulsamad2 on 2020-04-24
[h=2]**Hello everyone,**[/h][COLOR=#000000][INDENT][B]
I installed Ubuntu server 18.04. I configured Bond0 with Vlans during the installation. My question is that it is required to install the ifenslave package after the installation? Up till now I have not installed this package but my its working fine. so, there is no package then which module managing that configuration? and then why we need this package?

I need little urgent help. Thank you so much.


Regards,
Abdul Samad[/B][/INDENT]
[/COLOR]

---

### Post by dino99 on 2020-04-24
Do you work with 'external' slave network (on cloud for example) ? if so this tool deals with attach/detach these networks.
Note that the kernel must have support for bonding devices for ifenslave to be useful.

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) (no recent update)
[https://www.tecmint.com/configure-network-bonding-teaming-in-ubuntu/](https://www.tecmint.com/configure-network-bonding-teaming-in-ubuntu/)
[http://manpages.ubuntu.com/manpages/focal/man8/ifenslave.8.html](http://manpages.ubuntu.com/manpages/focal/man8/ifenslave.8.html)
[https://www.snel.com/support/how-to-set-up-lacp-bonding-on-ubuntu-18-04-with-netplan/](https://www.snel.com/support/how-to-set-up-lacp-bonding-on-ubuntu-18-04-with-netplan/)

---

