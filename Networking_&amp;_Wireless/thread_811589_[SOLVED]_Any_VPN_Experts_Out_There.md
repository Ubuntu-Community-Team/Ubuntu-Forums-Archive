---
title: "[SOLVED] Any VPN Experts Out There?"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by nlavon on 2008-05-29
I want to connect to my office VPN through Ubuntu. We use the client only on Windows to log in.

After much clawing around (and installing some VPN clients I did not need) I found the VPN connection menu from the Network Manager (had to double click, not left mouse click). 

At any rate, any light shed here would be great as I would love to get it up and running on Linux since I have the account authorized anyway.

Thanks!

Neal Lavon
Takoma Park, MD
USA

---

### Post by terazen on 2008-05-29
I'm using the Cisco VPNClient for linux downloaded from Cisco's website and it works fine.  One of the IT guys there would have to download it for you if you don't have a valid login on the cisco website.

[http://www.michelem.org/2008/03/12/patch-cisco-vpn-client-and-linux-kernel-2624/](http://www.michelem.org/2008/03/12/patch-cisco-vpn-client-and-linux-kernel-2624/)

If you can get the vpnclient installed you can try to copy your windows pcf file from c:\program files\cisco systems\vpn client\profiles directory to your ubuntu machine, /etc/opt/cisco-vpnclient/Profiles/.  I haven't tried it myself but the files look the same.

---

### Post by brommage on 2008-05-29
[http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Copy the encrypted code into this webform, and it gives it to you in cleartext.

---

### Post by nlavon on 2008-05-29
Thanks for the suggestions and sites.

Before trying the Cisco VPN client, I may try the Cisco VPN plugin through the Network Manager (which calls for these settings)check Firestarter and see if it goes.

Thanks all!

Neal Lavon
Takoma Park, MD
USA

---

