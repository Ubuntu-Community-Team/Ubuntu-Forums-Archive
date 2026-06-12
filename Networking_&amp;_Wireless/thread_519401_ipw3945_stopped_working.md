---
title: "ipw3945 stopped working"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by shoofy on 2007-08-07
I've been using my ipw3945 relatively happily in Feisty (and previously on Edgy) on a Dell e1505 for about a year now. A couple weeks ago, it started dropping the connection after a few hours of being connected. After this happened a few times I decided to try installing the newer version of the ipw3945 driver, and I did so successfully, but it didn't solve the problem. I went back and reinstalled the linux-restricted-modules package, which I believe should have reinstalled the drivers that came with Feisty.

The problem got more and more frequent, until yesterday, when I could no longer reconnect at all. I've read tons of threads on this topic and nothing has helped. The card is seeing the AP and telling me the strength, but it fails to associate with it or get an IP address.

I have not yet tested to see if I can connect from booting into Windows (I haven't had to do that more months now and I'd prefer not to), so it's possible that it's a hardware issue. I guess it's also possible that it's a problem with the router (just the wifi part, I can connect with a wire). I'll try to test these tomorrow, but if anyone has any ideas for how to fix this off the top of your head I'd be glad to hear them.

---

### Post by Anakashar on 2007-08-07
I assure you it works in windows, as my laptop has Vista and Kubuntu 7.04, and in Vista it works just fine, but one day it worked in 7.04, the next day after a system update it simply stopped working.

I'm in the exact same situation you are.

---

### Post by shoofy on 2007-08-07
Do you remember which update it was? Maybe we can roll back.

---

### Post by Anakashar on 2007-08-07
It was a few weeks ago, but I think it was the one with the update from .15 to .16 in the (I think) kernel update.

---

### Post by shoofy on 2007-08-07
hmmmm... I don't remember a kernel update recently, but I'll check the logs when I get home. I always keep the previous kernel around, so I'll try booting to it and see if that solves it.

---

### Post by shoofy on 2007-08-07
I think that [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439) might be related, although it's listed as a bug just in Gutsy, not Feisty.

---

### Post by Anakashar on 2007-08-07
It looks related, yeah.  It seems to be the exact same thing happening on my side.  Using either KNetworkManager or wicd, I can see the APs, but it won't get an IP.  However, if I use a static IP, it says it's connected at 0% strength, so.. heh.

---

### Post by shoofy on 2007-08-07
This also looks related: [http://ubuntuforums.org/showthread.php?t=516192](http://ubuntuforums.org/showthread.php?t=516192)

---

### Post by shoofy on 2007-08-07
I installed wicd and removed NetworkManager and the wireless appears to be working now. I'll post an update if it stops working.

---

### Post by Anakashar on 2007-08-08
I've switched back and forth between wicd and KNetworkManager, and even just plain NetworkManager, but it still doesn't work for me.  I'm pretty much at a loss now, heh.

---

### Post by shoofy on 2007-08-08
Well Wicd just dropped the connection, but at least it came back and I was able to connect again after toggling the wireless kill switch. Not a good sign though.

---

