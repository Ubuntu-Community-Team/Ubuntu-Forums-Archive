---
title: "Wireless Internet to Laptop, Laptop Connection to Desktop"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by rizlmilk on 2007-12-11
I would first like to start by saying that I have read all of the suggested threads relating to my problem, and then some, but still have not solved my problem.

I am trying to use the wireless connection on my laptop (XP) to connect my desktop (ubuntu) to the internet.

This will save me from either dragging a long Ethernet cable throughout the house, or paying $40 for a cable modem.

So...Wireless >(Wireless Adapter)> Laptop >(Ethernet Cable)> Desktop

My main problem is the fact that I can't enable "internet connection sharing" in FireStarter. In the wizard, I try to enable it, but it gives me the message saying "The local Area and the Internet connected devices can not be the same". So what I am assuming is that I need to have one as Eth0 and the other as Eth1 (or something of that nature)...but there is only Eth0 to choose from in the drop down menus.

Any help or insight will be greatly appreciated.

---

### Post by kevdog on 2007-12-11
I think you need to create a network bridge and bridge your wireless and ethernet connections.  (or create a bridge and add your wired ethernet card and wireless card to the bridge).  Ive seen this done with two wired network cards, but cant see why it wouldnt work with a wireless/wired combination.

Try this thread:
[http://ubuntuforums.org/showthread.php?t=632062&highlight=bridge](http://ubuntuforums.org/showthread.php?t=632062&highlight=bridge)

---

### Post by rizlmilk on 2007-12-11
It turns out I just had to enable internet connection sharing on the windows laptop. Stupid oversight on my part. Thanks for the help though.

---

