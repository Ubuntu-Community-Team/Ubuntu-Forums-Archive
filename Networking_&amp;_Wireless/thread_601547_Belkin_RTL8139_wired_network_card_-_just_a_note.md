---
title: "Belkin RTL8139 wired network card - just a note"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Aessa on 2007-11-03
Just another little hint for anyone going through this as well.

A lot of issues seem to be present with the RTL8139 LAN chip.
I just bought a Belkin LAN card (could not find any other one today) and pulled off the sticker to see it is also just an RTL8139 chip on a PCB.

After several hours of typing 'modprobe -r 8139cp' and 'modprobe 8139too' and trying to blacklist the first one etc, I tried this and actually looked at the output:
'lswh -C network'

Clear as day: Logical name was eth3 (there is only one network related device in this server, so I kept searching for eth0). I changed /etc/network/interfaces to use eth3 and it all works perfectly so far. It still loads both 8139cp and 8139too modules.

I do not know how to force the use of the one or the other or how to 'rename' eth3 to eth0, but it works.

(Ubuntu server 7.10)

---

