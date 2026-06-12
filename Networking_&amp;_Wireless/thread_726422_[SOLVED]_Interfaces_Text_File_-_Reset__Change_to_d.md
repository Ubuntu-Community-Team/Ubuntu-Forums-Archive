---
title: "[SOLVED] Interfaces Text File - Reset / Change to default"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-03-16
What is the default text for the interfaces file in /etc/network?
I changed mine to get my wireless network working but it is too unstable. I want to make the interfaces file back the way it was by default.

---

### Post by Rytron on 2008-03-21
Hi everyone,
I came across this:

```
sudo apt-get remove-purge network-manager net-tools
```

Then re-boot your system and re-install them again.

```
sudo apt-get install network-manager net-tools
```

---

### Post by astabeno on 2008-07-17
If you do this make sure you have the network-manager and net-tools packets locally on your system, because that will bring your networking down and apt-get will not be able to reinstall these files from the online repositories.

---

