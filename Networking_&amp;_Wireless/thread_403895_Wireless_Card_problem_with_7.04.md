---
title: "Wireless Card problem with 7.04"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by keithk50 on 2007-04-07
My Netgear WG511T card has worked perfectly since dapper installation (no setup was necessary just WEP entry).   Out of interest I have tried the 7.04 live cd on my laptop and got the following message box saying:

Restricted Driver.    " In order for this computer to function properly Ubuntu may be using driver software that cannot be supported.   Because the software is proprietary it cannot easily be changed tto fix any future problems.    Driver:   Atheros (HAL)      enabled      in use"

After entering my WEP code in the network section it attempted connection however failed to connect.   Although I am in no rush to install 7.04 I do intend to do a fresh install in the future.
Being fairly new to Ubuntu I just wondered if there is something I have missed regarding restricted drivers in future Ubuntu releases?

---

### Post by spd106 on 2007-04-09
The new restricted drivers application is designed to educate the user about the use of proprietary code in Ubuntu. Previously these drivers have been hidden from the user and allowed devices to "just work". With the expected introduction of proprietary graphics drivers in upcoming releases, it was decided that the situation should be more transparent. This also aids those who do not want any non-free code in their OS at all.


Your card should work as it has done previously, so I am surprised that you have had any trouble. It's probably related to Network Manager as that's been the biggest change. Have you tried setting a static configuration?

---

### Post by keithk50 on 2007-04-09
Thanks for the information, and I can now understand the logic behind it.   I was also surprised when I could not connect as Networking found my SSID first time (including others in my neighbourhood) and I even tried it with security disabled on my Netgear Router.   The status lights on the network PCI card showed connection for brief period then failed to connect again.   I shall try your suggestion with static IP configuration and post back results.   Other than that I was very impressed with 7.04 and eagerly await installation when the time comes.   Thanks again.

---

