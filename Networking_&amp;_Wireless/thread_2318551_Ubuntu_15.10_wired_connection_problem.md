---
title: "Ubuntu 15.10 wired connection problem"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by johnny41 on 2016-03-27
Hello.
Just installed Ubuntu 15.10 and have problem with wired connection.  Wi-Fi seems to work fine, although it is a bit slow. 
If I plug in the  wire for wired connection it works for a few seconds, and then not only I  don't have the Internet, but all hosts that are connected to the same  router also don't have it.  
I know it is common problem, but I couldn't find definite solution to  this. 
I'm sorry if I haven't provided enough information, I'm totally new to this. If you need the output of some commands from terminal it is not problem - I just need to know the commands.
Please help :(

@Actually the connection is lost, when I'm starting to actually use Internet. If I plug the wire, and leave it for some time (won't do anything via the Internet on my computer) everything is fine on other hosts. When I'm starting using Internet, for example enter some website, the problem occurs.

---

### Post by praseodym on 2016-03-27
Hi, please run the wireless-script from the sticky-thread and show the outputs here.

---

### Post by johnny41 on 2016-03-27
Here it goes.
Thanks for helping.[ATTACH]268003[/ATTACH]

---

### Post by praseodym on 2016-03-27
Try deactivating the queue of the driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Also deactivate IPv6 in the network-manager profile

---

### Post by johnny41 on 2016-03-27
Done.
Didn't help :F

@Edit. Okay guys, don't bother. I'll just try other distribution, maybe it'll work. Thanks praseodym for trying.

---

### Post by johnny41 on 2016-03-28
Okay, for people who still wonder - it was (actually is) a problem with alx driver.
Setting MTU (I set it for 9000) parameter in the Network Manager seems to solve this problem (or at least I have constant Internet access).
I've found the answer on archlinux forum: [https://bbs.archlinux.org/viewtopic.php?id=201459](https://bbs.archlinux.org/viewtopic.php?id=201459)    
post #25.

---

