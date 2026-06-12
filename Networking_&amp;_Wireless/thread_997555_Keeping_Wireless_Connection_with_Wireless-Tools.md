---
title: "Keeping Wireless Connection with Wireless-Tools"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by jetdog440 on 2008-11-29
Hello,

Recently I was looking through some old threads to find a way to keep a wireless network \\:D/conected\\:D/ with JUST my /etc/networking/interfaces file, which, by the looks of it, should be more than enough to keep a wireless connection alive.

For most practical purposes, I'd suggest using the NetworkManager applet.  For the rest of this document, I'll be showing you a non-gui-dependant means of preserving a single connection, from just the command line, without networkmanager!  

:idea:Also of note, This script isn't geared towards a workstation, as it's meant more so for a light-end non-gui server with only a command line, such as a debootstrapped ubuntu installation, or a network file server (though, if you're knowledgeable of cron, you can configure it to check your connection every minute or so).

Here's a great little file to add to crontab to maintain your wireless.  You can place it anywhere safe (I stuck mine in /root/ , but there's probably plenty of other places to put it).

:arrow:Replace "wlan0" with your interface name:

```

#!/bin/sh
#NOTE: This script is only tested for FULL DOMAIN addresses i.e. www.google.ca, due to the way the ping
#command likes to say WAY more about addresses that it can successfully resolve. (Eeeewww :P)
#
HOST=www.google.ca
IFACE=wlan0
ping -c 1 -W 10 "$HOST" -I "$IFACE" -q
if [ $? -ne 0 ]
then
	#restart the adapter - the linux way
	ifdown "$IFACE"
	ifup "$IFACE"
fi


```

As root,

```
chmod +x the_above_file.sh
```

Then add this to /etc/crontab:
```
*/10 *    * * *  root    /full/path/to/script/test_wir.sh
```

And that's it! :KS:lolflag::KS

PS.  For doing this with multiple wireless adapters, you can also replace the entry "IFACE=wlan0" with "IFACE=$1", to allow the interface name to be passed as a command-line parameter, from crontab:

```
*/10 *    * * *  root    /full/path/to/script/test_wir.sh wlan0
```

You could then pass the interface name to the script as a command-line parameter!

---

