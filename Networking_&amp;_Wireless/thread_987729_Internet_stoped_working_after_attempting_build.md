---
title: "Internet stoped working after attempting build"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by hithisishal on 2008-11-19
I followed the instructions here, in Ubuntu 8.04, to build openwrt kamikaze (wireless router firmware): [http://mightyohm.com/blog/2008/11/build](http://mightyohm.com/blog/2008/11/build) &#8230; g-openwrt/

under "the hard way":
Basically, I checked out kamikaze, updated everything, ran make prereq, make menu config, then make world.  make world took a long time, then ended with an  error. Running make world v=99 showed that the error was every connection to mirrors of ftp.gcc.org timed out.

But more importantly, the internet no longer works under ubuntu.  I can get it to work for a couple of seconds if I go to network...wired device...obtain IP address from DHCP.  The "use roaming" box was checked when I first went there.  After a couple of seconds, all attempts to connect time out.  I can get it to work for another ~15 seconds by checking use roaming, and unchecking it.  I have rebooted my computer a couple of times.

Everything still works fine under windows (Dual boot). 

Any ideas?

thanks!

---

### Post by hithisishal on 2008-11-20
Bump: still not working.

I tried releaseing my IP address from windows- didn't help.

I also tried assigning a static IP address - no luck.  I get about 15 seconds of internet when switching between roaming and DHCP modes, 

running ifconfig, I see the same (valid) IP address when it is both working and not working.  The outputs seem to be the same when it is both working and not working.

traceroute doesn't go anywhere when it is not working.  I get different messages when trying to ping my gatway (I think it's my gateway.  It's the .0 address) when it is working vs. not working.

any ideas?

Thanks!

---

