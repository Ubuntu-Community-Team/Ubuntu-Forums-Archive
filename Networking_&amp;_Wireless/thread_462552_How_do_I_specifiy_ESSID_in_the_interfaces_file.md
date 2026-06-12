---
title: "How do I specifiy ESSID in the interfaces file"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-06-02
I am VERY disappointed in how many bugs there are in Feisty as far are wireless networking is concerned. 

Anyway... how do I specify the ESSID in the /etc/network/interfaces file ?  knetworkmanager doesn't work and wireless assistant is buggy.  I want to manually set the ESSID for the network I want to connect to.   How do I do that ?

Thanks

---

### Post by kevdog on 2007-06-02
Given the you didnt specify any more details on your post,  Id check out the following post:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I tells you how to add the SSID, among other things!

---

### Post by elmerfud on 2007-06-02
I don't want to use wpa-supplicant.

---

### Post by kevdog on 2007-06-02
I would just skip the parts about the WPA stuff and just use the lines that are appropriate for you.  I think it should work.  Again you are giving no details if you are using a wireless or wired connection so its hard for me to guess what you want.

---

### Post by dustigroove on 2007-06-02
[FONT=Arial][SIZE=2][COLOR=Black]Example:

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
iface ath0 inet dhcp
  wireless-essid putyourshere
```[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]**EDIT**: I am incorrect - please see tturrisi's post below.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by elmerfud on 2007-06-02
> iface ath0 inet dhcp
  wireless-essid putyourshere

That does NOT work with a wlan0 device.

---

### Post by dustigroove on 2007-06-03
[SIZE=2][FONT=Arial]As stated, it was an example. You will need to substitute the "ath0" in my example (which is the correct device name in my instance) with "wlan0" which is the correct one in yours.

**EDIT**: I am incorrect - please see tturrisi's post below.

Cheers,

[/FONT][/SIZE]

---

### Post by tturrisi on 2007-06-03
> That does NOT work with a wlan0 device.
If your wlan0 device is using the linux-wlan-ng drivers then of course ot won't work, because wlan-ng devices do not work with wireless-tools (iwconfig, iwlist, etc).  To use a wlan-ng device see the /etc/wlan dir and also see  [http://packages.ubuntu.com/feisty/admin/linux-wlan-ng-doc](http://packages.ubuntu.com/feisty/admin/linux-wlan-ng-doc)

---

### Post by dustigroove on 2007-06-03
[FONT=Arial][SIZE=2][COLOR=Black]Thanks for correcting my incorrect advice and bringing that to light, never had to use the wlan-ng drivers myself so was unaware of that fact.

Apologies for steering the poster incorrectly.

Cheers
[/COLOR][/SIZE][/FONT]

---

