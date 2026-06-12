---
title: "Ubuntu 6.06 and losing Netowrk Connection"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by mikekie on 2007-06-04
Hi all,

I have a Dell PE 6650 (with dual Broadcom NICs) that I installed Ubuntu 6.06 with the intent to install free Vmware Server (just a test / fool around box).

All was working fine then the network connection just drops.   I checked with IT staff and the ports are active even though I cannot connect.    

I have tried static and auto IPs and the network connection just drops.  

Server network connections were fine with no loss when running VMware ESX 2.5 on this box.

Any known issues with losing network connection and Ubuntu?  Could it be a driver issue or bug (I have seen some posts on Network Manager being flaky at times).

Any help would be much appreciated. Thanks,Mike

---

### Post by loserboy on 2007-06-04
this may not be very helpful, but with dapper I would sometimes get random drops.  It hasn't happened since I moved to edgy and feisty, but I never found out why it happened.  for what its worth they werent broadcoms though.

---

### Post by DarkGob on 2007-06-04
I've been having the same problem with Feisty from day 1 (which to be fair, was less than a week ago), and I still have no clue why.

---

### Post by mikekie on 2007-06-05
I dug alittle deeper and it looks like a Netowrk Manager issue.  I updated to the latest version of Netowrk Manager and connection still drops off.

Anyone know if you can remove Network Manager and if you can what is the best procedure to do so?

Thanks!

---

