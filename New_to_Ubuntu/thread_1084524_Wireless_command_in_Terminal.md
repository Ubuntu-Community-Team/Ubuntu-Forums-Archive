---
title: "Wireless command in Terminal"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Jareth on 2009-03-02
Hi,
I am trying to get my laptop to connect to a wireless network a little quicker. It does connect fine eventually but for some reason the network is no longer broadcasting its name so it doesn't connect as quick and I can't just click on a network name in the network manager.

I remember there being a way of renewing connections in windows by typing ipconfig /renew.
Is there anything similar I can type into the terminal to speed things along a bit.

Thanks very much

---

### Post by BbUiDgZ on 2009-03-02
> **Jareth said:**
> Hi,
I am trying to get my laptop to connect to a wireless network a little quicker. It does connect fine eventually but for some reason the network is no longer broadcasting its name so it doesn't connect as quick and I can't just click on a network name in the network manager.

I remember there being a way of renewing connections in windows by typing ipconfig /renew.
Is there anything similar I can type into the terminal to speed things along a bit.

Thanks very much

```
sudo /etc/init.d/networking restart 
```

---

