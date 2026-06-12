---
title: "Clean install from 9.04 to 10.10 wifi now drops frequently"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by agm. on 2010-12-21
Hi,

I had been using 9.04 but since it stopped being supported, I decided to do a clean install of 10.10.  I first used the live CD and things looked good and it auto-connected to my WPA2 encrypted security wireless network.  I thought things were great and went ahead and installed.

The problem is that now in 10.10, wireless connects upon a restart, stays connected from between 2-6 minutes and then gets dropped.  It then has a very hard time reconnecting once it is dropped, asking several times for the password trying to connect but failing.

I am using a USB Linksys Wireless N dongle that worked quite well under 9.04.  Any recommendations to fix this problem?

From lsusb:
```

Bus 001 Device 003: ID 1737:0071 Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter

``` 

After updating via cord, I am running kernel 2.6.35-generic and the Linksys drivers look good.  I've tried looking through several how-to's and other forum posts, but couldn't see anyone who had encountered (or solved) this problem in 10.10.

I appreciate the help!  Please let me know if there is more information that you need to try and help me troubleshoot this problem!

---

### Post by smuthavarapu on 2010-12-21
Do you use any wireless mouse/keyboard ?

Try modifying the Channel number by logging in to your Router as Admin. 

Use Wired Connection to do the setup of Router

---

### Post by agm. on 2010-12-21
I use a wireless mouse, but used it when I had 9.04 as well.  I'll try to dig up an old wired mouse and see if that fixes the problem before I manually adjust frequencies within the router...

I just wonder if it isn't possibly something else since the mouse and dongle worked well together in 9.04?

---

