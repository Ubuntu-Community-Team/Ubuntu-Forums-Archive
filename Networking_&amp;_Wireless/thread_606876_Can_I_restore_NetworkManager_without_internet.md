---
title: "Can I restore NetworkManager without internet?"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by bliffle on 2007-11-08
How can I restore my network-manager? I was trying to install another type of net manager (wicd) which failed and left me with no internet access. I just want to go back to where i was yesterday.

I have an alternateCD, which I tried to use as a substitute for the internet repositories, but it only went partway and then demanded the internet.

---

### Post by ukripper on 2007-11-08
Are you using Wired connection or wireless?

---

### Post by Ehtetur on 2007-11-08
> **bliffle said:**
> How can I restore my network-manager? I was trying to install another type of net manager (wicd) which failed and left me with no internet access. I just want to go back to where i was yesterday.

Startup synaptic and install these packages:
network-management network-management-gnome
While in syanpatic, you may want to whack wicd... unless you compiled it from source.

After you reboot, the network manager applet should be running in your task bar. You can click on it and configure your network connections.
If the applet doesn't show, you can press Alt-F2 and enter nm-applet

---

### Post by rykel on 2008-07-21
Hi,

I completely removed Network Manager and reinstalled it. The applet works, but Roaming Mode seems to have disappeared... do you know how I can restore the mode?

---

### Post by ukripper on 2008-07-22
> **rykel said:**
> Hi,

I completely removed Network Manager and reinstalled it. The applet works, but Roaming Mode seems to have disappeared... do you know how I can restore the mode?

Are you using nm-applet?

---

### Post by rykel on 2008-07-23
Yes, I was.

Anyway, I solved the problem by purging network manager and reinstalling it.   :P

The problem happened because I had "disabled" online/offline mode notification earlier by editing some network-manager config file, and a clean reinstall replaced the file, hence Roaming Mode works now.

Thanks!!

---

