---
title: "Network manager icon"
date: 2016-02-18
forum: Networking &amp; Wireless
---

### Post by sheldon7 on 2016-02-18
Hi,
I am new to Ubuntu.  Trying to find an icon for my network manager.  Would have thought it would automatically be on one of my menu bars, but not seeing it.  Is there a terminal command I can type in to place it there?
Sheldon

---

### Post by Hadaka on 2016-02-18
Hi sheldon7, are you missing your Network Manager icon or do you just want to know where it is??

The icon most often called network manager is the connection indicator next to the envelope and by the time display
in the upper right corner. It is not labeled "Network Manager" because..nothing is...it;s just called that.
you can also manage the network.Network Manager  from the menu icons on the left. click System settings
and then network. But it also is not labeled Network Manager, it is just refered to as that. alot like Nautilus.
welcome to Ubuntu !

---

### Post by sheldon7 on 2016-02-18
Hi, thanks for your response.  Yes, I seem to be missing the network icon.  There is nothing next to the envelope icon.  When I use the search function from the home page for 'network', I can get into the manager, but when I try to enter any info on one of the tabs, the screens are washed out and don't allow me to enter any information (e.g. IPv4, IPv6).  I'm trying to activate a VPN account and keep running into problems.

Thanks again!

---

### Post by Hadaka on 2016-02-18
please post the output of..
```
cat /etc/lsb-release
```
thanks

---

### Post by sheldon7 on 2016-02-19
DISTRIB_ID = Ubuntu
DISTRIB_Release=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

---

### Post by Hadaka on 2016-02-19
hi, please open a terminal and do..
```
**sudo service network-manager stop**
sudo apt-get install --reinstall network-manager network-manager-gnome
** sudo service network-manager start**
```
thanks.[INDENT]
[/INDENT]

---

