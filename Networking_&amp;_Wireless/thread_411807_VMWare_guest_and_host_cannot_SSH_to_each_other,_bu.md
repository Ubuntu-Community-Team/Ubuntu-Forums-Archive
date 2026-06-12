---
title: "VMWare guest and host cannot SSH to each other, but can to other IPs on the network"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by lefty.crupps on 2007-04-17
**This post could be related to an Ubuntu bug filed at**: [http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am running Feisty and have a virtual machine of Etch running in VMWare.

I can SSH from either onto other machines on the network, or from the other machines to either my host or my guest; I can ping between my guest and my host.  But I cannot SSH from the guest to the host, nor the host to the guest.

My setup on the host followed HowToForge's Perfect Setup of Etch:
  [http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch)
with some image creation hints and tips from Forever For Now:
  [http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php](http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php)

Can anyone help me here?

---

### Post by milton1 on 2007-04-17
have you tried ssh from one to a remote comp, then ssh again back to the other local option? It could be something silly like your comp refusing to accept connections from its own ip. check iptables; maybe you are blocked from yourself.

---

### Post by lefty.crupps on 2007-04-17
Yes, I can SSH from guest to another then to host, or the other way...

I don't have IPTables set up, unless its a default thing now in Feisty.  I am able to SSH to myself via 'ssh 10.10.10.173' and I can get in...

---

