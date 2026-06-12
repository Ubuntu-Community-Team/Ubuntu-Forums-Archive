---
title: "Hard locks when using parproute w/ wireless and VirtualBox"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Amorget on 2008-05-02
Host: Ububtu 7.10
Guest: Vista Business

Network card driver: iwl4965 (not 100% sure what exact network card that is, but it is an Intel card)

Here is the code I am running to get my tap0 interface

```
sysctl net.ipv4.ip_forward=1

X="$(VBoxTunctl -b -u amorget)"

echo "$X"

ip link set "${X}" up
ip addr add "${1}/${2}" dev "${X}"

parprouted "${3}" "${X}"
```

$X ends up being "tap0"
$1 = ip address to use
$2 = subnet mask
$3 = interface (wlan0 for me)

Basically I'll just be going along and either Vista will just hard lock or Ubuntu will hard lock.  I haven't found anything specific that triggers it, though I think "heavy" network usage in Vista can trigger it.

Any thoughts?

Douglas

---

### Post by Amorget on 2008-05-05
Help, please  :(

---

### Post by Amorget on 2008-05-07
Anyone?

---

