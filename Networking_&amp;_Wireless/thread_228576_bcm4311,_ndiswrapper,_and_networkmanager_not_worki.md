---
title: "bcm4311, ndiswrapper, and networkmanager not working"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by marcw on 2006-08-03
I've got a brand spanking new Compaq v5209us notebook that comes with the Broadcom 4311 wireless chipset per lspci.  It did not work after a fresh install of Dapper.

So using ethernet, I got connected with the default network-admin and network-monitor in order to get updated.  This worked fine.

Then I installed ndiswrapper using the various how-tos and wikis found here.  Likewise, I am able to connect wirelessly now also using the default network-admin and network-monitor.

Then I installed networkmanager.  I can't get it to work.  It starts fine after a reboot, sees all the available networks including mine, but when I attempt to get connected, it just sits and spins until it times out.  I've reset my AP to WEP, WPA, and no encrytion.  Same results with all - no connection, although with WEP and WPA it does ask the correct questions for passwords.

I don't *think* this is an ndiswrapper issue because like I said I can connect fine as long as I use network-admin and don't use network manager.

Any thoughts?  I'd *really* like to use NetworkManager...  Thanks!

---

