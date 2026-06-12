---
title: "Monitor Mode Automatically Changes to Managed?"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by oohyeah on 2008-10-17
I'm running Ubuntu 8.04 on a Dell Inspiron 6000 with the ipw2200 wireless card.  The ipw2200 is on eth1.
```

h@GreyUB:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HasHome1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:E4:0B:EE   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-30 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:37  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```

So I put the card into monitor mode using:

```
sudo iwconfig eth1 mode monitor
```

And quickly check iwconfig after doing this:

```
h@GreyUB:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Monitor  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:37  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The card is in monitor mode now, right?  A subsequent check of iwconfig a few seconds later shows "Managed" instead.  Is there some setting that is making the mode default to Managed? :confused:

---

### Post by bionnaki on 2008-10-17
use airmon-ng instead.

---

### Post by oohyeah on 2008-10-17
Thanks for the suggestion.  

```
 h@GreyUB:~$ sudo airmon-ng start eth1


Interface	Chipset		Driver

eth1		Centrino b/g	ipw2200 (monitor mode enabled)

h@GreyUB:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"HasHome1"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:10:E4:0B:EE   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0
```

airmon-ng does the same thing, yes, with the same result.  Monitor mode is enabled for a fleeting moment before automatically defaulting back to managed.

---

### Post by lswb on 2008-10-17
Network Manager will try to regain control of the card. I often find it helps to unload Network Manager when doing much command line stuff with the network interfaces. To unload the commands are:

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
and replace "stop"with "start" to restart NM.

I have this script named netman in my /usr/local/sbin for convenience:

netman
```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@

```

Then I can just type "sudo netman stop" or "sudo netman start"

Also FYI, when the mode is changed, the ipw2200 driver may reset any other configured options (like essid or channel) to defaults. So make sure you change to the desired mode before setting any other options.

---

### Post by oohyeah on 2008-10-18
Thank you very much for clarifying this.  It appears that when the card is already connected to an AP, Network Manager will keep the mode to managed.  When I manually disconnect from the AP and set the mode, it stays to monitor mode.

=D>

---

### Post by bionnaki on 2008-10-18
sudo airmon-ng stop eth1
sudo ifconfig eth1 down
sudo airmon-ng start eth1

keep it simple.

---

