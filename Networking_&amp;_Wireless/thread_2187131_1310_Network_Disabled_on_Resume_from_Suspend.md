---
title: "13:10 Network Disabled on Resume from Suspend"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by 7-webmaster on 2013-11-10
Since migrating to 13:10 I am encountering what seems to be identical to a problem previously reported on 10.04, and supposedly resolved long ago.  Sometimes when resuming from suspend networking is disabled.  Right clicking on the Network Manager icon shows greyed out "Network Disabled".  Selecting the Enable Networking has no effect except to display the check mark.  "Edit Connections" is also greyed out.  I have to use the old kluge:

[INDENT]service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start


[/INDENT]

---

### Post by varunendra on 2013-11-11
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

