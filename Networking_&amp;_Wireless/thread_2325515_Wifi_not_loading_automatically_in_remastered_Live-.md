---
title: "Wifi not loading automatically in remastered Live-CD"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by johannes16 on 2016-05-23
Hi,

I want to create a LiveCD based on Ubuntu 14.04 for a project a my university. I ran into a strage issue: The wireless driver (iwlwifi) is not loaded automatically during boot time. However I can load it after startup using:

```
sudo modprobe iwlwifi
```

So far I have no idea what is causing this. The driver does not have to be in the initrd image, since it is loaded pretty late, correct? I also didn't modify the blacklists. Any idea/hint what can be causing this? Or some advice on where to look?

Thanks in advance!

---

