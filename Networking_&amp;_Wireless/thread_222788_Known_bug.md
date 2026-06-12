---
title: "Known bug?"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by otherd on 2006-07-25
On the Atheros (cisco) card I'm using, every time I restart the computer the domain name on the ath0 interface (settings, general tab) keeps disappearing. I set it for my domain name and click ok, then the network starts working. Until I do, I have no wireless access. Soon as I reboot, it's gone again and no wireless.

---

### Post by evongugg on 2006-09-09
What worked for me.

Ubuntu was trying to find my second ethernet connection and couldn't find it because I was not using it. It would default in Networking to this unused connection. And the domain name kept disappearing.
When I disabled the second ethernet connection in the Bios (the one I am not using), the domain name started sticking all the time and I do not have to reenter it each time I reboot. Do several reboots.
Now after reboots, Ubuntu realizes which connection is primary. You can go back in the Bios and reenable the second ethernet connection. Then you configure it in Networking and every time you reboot your primary ethernet connection will be used and the domain name will always stick. The second connection will also be available, if you desire.
Thanks

---

