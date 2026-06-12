---
title: "Qualcomm Atheros pci card - 90-98% package loss, on some networks - Ubuntu 16.04.5"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by ohls on 2019-02-04
When I'm on my home network, the connection never drops. On other networks I get intermittent connectivity, it's almost constantly down though. If I ping 1.1 for example, I usually get 90-98% package loss. Sometimes it might work for 3-4 minutes just fine, and then it starts dropping packages again. I used to run Ubuntu 14, and I had this same problem, on the same networks. Then I would usually get 20-30 minutes of good connectivity before having to wait 5-10 minutes. Upgrading only seems to have exacerbated the problem.

Here's a pastebin of some specs: [https://pastebin.com/dVL21ZD5](https://pastebin.com/dVL21ZD5)

Anyone got a clue on whats going on here? If there's anything more I can provide to help find a solution, please ask. Thanks in advance!

Also, if there's no one able to answer this, is there any USB device that is guaranteed to work on Ubuntu 16?

---

### Post by jeremy31 on 2019-02-05
See if ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
And a reboot helps, that command should keep network manager from enabling wifi power management

---

### Post by ohls on 2019-02-05
Doesn't make any difference. Thanks for the suggestion!

---

