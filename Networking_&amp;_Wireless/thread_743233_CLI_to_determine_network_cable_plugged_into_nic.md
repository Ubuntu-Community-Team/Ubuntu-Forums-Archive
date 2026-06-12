---
title: "CLI to determine network cable plugged into nic"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Contrarian on 2008-04-02
Is there a way from the command line to determine if a network cable is plugged into a NIC?  I have multiple NICs on a system, but not sure which is actually receiving data from the live connection.

---

### Post by prshah on 2008-04-02
> **Contrarian said:**
> Is there a way from the command line to determine if a network cable is plugged into a NIC?  I have multiple NICs on a system, but not sure which is actually receiving data from the live connection.

```
sudo mii-tool
man mii-tool
```

Unfortunately does not work without sudo.

---

