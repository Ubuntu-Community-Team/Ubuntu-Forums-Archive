---
title: "Trying to disconnect from the internet."
date: 2013-12-21
forum: Networking &amp; Wireless
---

### Post by cyclingchap on 2013-12-21
Hi.

Something funny going on with my system (Ubuntu 12.04 LTS). Usually people have problems connecting to a wireless netork and the internet, but I seem to be having the opposite problem; I can't disconnect!.

I wanted to voluntarily disconnect from my network and internet, to work off-line.

To to this I right-click on the wireless icon in the top bar and first disconnect from my WAN, and then 'disable networking'.

Whe I do this the wirless icon apears 'unfilled' (indicating no connection) and the 'disable networking' in the menu changes to 'enable networking'.

That all seems correct..

but the only problem is I am still connected to the internet, i.e. my browser still brings up pages! Running netstat shows that I still have established connections.

Is this some kind of known bug? Surely doing what I did above is supposed to completely disconnect you from your WAN/internet? 

Any help appreciated....

Paul

---

### Post by TheFu on 2013-12-21
Disable the wifi chip using the BIOS. I assume you are on a laptop.  Mine has a Fn-{key} that toggles the wifi off and on.

---

### Post by steeldriver on 2013-12-21
what does ifconfig say? do you perhaps have another interface defined outside of NetworkManager (e.g. via /etc/network/interfaces)

---

