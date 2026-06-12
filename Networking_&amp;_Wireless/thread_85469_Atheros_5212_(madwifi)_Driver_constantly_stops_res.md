---
title: "Atheros 5212 (madwifi): Driver constantly stops responding"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by miras on 2005-11-02
Hi All,

I have a weird problem with Atheros which is that the driver constantly goes to sleep and stops responding for an unspecified period. To solve the problem I have installed the newest drivers from this place:  [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas madwifi. That did not fix the problem. I can only think of two possible reasons the 2.6.10 and 2.6.12 kernel or the ACPI system. I did not see this problem on Hoary (kernel-2.6.8).

No information can be found in any log file.

Regards,
Michael.

---

### Post by finni on 2005-11-03
[QUOTE=miras]Hi All,

I have a weird problem with Atheros which is that the driver constantly goes to sleep and stops responding for an unspecified period. To solve the problem I have installed the newest drivers from this place:  [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas madwifi. That did not fix the problem. I can only think of two possible reasons the 2.6.10 and 2.6.12 kernel or the ACPI system. I did not see this problem on Hoary (kernel-2.6.8).

No information can be found in any log file.

Regards,
Michael.[/QUOTE]

Same chipset here and worked also flawlessly on hoary. :confused:

---

### Post by cylon359 on 2005-11-07
[QUOTE=miras]Hi All,

I have a weird problem with Atheros which is that the driver constantly goes to sleep and stops responding for an unspecified period. To solve the problem I have installed the newest drivers from this place:  [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas madwifi. That did not fix the problem. I can only think of two possible reasons the 2.6.10 and 2.6.12 kernel or the ACPI system. I did not see this problem on Hoary (kernel-2.6.8).

No information can be found in any log file.

Regards,
Michael.[/QUOTE]

Do you have NetworkManager installed?  I was playing around with it, but it caused this exact problem (I think it was channel scanning or something).  After removing it, everything worked fine.

---

### Post by miras on 2005-11-07
[QUOTE=cylon359]Do you have NetworkManager installed?  I was playing around with it, but it caused this exact problem (I think it was channel scanning or something).  After removing it, everything worked fine.[/QUOTE]
Well, I did help some. Now the network connection comes up again after it was dropped. It does however still drops frequently. I have tried with a Debian 2.6.14 kernel and lasted madwifi build for Debian. On Debian it works like a charm but on Ubuntu it drops the connection now and then. Apparently it must be something in Ubuntu's implementation of either ACPI or laptop-mode. The result for my part is that I cannot use Ubuntu for any serious work in which case I will jump back to Debian :-\

---

### Post by miras on 2005-11-07
[QUOTE=miras]Well, I did help some. Now the network connection comes up again after it was dropped. It does however still drops frequently.[/QUOTE]

And then when you least expect it the answer shows up. The problem: On Debian and Ubuntu I use wifi-radar to connect to AP's. On Debian there is no problem in having it open after it have got a connection but apparently Ubuntu does not like this. Closing it down after you have received your connection solves the problem with frequently dropping the connection.

Was does this mean? You could see the same problem when network-manager was installed because it sometime scans the interface. This is also the case with wifi-radar so it seems that Ubuntu does not like applications scanning an interface which already have a connection. Apparently this is no problem in Debian so I wounder what is different in Ubuntu compared to Debian.

Lesson learned: Do not use any application which frequently scans the wifi interface as this seems to make Ubuntu drop the interface connection!

---

### Post by finni on 2005-11-17
[QUOTE=miras]And then when you least expect it the answer shows up. The problem: On Debian and Ubuntu I use wifi-radar to connect to AP's. On Debian there is no problem in having it open after it have got a connection but apparently Ubuntu does not like this. Closing it down after you have received your connection solves the problem with frequently dropping the connection.

Was does this mean? You could see the same problem when network-manager was installed because it sometime scans the interface. This is also the case with wifi-radar so it seems that Ubuntu does not like applications scanning an interface which already have a connection. Apparently this is no problem in Debian so I wounder what is different in Ubuntu compared to Debian.

Lesson learned: Do not use any application which frequently scans the wifi interface as this seems to make Ubuntu drop the interface connection![/QUOTE]

Removing wpasupplicant entries in /etc/rc.* might also help with this frequent disconnecting problem.

---

