---
title: "Kubuntu &amp; Ndiswrapper"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Otto-C on 2006-11-26
I was reading in the below website a discussion regarding
Ndiswrapper and updating. The discussion seems to center
around Fedora. My question is there a similar workaround
in Kubuntu. I very much want to do an update but not if
its going to break my current Ndiswrapper install.
uname -r 2.6.15-26-686

[www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Configuring_802.11g_with_Linux_Incompatible_NICs](www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Configuring_802.11g_with_Linux_Incompatible_NICs)


10. You will always need to have a ndiswrapper compatible kernel for the application to function correctly. To maintain your current kernel during yum updates, edit your /etc/yum.conf file to exclude the kernel from being kept up to date with the exclude option.
---------------------------------------------------
#
# File: /etc/yum.conf
#

exclude= kernel
----------------------------------------------------

tia
otto-c

---

