---
title: "network manager and vpn"
date: 2018-05-29
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-05-29
Is there is a way to make the network manager stop if its running with a vpn and the vpn stops?

Thank you..................

---

### Post by wildmanne39 on 2018-05-29
```
sudo systemctl start NetworkManager.service
```
will stop network manager from running and disconnect your computer from the internet in 16.04 and newer version of Ubuntu, I do not have a vpn installed at this time but I believe it will also disconnect your vpn.

Reference:

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by jgw on 2018-05-29
thanks for the reply.

I think I didn't say it right.  What I want is a way to run with a vpn all the time.  If the vpn fails then I want the network to shut down too.  Right now, for instance, if the network goes down then so does the vpn.   I want the reverse to be true too.

---

### Post by wildmanne39 on 2018-05-29
Okay, I will leave it to someone else to answer then, I did have a vpn installed for a time and mine did fail from time to time, I always received a message that it failed but my computer stayed connected to the internet as well.

---

### Post by crip720 on 2018-05-29
You are looking for a kill switch.  Wish I had paid more attention, but a few days ago this came up because someone could not find it on 18.04, when they had it working on 16.04.  It was a RSS feed of either 'ask ubuntu' or 'ubuntu forums'.  I am sure if you google 'network manager kill switch' you can find it.

---

### Post by jgw on 2018-05-29
thanks for the reply, I will do a search on that one tomorrow.

Now tomorrow.  I fixed the problem with this:[https://thedarkgod.wordpress.com/2014/09/05/adding-a-vpn-killswitch-to-networkmanager/](https://thedarkgod.wordpress.com/2014/09/05/adding-a-vpn-killswitch-to-networkmanager/)

If you google "vpn killswitch" you will get a lot of answers.  The one above seems to be the easiest.  The name of the file to create should be 99vpnkillswitch and not 99vpnkillswitch.iface.  I tested it and it worked GREAT.

Thanks for for the help and "kill switch" I would have never got this one done!

marking as solved

---

