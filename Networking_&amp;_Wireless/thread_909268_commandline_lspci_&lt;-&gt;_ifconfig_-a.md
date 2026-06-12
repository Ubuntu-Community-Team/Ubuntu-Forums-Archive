---
title: "commandline: lspci &lt;-&gt; ifconfig -a"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by ensis2k on 2008-09-03
How can I tell which device listed in lspci is connected to a given ethX via command line?

---

### Post by Ayuthia on 2008-09-03
> **ensis2k said:**
> How can I tell which device listed in lspci is connected to a given ethX via command line?

You can try lshw -C network.  It will give you the logical name (ethX).  In some cases the wired card does not show up because it is defined differently so you might have to just do lshw and look for it:
```
lshw|less
```

Hope that helps.

---

### Post by ensis2k on 2008-09-05
It works. Thank you verry much.

---

