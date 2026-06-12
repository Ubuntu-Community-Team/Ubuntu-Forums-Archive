---
title: "Belking F5D7010xx Installation (Completely New)"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Mr.Chris on 2007-05-07
I just installed Ubuntu, and am having great difficulty installing the card specified above. 

Any support on this would be so, so helpful.

---

### Post by chili555 on 2007-05-08
Welcome to the party, Mr. Chris!

These came in at least three different versions, some very easy to install, some, not so much. However, none of them are impossible to install with determination. The first step is to find out which we are working with. Make sure it's in the slot and open a terminal and type:```
sudo lshw -C network
```Give your password and a lot of text will appear. One section will refer to your ethernet card and one to the wireless. The wireless section will refer to the chipset your card uses. It may even tell you the driver it expects to use.

If you are intrepid, you can look here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)  for guidance as to how to proceed. If you need a sherpa, post the result here and we'll help you.

---

