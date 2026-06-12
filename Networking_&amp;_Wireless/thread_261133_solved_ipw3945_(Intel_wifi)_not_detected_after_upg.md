---
title: "solved: ipw3945 (Intel wifi) not detected after upgrade to kernel 2.6.15-27-686"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by emparq on 2006-09-19
Don't know if anyone else ran into this problem, but I just ran into it today, and after some poking around, I arrived at my own solution..

_problem:_
  - ipw3945 (Intel 3945 802.11abg wireless adapter) not detected

_last known steps before problem occurred:_
  - from default Kubuntu 6.06.1 LTS installation, I upgraded my kernel to 2.6.15-27-686 via:
  ```
sudo aptitude install linux-image-2.6.15-27-686 linux-686-smp
```
  - rebooted
  - booted to the new kernel version 2.6.15-27-686

_symptoms:_
  - when opening 'wlanassistant' (Wireless Lan Manager), it reported not detecting any adapters
  - adapter was detected just fine in previous kernel version (2.6.15-23-386)

_my system:_
  - Thinkpad T60 2613-EAU ([specs]("http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2613eau&sitestyle=lenovo")) (Intel 3945 802.11abg wireless adapter)
  - distribution: Kubuntu 6.06.1 LTS
  - kernel version: 2.6.15-27-686 (upgraded from 2.6.15-23-386)

_solution:_
  - copy one of the 'ipw3945d-<old-kernel-version>' files to a correctly named version for your kernel via:
```
sudo cp /sbin/ipw3945d-2.6.15-26-386 /sbin/ipw3945d-$(uname -r)
```

_verification:_
  - reboot
  - booted to the new kernel version 2.6.15-27-686
  - 'wlanassistant' (Wireless Lan Manager) is now able to open and function as before

---

### Post by Matt0001 on 2006-09-19
I have the same problem with my Toshiba Satelite A85 and Atheros wireless. Wireless card is not detected with the upgraded kernel. As for now, I rebooted using the old kernel, I'm not sure if I'm knowledgable or confident enough to adapt your solution.

EDIT: And now I have found my solution from [this]("http://ubuntuforums.org/showthread.php?t=260842") thread. Restricted module did not update with the kernel. I installed the latest restricted module that matched the new kernel and problem is solved.

---

### Post by cosmolee on 2007-02-28
I had a similar problem, except that I was upgrading from 2.6.15-27-686 to 2.6.15-28-686.  Fortunately, I noticed the problem right after upgrading the kernel, so I was able to figure out the problem immediately.  I just use the old kernel.  

However, other folks may not be so lucky.  If one is doing a new installation, they may be frustrated to find that "linux doesn't work for them", because they can't get wifi to work, even though it should.

Thinkpad T22, Dlink DWL-G630 wifi card.

HTH.

---

