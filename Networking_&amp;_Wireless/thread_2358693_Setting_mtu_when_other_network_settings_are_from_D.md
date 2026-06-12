---
title: "Setting mtu when other network settings are from DHCP"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by David_Partridge on 2017-04-16
I want to set MTU of 7000 on my Realtek 9168SC network interface (eth0).

I can issue```
 ipconfig eth0 mtu 7000 
```and that works fine tho' I wish it would support 9000.

I edited /etc/network/interfaces so that it reads:

```
# The primary network interface
auto eth0
iface eth0 inet dhcp
mtu 7000
```

but that after a reboot the system reverts to an MTU of 1500.

How can I make this stick please. (I can't set this on the DHCP server as it's a fairly dumb VDSL hub).

Dave

---

### Post by TheFu on 2017-04-17
Which release of Ubuntu are you using?  The way networking is handled has changed between releases.
Is not using DHCP an option? That would mean using static settings, just make certain what you choose is correct and fits the subnet provided by the router.

BTW, the mtu 9000 issue is usually NOT due to any computer or computer driver issue. Rather it is due to something in your network - a switch/router/AP that didn't include the overhead in their MTU sizing.  Setting it to 8992 might work and if it doesn't, reducing it by 32 each time (8960 is next) will eventually find the largest value that works on your network.  However, some other protocols might have issues.  When I moved to jumbo frames, my NTP server started having issues. The Windows NTP clients stopped keeping anything close to correct time.

---

### Post by David_Partridge on 2017-04-22
I'm running 16.04.2 

I'd prefer to continue using DHCP, but am prepared to reconsider.

Dave

---

### Post by TheFu on 2017-04-22
You could put the /sbin/ifconfig command into a startup script that runs after the networking is up.  There are a few different ways to accomplish this.  rc.local is one.  post-up is another (inside the interfaces file).  

From the interfaces manpage:
```
       post-up command
              Run  command  after  bringing the interface up.  If this command
              fails then ifup aborts, refraining from marking the interface as
              configured  (even  though it has really been configured), prints
              an error message, and exits with status 0.   This  behavior  may
              change in the future.
```  
Just be certain to always use full paths. Also, the interface name may change to something funky, based on the NIC MAC.

---

