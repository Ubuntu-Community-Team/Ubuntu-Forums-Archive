---
title: "Network is not working on Ubuntu 10.10 (Maverick Meerkat)"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by skendaax3 on 2010-11-25
Hi, this is really important!! My network is not working on Ubuntu 10.10. I don't think this is a normal problem because the same thing was happening on 10.04. I installed Maverick Meerkat using Wubi for Windows. The icon to connect to the internet is shown with a red exclamation mark and when I click on the icon it says 'Wired Network: Disconnected'. How do I fix this problem!?!


Thanks

---

### Post by ptn107 on 2010-11-25
Pop open a terminal (Applications -> Accessories -> Terminal) and do both these commands:

```
sudo lshw -C network
lspci -v
```

post the output here.

---

### Post by vivek.pandey on 2010-12-04
> **skendaax3 said:**
> Hi, this is really important!! My network is not working on Ubuntu 10.10. I don't think this is a normal problem because the same thing was happening on 10.04. I installed Maverick Meerkat using Wubi for Windows. The icon to connect to the internet is shown with a red exclamation mark and when I click on the icon it says 'Wired Network: Disconnected'. How do I fix this problem!?!


Thanks
try this right click on network manager on right corner of ur screen...check whether network method u r using is enabled or not if not left click n then try to connect again

---

### Post by Spyderkid on 2010-12-04
run    lsusb    and post the outputs

---

