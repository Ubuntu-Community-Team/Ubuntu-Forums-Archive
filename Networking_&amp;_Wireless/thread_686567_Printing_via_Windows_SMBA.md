---
title: "Printing via Windows SMBA"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by gleiter on 2008-02-03
I am trying to use a HP 722C that is attached to my windows machine.  This printer worked during a live install, but not after the actual installation. 

 I am using Windows printer via SAMBA, and download available updates.  It did not work before or after the updates were installed.  I am using the recommended driver thru ubuntu, Footmatic/pnm2ppa.  Under Verified in the setup  I get "This print share is accessible".  A test page will not print.  I tried printing thru Open Office as well, did not print. 

I do have axcess to the network and internet.

I have spent the time to research here on FAQ, and this forum, but nothing seems to work.

---

### Post by linuxwizard on 2008-02-03
Look through this > [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530) > The HP DeskJet 710C/712C/720C/722C/820C/1000C (driver "pnm2ppa") do not work in Gusty. This maybe your problem. You didn't post which version of Ubuntu you are using.

---

