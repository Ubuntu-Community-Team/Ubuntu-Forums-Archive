---
title: "Ubuntu 24.04 LTS | Internet works fine |  Connection Failed popup window recurs"
date: 2024-08-28
forum: Networking &amp; Wireless
---

### Post by arkie76 on 2024-08-28
Noob here. Running a amd wrx90 sage motherboard, ubuntu 24.04 . Three ethernet ports on back. 2 are intel 10 gb . Both work. No packet lost while pinging during connection failed popup. The third is from realtek and is for a ipmi controller. According to internet, none of these need additional drivers. However the popup occurs 4 to 8 times an hour, without identifiable degradation. How do I begin troubleshooting?[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294153&stc=1[/IMG]

---

### Post by arkie76 on 2024-08-28
Running nmcli monitor, I will see populate repeatedly:
enxfef590e94f2c: using connection 'netplan-enxfef590e94f2c'
enxfef590e94f2c: connecting (prepare)
enxfef590e94f2c: connecting (configuring)
enxfef590e94f2c: connecting (getting IP configuration)
enxfef590e94f2c: connection failed
enxfef590e94f2c: disconnected.

I think this is the ipmi / realtek lan module.  Is there a way to stop the automatic polling of this?

---

### Post by currentshaft on 2024-08-28
Settings > Privacy & Security > Connectivity

---

### Post by arkie76 on 2024-08-29
Thanks for the reply currentshaft! Turned it off, rebooted, and problem continues.

---

### Post by currentshaft on 2024-08-29
Are you using DHCP or a static IP?

---

### Post by arkie76 on 2024-08-29
Dynamic

---

