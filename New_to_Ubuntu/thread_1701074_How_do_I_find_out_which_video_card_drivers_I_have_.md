---
title: "How do I find out which video card drivers I have loaded"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-03-06
Whats driving my bus? Need to know which driver I have installed for my video card I'm running ubuntu 10.10 and my card is a NVIDIA 6600gt

---

### Post by mikewhatever on 2011-03-06
Are there any doubts that the nvidia driver is loaded and, say, not ATI? Anyway, you can verify that with the following command:
```
sudo lshw -C display | grep driver
```

---

### Post by fabricator4 on 2011-03-06
> **Jon Anderson said:**
> Whats driving my bus? Need to know which driver I have installed for my video card I'm running ubuntu 10.10 and my card is a NVIDIA 6600gt

Also:

```

lspci -v

```

---

