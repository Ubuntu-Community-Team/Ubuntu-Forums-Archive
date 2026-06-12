---
title: "Roaming Fixed IP?"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by hatkirby on 2008-01-22
How do you set a fixed IP address while still staying in roaming mode (for Wireless internet)? I have a few servers on my computer, and it's annoying to have to log into the router and change each NAPT entry individually whenever the internal IP changes. But if I leave Roaming mode, it doesn't connect! Please help!

---

### Post by Borbus on 2008-01-22
You could set up static DHCP on your router if it has that feature. Most good firmwares do (DD-WRT etc.).

---

### Post by hatkirby on 2008-01-22
I thought that there would be something like that, but I looked around in the router settings and the only DHCP related setting I could find was:

DHCP Server: Enable, Disable, DHCP Relay

Under that was just the "What's the lowest possible IP? What's the highest possible IP?" and some more stuff like that.

EDIT: Wait. Would disabling the DHCP server do it?

---

