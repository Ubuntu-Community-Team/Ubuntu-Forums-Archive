---
title: "&quot;Connect to dsl-provider via modem&quot; on network manager disappeared"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by cokhavim on 2008-02-18
Hello,

When I was running Feisty, my NetworkManager had the option "Connect to dsl-provider via modem" in the menu, but now that I installed Gutsy, it disappeared.  How do I get it back?

Thanks.

---

### Post by SpaceTeddy on 2008-02-18
i am everything but sure about it, but i think it only shows when you have a vaild configuration in your /etc/ppp/peers directory... 

to create a configuration there, you will need to run *sudo pppoeconf* in a terminal and follow the onscreen instructions. if pppoeconf is not found, run *sudo apt-get get install pppoeconf* to install it. After that, network manager should (?!?) pick up the config... maybe :) mine does anyway

hope this blabber helps

---

### Post by cokhavim on 2008-02-18
Yup, that worked!

Thanks!

---

