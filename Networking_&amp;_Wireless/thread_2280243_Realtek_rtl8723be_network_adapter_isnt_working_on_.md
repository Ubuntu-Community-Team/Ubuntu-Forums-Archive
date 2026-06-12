---
title: "Realtek rtl8723be network adapter isnt working on my HP 13 Laptop"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by anthony64 on 2015-05-29
Whenever I reboot the computer I'll have wireless for maybe twenty minutes.  After that I lose connection and although I can see the networks I can never connect to mine.  It just keeps cycling through.  To further complicate the matter, this laptop doesn't have an ethernet port so I have no alternative methods of connecting to the internet.  I tried looking for drivers but I don't really know whats going on with those because I've only installed Broadcom drivers before.

There was another post on here that had a solution but I dont think it worked.

---

### Post by jeremy31 on 2015-05-29
I would check wifi router encryption settings, have it set for WPA2-AES or WPA2 only, you do not want TKIP enabled

Then I would try ```
[COLOR=#000000][FONT=Ubuntu Mono]echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot[/FONT][/COLOR]

---

### Post by anthony64 on 2015-05-29
Thanks.  Checked my router and its set to WPA2-AES then I changed that and the output 

```
options rtl8723be fwlps=N ips=N
```

---

### Post by jeremy31 on 2015-05-29
Is it fixed?

---

