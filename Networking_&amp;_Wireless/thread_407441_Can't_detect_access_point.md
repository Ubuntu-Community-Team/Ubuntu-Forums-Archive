---
title: "Can't detect access point"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by x.1.alvin on 2007-04-12
I have a Linksys notebook adapter WPC54G, properly detected by my Compaq 800 laptop (using Dapper). Using iwconfig, the only thing wrong is the access point is invalid, all the others are okay. Tried to set the ap (copying the ap in my other working laptop) using iwconfig, not working. iwlist scan doesnt work also. Any suggestions on how I can detect the ap? Thanks!

---

### Post by garrido on 2007-04-12
Can't you just set the ESSID?

```
sudo iwconfig ethx essid "your essid here"
```

When you say iwconfig and iwlist don't work, what do you mean?  What output do you get?

---

### Post by x.1.alvin on 2007-04-13
Thanks for your reply. I did set ESSID, and when i iwconfig, the ESSID is correctly written, but 'Access Point: Invalid'. Any ideas?

[HTML] IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]

Thanks again.

---

### Post by x.1.alvin on 2007-04-13
I think I know what's wrong, the access point cannot see my hardware. How do I log into the AP to see if my MAC address is there? How do I match the settings of the AP and my laptop?

Thanks for being patient with a newbie! :)

---

