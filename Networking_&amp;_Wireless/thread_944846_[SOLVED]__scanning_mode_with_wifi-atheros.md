---
title: "[SOLVED] ? scanning mode with wifi-atheros"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by gary22 on 2008-10-11
For a new user I find my way around Ubuntu pretty well. There is a couple of  problems that I have not been able to solve. I am trying to get Wireshark up an running by using the command gksudo. It scans only my own network. I think I am running mad-wifi with a atheros driver but I have not figured out how to verify it yet. I think I have to configure something to the scan mode but the school  of hard Knox  has not shared it with me yet.

Thanks for any  help someone mite be
Gary22

---

### Post by jbrown96 on 2008-10-11
I think what you want is monitor mode. Try ```
iwconfig
``` to find your wireless device (ath0, wlan0, etc) Then try ```
sudo iwconfig DEVICE mode monitor
```

---

### Post by gary22 on 2008-10-12
I keep getting a message that says no such function when I try change the mode to monitor. I would like to check the version of Atheros Driver that I am using but I can't find a command for this. I am sure there is one.
Thanks
Gary22

---

