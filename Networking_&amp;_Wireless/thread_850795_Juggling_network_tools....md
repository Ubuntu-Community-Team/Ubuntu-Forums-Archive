---
title: "Juggling network tools..."
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by arnicainthemembrane on 2008-07-06
My issue is, I use wicd to find and connect to wireless networks. The problem is, every time I try to connect, Network Manager connects too, and I can't get my PCI wireless adaptor to "turn on" unless I connect to the network with Network Manager AND wicd. 

So my question is, how can I get wicd to be the only program which detects and connects to networks, and how can I tell (via command line) WHICH network is being detected, and WHICH program is connecting it?

thanks.

---

### Post by kevdog on 2008-07-06
Just a suggestion as per the wicd page -- if you install wicd you are supposed to completely uninstall network manager.  The two should not be run together -- sounds like that is what is happening.

---

### Post by imdano on 2008-07-06
How did you install wicd?  Unless you built from source it should have uninstalled NM as part of the wicd install process.

---

### Post by sputnikkk on 2008-07-22
The install routine for wicd gave a message box that indicated it wanted me to approve removing NetworkMisManager ... I said yes.

Sadly NetworkManager GUI is still there.

I thought I also read that Wicd is on top of NM?  Cant seem to find that now ...

How can I get rid of the NetworkManager software?

---

