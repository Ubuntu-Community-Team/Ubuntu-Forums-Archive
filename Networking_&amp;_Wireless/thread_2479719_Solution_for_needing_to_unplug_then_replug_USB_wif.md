---
title: "Solution for needing to unplug then replug USB wifi adapter on boot."
date: 2022-10-04
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2022-10-04
I keep this device around just in case.

```
Bus 001 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
```

It was not enabling on boot. Required unplugging then plugging back in to enable.

Solution.

Find module loaded for it.

```
sudo lsmod | grep 8188

r8188eu               688128  0
```

Add first part to /etc/modules

```
echo "r8188eu" | sudo tee -a /etc/modules
```

Will now load on boot.

I'm hoping this solves something for a few, I thinking I can't be the only one to run into this type of thing.

---

### Post by &amp;KyT$0P# on 2022-10-04
> **Tadaen_Sylvermane said:**
> It was not enabling on boot. Required unplugging then plugging back in to enable.

... I thinking I can't be the only one to run into this type of thing.

You are indeed not the only one, there was another recent [thread]("https://ubuntuforums.org/showthread.php?t=2479602") describing the same symptom.

---

### Post by Tadaen_Sylvermane on 2022-10-04
Totally missed it. Thank you, my apologies.

---

