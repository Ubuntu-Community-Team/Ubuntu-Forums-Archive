---
title: "howto: auto connect to wifi point on start-up (script)"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Jacks0n on 2007-03-09
Lately I've been moving around quite a bit between places, and I've been changing wifi points quite regularly. I figured why not make a bash script that chooses an open wifi-point at startup, and connects to it. If someone's done this before here I apologize..

So if anyone wants it, just type the following into terminal...

```

gksudo gedit /etc/init.d/wifiscan.sh

```

copy the following into the text editor and save it

```

#!/bin/bash

# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
dev=$(cat /tmp/dev_pure)

# Get a list of open wifi points, and choose one
iwlist $dev scan > /tmp/scan_output 2>/dev/null
scanone=$(egrep 'ESSID|Encryption' /tmp/scan_output)
essidone=${scanone%%"Encryption key:off"*}
essidquot=${essidone##*'ESSID:"'}
essid=${essidquot%'"'*}

# Connect
if [[ ! -z $essid && ! -z $dev ]]; then
	iwconfig $dev essid $essid
fi

```



```

update-rc.d wifiscan.sh defaults
sudo chmod +x /etc/init.d/wifiscan.sh

```

And that's it! I haven't tested it too much, but so far it's worked every time for me.

---

### Post by renzokuken on 2007-03-09
i've been looking for something exactly like this to stop my laptop from automatically connecting to my neighbours (unprotected) wireless on boot and not to my passworded wifi network.

i'll have a go tonight and see how it goes.

does the script require any customisation, like do i have to replace any of the "essid" parts with my essid?

and what about keyrings?

---

### Post by Jacks0n on 2007-03-09
ah, the script I wrote finds open wifi points, and connects to it. If you want to connect to your one (closed), change it to...

#!/bin/bash

# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
dev=$(cat /tmp/dev_pure)
iwconfig $dev essid "YOUR_ESSID" key 0123-4567-89


Change the "YOUR_ESSID" and 0123-4567-89 accordingly for your network

---

