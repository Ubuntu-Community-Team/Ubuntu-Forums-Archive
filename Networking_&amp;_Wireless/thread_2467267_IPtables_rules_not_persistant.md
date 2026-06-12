---
title: "IPtables rules not persistant"
date: 2021-09-21
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-09-21
I had a problem with one of my 18.04 computers (formerly 16.04) that has a bunch of site specific iptables.rules. The onboard NIC went out. I installed a new NIC and it started working immediately as expected, except of course the iptable.rules were not loaded. 
I edited the iptables.rules file with the new network interface name (eth1) and loaded the iptables rules with: 
```
iptables-restore < iptables.rules
```
That worked great I was back in business.
I rebooted the computer to see if the rules would be reloaded as they always had been before. It didn't work.
I tried:
```
# apt-get install iptables-persistent
```
Got that the version installed was already the latest.
I then tried to save the loaded rules;
```
# iptables-save > /etc/iptables/rules.v4
# ip6tables-save > /etc/iptables/rules.v6
```
That worked the files now contain the correct rules.
But it still not loading on reboot. 
ufw is inactive and As far as I know always has been.
It's been so long since I set this up (years) - either I've forgotten what I did or they've changed something.
Honest it worked yesterday before the NIC failed. :(

---

### Post by dogservant on 2021-09-21
What you've stated is what I do. I would double-check filename and permissions. No errors reported during restore?

---

### Post by rsteinmetz70112 on 2021-09-21
OK I found the answer. Apparently some time ago (years) I have edited /etc/network/interfaces to read the /etc/iptables.rules file and install the rules saved there. I edited that file /etc/network/interfaces file again to update the name of the interface and all is good now. 
Another thing to add to my ever growing list of things to clean up.

I'll mark this solved now.

---

