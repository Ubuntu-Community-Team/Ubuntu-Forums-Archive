---
title: "How come WPA does not even come up as an option under encryption?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by rudeboyskunk on 2007-09-24
Ok, asking for help has become my last resort.  I have read every posting about this topic on the ubuntu forums and on just about any other forum online that I can find.

I am trying to connect my fiancee's computer to her apartment wireless network.  Her roommates have it set up as WPA Personal.

I have installed wpa_supplicant and wpagui.  Network Manager is of course installed (network-manager and network-manager-gnome).

Now hear this:  NETWORK MANAGER DOES NOT LIST WPA AS AN OPTION.  Even with wpa_supplicant installed.  When I do "sudo wpa_gui" the gui just says that it cannot connect to wpa_supplicant (with or without sudo).

I edited my /etc/network/interfaces all the ways I was told to.

I edited my /etc/wpa_supplicant.conf all the ways I was told to.

Ok, there are two wireless cards in this computer.  One is internal, but its chipset is Broadcom and is not supported in Linux (I will only try ndiswrapper on this as a last last last resort).  The other is external, Cisco Aironet 350 Series Wireless Lan Adapter.  The one being used is, obviously, the Cisco one.

The only thing I can think of is that for some reason the Cisco card cannot support WPA...???  Like I said before, Network Manager does not give me the option to do WPA, only WEP.

Has anybody solved this problem?

---

### Post by kevdog on 2007-09-25
Maybe the Cisco card doesnt support WPA??  Try ndiswrapper with the broadcom card -- Im fairly certain this will support wpa

---

