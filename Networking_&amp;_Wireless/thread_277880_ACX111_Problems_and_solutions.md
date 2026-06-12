---
title: "ACX111 Problems and solutions"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by rebird242 on 2006-10-15
Hi everyone. I just got Ubuntu and I have an ACX111 card. Anyway I was having a hell of a time getting it to run until now. Here is what I did. This is a quote from a previous posting. Below this is the modifications I did specifically to make mine work.

"Install acx drivers:

1:Link correct firmware to correct kernel version:

sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16

1.5:Or do this or both:

Append the line
options acx firmware_ver=1.2.1.34

to /etc/modprobe.d/options

so that the 1.2.1.34 firmware is used each time the acx module is loaded.

2:Load acx module:

sudo modprobe acx

3:Network settings: Either use network-manager or edit /etc/network/interfaces:

iface wlan0 inet dhcp
wireless_mode managed #working mode
wireless-essid B1KBCnet # essid (sid) of your network
wireless_nick RS101 #How you like to other se you
wireless_rate auto #Transfer rate auto, 1M...11M etc
wireless_txpower 10 #Txpower in dBm
"
------------------------------------------------------------------
It turns out both 1.2.1.34 and 1.2.0.30 will work. Im not sure if that was the fix. The second and maybe key item is I ran 
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
for all the files within the directory not just C16.
------------------------------------------------------------------
I hope this helps someone having trouble!
:mrgreen:

---

### Post by rebird242 on 2007-01-28
bump

---

