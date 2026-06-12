---
title: "Wired internet stopped working... vmware with XP internet works fine???"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by johndavid400 on 2007-10-21
Ok, I have had problems before with my wired ethernet cards needing to be replaced or drivers re-installed, but nothing like this.

I have an upgraded install of Gutsy 7.10 from a Feisty install several months ago. Everything has always worked just fine. Yesterday I installed a VMWare virtual machine with Windows XP and everything continued to work fine all day yesterday and this morning while running both Gutsy and the virtual machine running XP. I normally set up VMware to use NAT or the shared internet connection, But I thought it might be fun to try to give the virtual XP it's own IP address, so I did, and like I said it all worked just dandy.

But I shut down my computer a few minutes hours ago, now when booting back up, I have no internet in Gutsy. All other devices on my network have internet, including the virtual machine running inside of Gutsy! But Gutsy itself cannot connect.

I tried checking the network connections and it had defaulted my network device to "loopback interface" instead of "ethernet". I tried changing it to eth0 and it defaults it back to loopback.

I have rebooted twice, and am posting on my Gutsy machine using the connection on the VMWare virtual XP that I have running, so I know it is not my ethernet card.


Any ideas on how to get my ubuntu internet connection back??

thanks in advance

---

### Post by stevoo on 2007-10-21
it could be an IP conflict. 

Try and see what ip does vmware gets.

See if Gutsy gets an ip. 

if not try and force gutsy an ip different than the vmware.
Or try and disable vmware , restart and see

Just a thought

---

