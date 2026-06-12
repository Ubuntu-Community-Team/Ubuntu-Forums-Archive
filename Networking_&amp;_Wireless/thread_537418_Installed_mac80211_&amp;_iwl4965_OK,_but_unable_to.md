---
title: "Installed mac80211 &amp; iwl4965 OK, but unable to detect networks"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by fd9_ on 2007-08-28
I've installed the mac80211 and iwl4965 modules using the guide posted here ( [http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965) ) and I'm running the 2.6.22 kernel. The installation went OK, but NetworkManager isn't detecting any networks. Also,

```

modprobe mac80211
modprobe iwl4965
```

Returns without any errors. That means they're installed, correct? Is there anything else I can check to make sure I didn't miss something? By the way, I'm also using Lenny, but I don't think that should have any bearing on this. I'm using the mac80211-8.0.2 and iwlwifi-0.0.34, which I know for a fact work in Feisty.

---

### Post by fd9_ on 2007-08-29
Is there anything I can check to make sure I've installed the mac80211 & iwl4965 modules correctly?

---

### Post by Zorael on 2007-08-29
```
lshw -C network
```

Does the output from that suggest the interface is assigned the iwl4965 driver, or is it in one of those "UNCLAIMED" states?

---

### Post by fd9_ on 2007-08-29
> **Zorael said:**
> ```
lshw -C network
```

Does the output from that suggest the interface is assigned the iwl4965 driver, or is it in one of those "UNCLAIMED" states?

It says that my Network controller is "unclaimed".

---

