---
title: "Wireless not working with AR5007 and Wicd"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Spartacus84 on 2008-05-02
I have a Compaq f756nr and I installed ndiswrapper and the correct drivers using the instructions here: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

I also installed wicd, but I can't get it to connect. 

When I try it without a static IP address, I get the message "Connected to <SSID> at 0 (IP: 192.168.X.X)".

When I try it with a static IP address, I get the message "Connected to <SSID> at 100 (IP: 192.168.X.X)".

However, neither of these configurations work. Am I supposed to be doing something with the DNS? Can anybody help me?

---

### Post by kiisu on 2008-05-02
I have the same setup. Have yuou tried going into the preferences of wicd? 

Make sure at the top where it says supplicant driver you have ndiswrapper selected, and make sure your wireless interface is named correctly. I think it should be the same as the logical name in lspci.

---

### Post by Spartacus84 on 2008-05-02
When I set it to ndiswrapper, it says "Connected to None at 0 (IP: 192.168.X.X)", and doesn't connect. That doesn't seem like an improvement.

---

### Post by Spartacus84 on 2008-05-02
Should I try another application other that wicd? If so, any suggestions?

---

