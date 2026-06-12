---
title: "howto get the list of all avilable wireless networks?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by adhg on 2008-05-05
Hi all,

When I click the "Manual network configuration" icon (next to the clock) I expect to see the list of all networks (including mine that works fine) but for some reason I don't and the only option available is: Manual configuration.

When I click it - I get the Network settings but the 'location' is empty 

thanks for any pointers

---

### Post by amohanty on 2008-05-06
If you do manual network configuration, nm-applet or network applet expects you to provide all the information via the System->Administration->Networks GUI or via the /etc/network/interfaces file (the gui simply adds to this file).

Only in roaming mode can you see the drop down list of available wireless networks.

You could alsy try the following (I am not sure if it works in Manual Config mode):

sudo iwlist sc

HTH
AM

---

### Post by kevdog on 2008-05-06
at command line:

iwlist scan

---

### Post by hyper_ch on 2008-05-06
or kismet also scans for wifi

---

