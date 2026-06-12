---
title: "System Monitor showing Data sent with NO browser open"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by sattyfied on 2007-06-14
Just loaded Feisty Fawn and when I first login and open system monitor with no internet browser open  i show 1.4kbs data sent (upload) static. I shut of auto updates and still the same. Very new to Linux how can I see what is talking to network. Any commands  in Linux like the netstat or ipconfig? Any networking visual tips would be appreciated.

---

### Post by tact on 2007-06-14
Firstly - don't panic.  There will be certain small network traffic going on even when you are not surfing or downloading updates etc.  there are lots of administrative messages flying around networks (network overheads).

If you want a graphical view of connections made then maybe you can install firestarter (its just a graphical front end to the firewall (iptables) that is present in your current default fiesty install).

firestarter has a panel showing active connections and can even right click and resolve host machine names from ip addresses.  It also warns you if it thinks you are being hit by some machine or someone external.

firestarter is in the repositories so click on system>administration>synaptic to find and install it.

I am sure there are other tools that would monitor and report network activity but none I have played with.

---

### Post by sattyfied on 2007-06-16
Thanks I will try firstarter. Something funny though. I unplugged my Ethernet cable and still showed 1.4kbs upload. go figure it must be a bug?

---

### Post by YoG%*@ on 2007-06-16
> **sattyfied said:**
> Thanks I will try firstarter. Something funny though. I unplugged my Ethernet cable and still showed 1.4kbs upload. go figure it must be a bug?

i'm not sure, but sometimes polling for network status can cause "network traffic". i noticed the same when i used conky to display network stats etc... the network monitor would constantly show a few kb of up/down load even though there was none.

---

### Post by langi280179 on 2007-06-16
Wireshark can let you snif your traffic. I would use this as starting point.

---

