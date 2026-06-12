---
title: "wifi is asleep after 'suspend'"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by makem2 on 2016-09-14
I have just upgraded to 16.04 and the wife was working fine.

I wanted to test the power from usb when asleep which this machine can so 'suspended' it as 'sleep' was not available.

On resume I have lost wifi.

```

makem@ssdTOSH:~$ nmcli g
STATE   CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
asleep  none          enabled  enabled  enabled  enabled 
makem@ssdTOSH:~$

```

The wifi icon menu shows:

Networking disabled
Enable networking is checked

Please help me wake it up!

---

### Post by makem2 on 2016-09-14
Tried a number of restarts and various commands found via google to no avail. Treating xubuntu like winblows I re-suspended it, woke it up and found I could not turn if off! Every time I tried it just came back to the login without rebooting even.

I was forced to press the power off switch until it shut down

Upon restarting I find that networking is up and running again.

I will never suspend again!

Still need to find out how to enable power on usb which my machine can do though ;)

---

