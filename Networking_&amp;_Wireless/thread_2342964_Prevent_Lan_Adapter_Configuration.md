---
title: "Prevent Lan Adapter Configuration"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by whitenoize on 2016-11-11
Hi everyone,

I'm relatively new to Ubuntu, and hoping someone could point me in the right direction here.

Long story short, I'm using Ubuntu 16 on a dedi and have set up VirtualBox and an Ubuntu 16 VM instance.
I have a /29 allocated to the dedi, and have used on of the IP's on the VM using a bridged configuration.

My goal is to allow a customer access into the VM ( OwnCloud server ) using teamviewer ( these are desktop versions ) however I'm looking for a way to disallow configuring the network adapter.
The VM has to remain on the public IP I assigned as if it were to change it would mess up my entire network.
I have tried disabling network manager, however it can be turned on quite effortlessly. The customer requires sudo privileges ( IT guy's request )

So ideally I would be able to feed the public IP to the VM using DHCP ( no idea how to do this, I tried ) and somehow not allow any other public IP to pass data through from VM to dedi.
Even more ideally, I could set the public on the VM, bridge config in VirtualBox but allow only traffic from that public IP.

Have been searching for this info for a couple of days, learned lots of new things and generally gained much respect for Ubuntu.
Any help or advise would be greatly appreciated.

Thanks and Regards
WhiteNoize

---

