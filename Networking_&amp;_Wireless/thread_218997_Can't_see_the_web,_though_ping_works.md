---
title: "Can't see the web, though ping works"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by ToreUs on 2006-07-19
After finally getting my wireless card to work, I suddenly can't get any web pages to come up in Firefox under Dapper Drake. I can ping all the addresses I want to, but the web pages never come up. The only think I did was to install the VMWare Player and bring up a saved Windows XP guest, which booted just fine but never could see the network either. I don't remember making any changes to networking configuration on the Dapper host, just on the XP guest. So I'd appreciate any help I can get...

I'm currently experimenting with Ubuntu on a dual boot machine (a Dell Latitude D600 with a 1350 wireless card (Broadcom 4206). My intent eventually is to wipe the hard drive and reinstall Ubuntu as the primary OS with XP either on a small partition for dual boot or as a guest under VMWare (I'm thinking dual-boot right now). I just need all my "ducks in a row" first as being able to use this machine for Internet and writing is critical.

---

### Post by x64Jimbo on 2006-07-19
Interesting. VMWare installs some virtual network interfaces... I wonder if your computer is now trying to use its direct connection to the guest OS for its internet connection. 
I'd recommend looking through this how-to and see if you did anything differently:
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

