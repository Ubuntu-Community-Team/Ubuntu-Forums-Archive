---
title: "Unknown connections listed"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by tigerjack89 on 2016-10-16
I have two connections in the network manager named respectively "ASUS_Z00AD Network" and "Nokia 113 Network", both listed as Disconnected. They seem to be some kind of wired connection, but I don't know neither of them. 
I mean, I surely have an Asus phone which I sometimes connect to the laptop in order to charge it, but I don't have any Nokia.  
I've tried many times to delete the corresponding files from the /etc/NetworkManager/system-connections directory, but they continue to reappear without any specific reason.  

What are these connections? Is there a way to know which process created these files? Can they pose a security risk even if they appear as disconnected?

---

### Post by tigerjack89 on 2016-10-16
Ok, problem solved. 
  The problem is related to old Bluetooth devices paired with my  laptop. For some of these devices, I checked the "Use your mobile phone  as a Network device" flag. Unchecking them or simply removing the paired  device did the trick.

---

