---
title: "No Network Link"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Duck Man on 2007-09-06
I am normally a Gentoo user but the kde4 beta2 came out and I wanted to try it out. I could use a live cd and junk but I wanted to do a full install so I could really mess with it. Gentoo takes too much work to do some messing around with unstable stuff so I went to Kubuntu because I love you guys and KDE. :-P SO to the problem.

The install went ok... It got stuck some place and I ended up rebooting and it was installed... I only say this because this might be the problem. :-P The actual problem showed up in the livecd as well. No network! NetworkManager is there and KNetworkManager is there. It says its disconnected and on further inspection it sees eth0. Open a terminal and do a ifconfig and eth0 is there along with a eth0:avah and lo of curse. eth0:avah has an ip and all the info it looks like it should. So its getting an ip from someplace. Now here is the odd part. The link light on my switch is off and so is the one in the back of the comp. When I log into window on the same machine every thing works fine. Any ideas?

Here is relevent lspci:
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

---

### Post by Duck Man on 2007-09-07
I got the idea to search for "link light" on the forums and found this towards the top: [http://ubuntuforums.org/showthread.php?t=538448&highlight=link+light](http://ubuntuforums.org/showthread.php?t=538448&highlight=link+light)

IT WORKED!!!

---

