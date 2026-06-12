---
title: "ndiswrappre sudo make error - attempting wireless adaptor install"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by FromFPan2Fire on 2008-07-11
Hi all.

Problem getting wireless working on Ubuntu. 

Specifics:

Drake 6.06
Trying to make Ndiswrapper 1.53
Trying to use a USB Linksys WUSB54G Ver 4

Reason:  For no apparent reason, my internal laptop wireless adapter appears to have failed.  It now only shows “0” signal level.  I see no indication that the configuration has changed or is in any way wrong, so I'm assuming a hardware failure.  So, am trying to use a USB adapter.  (Inbuilt wireless is still looking all but normal; can activate/deactivate, “connect” etc... but there is just never any signal showing.)  I have confirmed that the router is broadcasting – other wireless device working on the network.

Okay – I've spent a lot of time on this, searching, and seen others working on the same issue, but haven't found my solution.  

I've reached the series of steps:

sudo make uninstall
sudo make
sudo make install

The “sudo make uninstall” step works fine.  The “sudo make” command gives me these errors:

(See screen shot I hope I'm attaching)


So,  I'm stuck here.  Any help would be appreciated.

---

