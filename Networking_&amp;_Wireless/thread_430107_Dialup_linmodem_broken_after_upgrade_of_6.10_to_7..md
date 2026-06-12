---
title: "Dialup linmodem broken after upgrade of 6.10 to 7.04"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by boon on 2007-05-01
With temporary access to broadband, i was able to successfully upgrade to feisty 7.04.

Everything seems fine except that dialup internet access (usually my only access)  is broken. It gives me a 'carrier not found' 'connect script failed' message. 

7.04 has a new feature 'Restricted Drivers Manager' which shows i have a driver for a lucent/agere internal modem but it makes no difference whether i enable or disable this.

The linmodem survived the previous upgrade from 6.06 to 6.10, why does it have to break now?

Any solutions?

---

### Post by boon on 2007-05-05
ok i was able to solve my own problem by using the linmodems.org site & mailing list. 

I was supplied with a new slmodemd and after installing it things seem to run fine.

What a great resource those guys at linmodems.org are.

It might seem a bit complicated but I would recommend people with linmodem problems read the site carefully, use the scanModem utility, subscribe to the list and follow directions. 

Works for me, twice now!

---

