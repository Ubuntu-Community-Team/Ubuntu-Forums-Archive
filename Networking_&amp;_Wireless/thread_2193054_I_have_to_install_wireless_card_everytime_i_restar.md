---
title: "I have to install wireless card everytime i restart 12.04, how to solve this."
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by m_elsa160660 on 2013-12-11
hi
my wireless card is not supported by ubuntu yet, so i had to do a manual install with the terminal, after that its good, it works, but everytime i restart the machine i have to reinstall all over again.. what are the steps to make this automatically. 
 
  thanks.

---

### Post by mikewhatever on 2013-12-11
Can you reveal the wireless card make and model, as well as the terminal commands used to make it work. It would greatly benefit both yourself, and those willing to help. Thank you for cooperation.

---

### Post by varunendra on 2013-12-12
> **mikewhatever said:**
> Can you reveal the wireless card make and model, as well as the terminal commands used to make it work. It would greatly benefit both yourself, and those willing to help. Thank you for cooperation.

+1
We need details to be able to offer any kind of help.

To identify the card and its driver, please post back the output of this command (you may copy-paste it to avoid typo) -
```
lspci -nnk | grep -iA2 net
```

And like Mike asked, the terminal commands you use to make it work may be a great help in identifying the actual problem. :)

---

