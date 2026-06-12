---
title: "[HowTO] Network Manager with static"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by ATIR350 on 2007-06-17
I use a static ip and network manager refuses to detect that connection
Asked some classmates and they suggested that I 'downgrade' to network manager 0.6.4-6ubuntu4

And that worked like a charm! Now I use my VPN connection through network manager with no hassle

here I post the deb packages, since they can be quite difficult to find
[Network manager gnome]("http://learn.tsinghua.edu.cn:8080/2005011143/network-manager/network-manager-gnome_0.6.4-6ubuntu4_i386.deb")
[Network manager]("http://learn.tsinghua.edu.cn:8080/2005011143/network-manager/network-manager_0.6.4-6ubuntu4_i386.deb")

[libnm-glib]("http://learn.tsinghua.edu.cn:8080/2005011143/network-manager/libnm-glib0_0.6.4-6ubuntu4_i386.deb")
[libnm-util]("http://learn.tsinghua.edu.cn:8080/2005011143/network-manager/libnm-util0_0.6.4-6ubuntu4_i386.deb")

Open synaptics and uninstall network manager and network manager gnome
then in terminal do a  
'sudo dpkg -i' on the first two files

I provide two dependencies just in case

Enjoy!:popcorn:

---

