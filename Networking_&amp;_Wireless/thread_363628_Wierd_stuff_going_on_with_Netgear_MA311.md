---
title: "Wierd stuff going on with Netgear MA311"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by ToiletPaper on 2007-02-17
I loaded Ubuntu Edgy a few days ago, and it seemed to work fine.  The Internet was running as it normally would.  But after I restarted my computer after it updated itself, my internet was down, I couldn't get into the Networking configurator, and I have absolutely no idea what to do.  I tried to reinstall it, but the same happened after restart.  Also, one of the help sites that there is MA311 support out of the box.

Have any suggestions?

---

### Post by ToiletPaper on 2007-02-17
Okay, I fixed it on my own.  Never mind.

---

### Post by Episcopus on 2007-03-04
I am having the same problem.  If anyone hanging around knows how to make it work, would you mind sharing?  This site: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) says that it should work out of the box, and it did until I downloaded a list of updates.  Now the device manager finds the hardware and recognizes it as a prism2.5 card made by netgear, but I don't have any wireless connections when I run iwconfig.

Would it help if I posted a dmesg, lsmod, or iwconfig result?

Thanks

---

### Post by koshari on 2007-04-22
you need to placklist the prism and hostapp drivers so it loads the orinco drivers for the 311.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989)

---

