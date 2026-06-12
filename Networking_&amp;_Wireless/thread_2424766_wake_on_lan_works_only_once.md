---
title: "wake on lan works only once"
date: 2019-08-14
forum: Networking &amp; Wireless
---

### Post by replab_robin on 2019-08-14
Ubuntu 18.04.3 running on an i5 intel nuc.

I set up wake-on-lan using ethtool. I connect to the network from home using ssh to a gateway machine and then wake the NUC using a python script.

This works correctly just once. If I shut down the machine using eg

echo "systemctl poweroff" | sudo at now + 1 min

then the machine powers off and I can no-longer wake it. 

I have setup a wol.service using

/etc/systemd/system/wol.service

$ cat wol.service
[Unit]
Description=Configure Wake-up on LAN

[Service]
Type=oneshot
ExecStart=/sbin/ethtool -s eno1 wol g

[Install]
WantedBy=basic.target

and this is linked in ./basic.target.wants/wol.service

I'm not a great expert at systemd, but I assume basic.target does get executed when I wake the machine.

How can I make ssh shutdowns wakeable?

---

