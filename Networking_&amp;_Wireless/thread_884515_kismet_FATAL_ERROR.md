---
title: "kismet FATAL ERROR"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by thethirdhunter on 2008-08-09
Can someone help me? When ever I try to run kismet I get this message? thank you in advance for all your help. 

BTW: i intalled it with 'sudo apt-get install kismet' on HARDY HERON


Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.

:popcorn:

---

### Post by chili555 on 2008-08-09
You need to edit */etc/kismet/kismet.conf* to specify your capture source. You can learn more with:```
less /usr/share/doc/kismet/README.gz
```Especially read sections 9 and 12. Here, as an example, is a relevant section from my *kismet.conf:*```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw2915,eth1,ipwcosource
```Your *kismet.conf* must be set up to suit your wireless card.

---

