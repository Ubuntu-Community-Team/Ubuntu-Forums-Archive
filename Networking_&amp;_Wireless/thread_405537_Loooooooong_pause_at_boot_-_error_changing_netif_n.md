---
title: "Loooooooong pause at boot - error changing netif name"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by brandon moore on 2007-04-09
I hope I'm posting in the correct category...

On boot, I have a long pause (1-2 minutes). When I watch the boot process with recovery mode, I can see that this pause takes place along with an output that reads as follows:

> error changing netif name wlan0 to eth0

I am running Feisty 64-bit with a Broadcom 4318 wireless card.

---

### Post by ahaurw01 on 2007-04-10
I have this long pause as well. I haven't checked out recovery mode yet, but I assumed it was some setup of my 4318 broadcom card timing out as I have yet to get it to work on my newly installed feisty. (It worked fine on dapper after some pain.) Does your wireless card work for you? I've been following different suggests on the forums, but no avail yet. I've gotten as far as actually connecting to a wireless network that should be near perfect reception and then getting kicked off after 30 secs and the wireless card failing to detect any more networks after that. 
How have your experiences been?
aaron

---

### Post by brandon moore on 2007-04-10
> **ahaurw01 said:**
> I have this long pause as well. I haven't checked out recovery mode yet, but I assumed it was some setup of my 4318 broadcom card timing out as I have yet to get it to work on my newly installed feisty. (It worked fine on dapper after some pain.) Does your wireless card work for you? I've been following different suggests on the forums, but no avail yet. I've gotten as far as actually connecting to a wireless network that should be near perfect reception and then getting kicked off after 30 secs and the wireless card failing to detect any more networks after that. 
How have your experiences been?
aaron

The wireless card works flawlessly out of the box in Feisty, which surprised me. I've kept up with every update that has come out and I have genuinely expected it to quit at some point along the way, but it has continued to connect without any problems under network-manager. I previously used wifi-radar on Mepis for this card and wifi-radar on previous releases of Ubuntu because it was the only one that worked. Feisty really impresses me, more so than any other release or distro. All that to say, yes, the Broadcom 4318 card works great on my Gateway MX6424.

For you, I might suggest posting the output from this command:

> ndiswrapper -l

and checking this forum: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by ahaurw01 on 2007-04-11
I ended up reinstalling feisty last night. The wireless did not work right away, but I installed compwiz's deb package for feisty from the link you gave me. It worked right away even though thats exactly the first step I took last time I installed. Also, I dont' seem to have the same pause on booting that you described. although now the network manager icon in the notification area shows like the network is disconnected although i'm online wired. doesn't affect anything, although i hope its not a sign of a more significant underlying problem. thanks for the tips

---

