---
title: "[SOLVED] Firestarter has been uninstalled but it still seems to be 'firewalling'!"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by ken300 on 2008-01-21
Hi,

I've been using Ubuntu for a couple of months. When I first installed it I had an ADSL  modem with no hardware firewall built in so used Firestarter to put iptables into 100% stealth mode & got a 'passed' on the 'Shields UP!' firewall test site (at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)). 

I have since bought a new ethernet  ADSL  modem (a Thomson Speedtouch 510v6) that's got a hardware firewall built in, so I disabled Firestarter to remove the rules it had added to iptables and then uninstalled it via Synaptic (by marking it for complete removal).

I re-ran the 'Shields UP!' test & got 100% stealth and a pass as before. I decided to check it was the firewall in the new modem that was protecting me so I disabled the hardware firewall (in the modem) but still got 100% stealth and a pass at 'Shields UP!.

I've opened a terminal & entered 'sudo iptables -L' to list the rules that are being applied & get:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

I can't understand why my firewall still seems to work even though both the modems hardware firewall & iptables 'firewall' seem to be deactivated!

Any help to get to the bottom of what's going on would be much appreciated,

Thanks,

---

### Post by stunner on 2008-01-21
I'm no iptables guru, but those look like empty tables.  I'm using firestarter and the same command gave me significantly more output.

---

### Post by ken300 on 2008-01-21
Yeh,

I just had an idea & dug out my old modem, reconnected it, re-did the 'Shields IP! test & it failed so it looks like even though the web interface of the speedtouch 510 says the firewall's disabled it isn't!

Thanks stunner, I should have tried this switching modem thing first, oops!

---

