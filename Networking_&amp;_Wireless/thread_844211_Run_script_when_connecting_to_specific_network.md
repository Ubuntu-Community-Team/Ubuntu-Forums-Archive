---
title: "Run script when connecting to specific network"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by XezzeX on 2008-06-29
I'm using Ubuntu Hardy Heron on my laptop and autoconnect to a WPA2 wireless network when at home using the NetworkManager from Gnome.
Furthermore I have a server running NFS on my homenetwork, and I would like a NFS share from the server to be automounted on my laptop when I connect to my own network.
Is that possible?

---

### Post by kevdog on 2008-06-29
I dont think its possible using NetworkManager -- they haven't integrated this feature.  I believe WICD has this feature, or you are going to have to make a script and then connect manually.

---

### Post by HalPomeranz on 2008-06-29
The easiest thing would be to just add some code to /etc/rc.local that detects what network you're on and runs the appropriate commands if you're on your home network.  Detecting what network you're on could be done by parsing the output of "netstat -in", "netstat -rn", and/or "ifconfig".

Here's some sample code to get you started:

```

HOMEROUTER=192.168.1.1
DEFROUTE=`netstat -rn | awk '/^0.0.0.0/ { print $2 }'`

if [ "$DEFROUTE" = "$HOMEROUTER" ]; then
    # if you get here then you're on your home network
    # put the commands you want to run here
fi

```

You would need to replace 192.168.1.1 with the IP address of your default gateway on your home network.

---

