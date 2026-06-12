---
title: "How to permanently disable network adapter?"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by snakyjake on 2015-05-20
Using the command line, how can I permanently disable network adapters?

I can disable the network adapters via GUI (see screenshot).
How can I do the same via command line (CLI)?  
Is there a file I can edit?

[ATTACH=CONFIG]262096[/ATTACH]

Thanks in advance,
Jake

---

### Post by SeijiSensei on 2015-05-20
sudo ifconfig eth0 down

will disable the primary Ethernet interface.  Apply the same logic to any other interfaces you wish to disable.

If you want to permanently disable it so it doesn't come up at the next reboot, you'll have to "blacklist" the network driver in /etc/modprobe.d/.  It's probably easier to add the ifconfig command (without the "sudo") to /etc/rc.local, the last script that runs when the machine boots.

---

### Post by snakyjake on 2015-05-20
I think I'm running into a problem adding to the rc.local.  I'm guessing I have services running and using the network adapter, and then the rc.local shuts the adapter down.  If this is true, I need the solution the disable the adapter before rc.local, init.d, etc.  

I need something that will disable the adapter at the beginning.

I have two network adapters (eth0 and wlan0).  I don't want to use wlan0 for anything.

---

### Post by Vladlenin5000 on 2015-05-20
> **snakyjake said:**
> I need something that will disable the adapter at the beginning.

Answer in post #2 (blacklist driver).

> I have two network adapters (eth0 and wlan0).  I don't want to use wlan0 for anything.
Wouldn't NOT connecting to any WiFi network and/or use an hardware switch (if available) or simply removing the card/USB you "don't want to use for anything" be a way simpler and effective solution?

---

### Post by snakyjake on 2015-05-20
Where's the setting to disable "Automatically connect to this netowork when it is available"?

I need this setting, and the adapter, disabled at boot before some services start.  I don't want the services (apps) mapping my router to the wlan0 IP address.

[ATTACH=CONFIG]262101[/ATTACH]

---

### Post by snakyjake on 2015-05-20
> **SeijiSensei said:**
> "blacklist" the network driver in /etc/modprobe.d

I'm not able to see modprobe.d

---

### Post by Vladlenin5000 on 2015-05-20
> **snakyjake said:**
> I don't want the services (apps) mapping my router to the wlan0 IP address.

If you never connect to a WiFi network, nothing will be mapped; likewise if there's no adaptor at all (removed).
I'm still confused: Why are you complicating things so much?

---

### Post by Vladlenin5000 on 2015-05-20
> **snakyjake said:**
> I'm not able to see modprobe.d

Everybody has /etc/modprobe.d so i also don't understand why you don't "see" it.

---

