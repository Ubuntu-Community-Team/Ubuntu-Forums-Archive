---
title: "Ndiswrapper must be reconfigured on startup?"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by JeffoOfMetal on 2008-04-06
Hello. I'm setting up a computer that has to use ndiswrapper with a wireless device. It all works fine and dandy, except that on startup, I have to reinstall the driver. Is there a script to do this automatically and can someone please supply me with it? I would greatly appreciate it!

---

### Post by JeffoOfMetal on 2008-04-06
Please, can anyone help?

---

### Post by kevdog on 2008-04-07
#1 - Use the search in the forums to find an answer to this question since its been asked a million times


#2 - echo ndiswrapper | sudo tee -a /etc/modules

---

