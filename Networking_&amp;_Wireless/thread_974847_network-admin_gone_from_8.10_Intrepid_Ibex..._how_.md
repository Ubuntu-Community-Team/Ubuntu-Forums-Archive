---
title: "network-admin gone from 8.10 Intrepid Ibex... how do I connect to wpa router?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2008-11-07
So I did a fresh install (not an upgrade) of 8.10 Intrepid Ibex.  I need to connect to my WPA wireless router.  I've installed the driver through ndisgtk, and it seems to work fine.  However, network-admin was not installed in 8.10!  That's what I had been using on 8.04.1, and it had worked fine.  So I installed it from Synaptic--but when I ran it, I discovered that the configuration window is missing the WPA option.  It only has WEP available.  So, I uninstalled network-admin to get my system back to the way it was.

Next I tried nm-applet (which I have never used before).  But that just gave me weird error messages in terminal whenever I tried to run it, so I deleted that, too.

I need to connect to a WPA wireless router.  Any suggestions would be much appreciated.

Thanks in advance!

---

### Post by brs19301 on 2008-12-20
Just installed 8.10 and can't find "network-admin" to set up wlan0.  iwconfig shows my my device properly.  I tried the following command to try to get it going by hand but am not sure about the WEP code I used "enc" is that right?

sudo iwconfig wlan0 essid "HOMENET" channel 11 mode Managed enc xxxxxxxxxxxxxxxxxxxxxxxxxx commit

Does this look right?  What else can I do?

---

### Post by Mark_Malewski on 2008-12-26
I did a fresh install of Ubuntu 8.10 and there doesn't seem to be any network-admin.  Any ideas on how to get network-admin back into Ubuntu 8.10, and to get it working?

Where did it go, and why isn't network-admin in Ubuntu 8.10?  How do you configure the network adapters with a GUI in Ubuntu 8.10 without network-admin working?

Does anyone have any idea what is going on with the network-admin missing in Ubuntu 8.10?  How do I install it, and/or get it working?

---

### Post by voxel on 2009-01-17
I was just having the same problem myself.
If you install the package gnome-network-admin, that should be it.

---

### Post by appoi on 2009-10-06
u can try this sudo apt-get install gnome-network-admin in your root terminal....

it's working on my notebook after upgrade 8.04 to 8.10...

---

### Post by Bucky Ball on 2009-10-06
Just one genuine question: If 8.04 was working, why did you decide you needed 8.10? Was there a particular package or setup you were keen on using??

---

