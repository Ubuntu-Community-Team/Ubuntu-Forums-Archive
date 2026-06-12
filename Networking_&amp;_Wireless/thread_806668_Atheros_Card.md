---
title: "Atheros Card"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by vernezane on 2008-05-25
Anyone have a fix to allow my HP Pavilion M7585a with an Atheros 5413 card to connect with wireless. I cant find any drivers or projects that support this card. The Atheros webpage says there is a project which they share the information with the linux community but i dont know the whereabouts of any information or projects. 

If anyone knows anything please let me know in this thread. Thanks.

---

### Post by chili555 on 2008-05-25
Your card is supposed to be supported in the madwifi project. In Ubuntu, it's included in:```
sudo apt-get install linux-restricted-modules-`uname -r`
```The `uname -r` bit is just a way to tell apt-get, 'please match my running kernel.'

Having said this, there are bugs filed here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/222865](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/222865) and here: [http://madwifi.org/ticket/1912](http://madwifi.org/ticket/1912)

I do notice, in the second bug:> try to install the madwifi-trunk download it from snapshot and then compile it... make make install depmode -ae modprobe ath_pci

I've the same chipset and works very very well with this trunk... or try to install a svn version 2834...If you then go to Madwifi's site, [http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi) it shows instructions for downloading the trunk:```
svn checkout http://svn.madwifi.org/madwifi/trunk madwifi
```You will need to have a few pre-requisits:```
sudo apt-get install subversion build-essential linux-headers-generic
```Have we overwhelmed you? Post back and we'll help you.

---

