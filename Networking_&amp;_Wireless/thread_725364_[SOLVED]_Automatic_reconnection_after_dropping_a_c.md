---
title: "[SOLVED] Automatic reconnection after dropping a connection due to poor signal streng"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by vatzec on 2008-03-15
I'd like to make my computer reconnect after it drops the connectivity due to loss of the signal (or actually anything else). I'm administrating it via SSH and right now anything I can do is going to the server room (the basement :P) and rebooting it. The wi-fi device is a USB Planet thingy, Ubuntu detects it as eth1. I've tried making a bash script which cron would run every 5 mins but that doesn't work for some reason (the script's probably the reason, because sudo /etc/init.d/networking restart && sudo /etc/init.d/wifiautoreconnect didn't do the thing).

This is my /etc/network/interfaces (if it helps in any way):
```
auto eth1
iface eth1 inet dhcp
wireless-essid <network's essid>
```

And here's my reconnect script:
```
#!/bin/bash
if ! ping -c 3 192.168.1.1 # this is the router's IP
then
  /etc/init.d/networking restart
fi
```

The crontab entry:
```
*/5 * * * * /etc/init.d/wifiautoreconnect
```

- EDIT -
Oh, and yes, I've used sudo crontab -e, so it's ran as root.

- YET ANOTHER EDIT -
Alright, I have solved it this time. The whole problem was that even though I have created the file with sudo nano I didn't set the exec permissions for the root user. Argh.

---

